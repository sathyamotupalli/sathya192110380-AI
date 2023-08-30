
% Facts representing parent-child relationships
parent(john, susan).
parent(susan, emily).
parent(susan, james).
parent(mary, john).
parent(james, anna).

% Rules for deducing grandparent relationship
grandparent(X, Z) :-
    parent(X, Y),
    parent(Y, Z).

% Backward chaining algorithm
backchain(Goal) :-
    Goal,
    writef('Goal "%w" is true.\n', [Goal]).
backchain(Goal) :-
    rule(Goal, Premises),
    writef('Goal "%w" can be inferred from:\n', [Goal]),
    write_premises(Premises),
    nl,
    deduce_premises(Premises).

% Example rule base
rule(grandparent(X, Z), [parent(X, Y), parent(Y, Z)]).

% Helper predicates
write_premises([]).
write_premises([Premise|Rest]) :-
    writef('  %w\n', [Premise]),
    write_premises(Rest).

deduce_premises([]).
deduce_premises([Premise|Rest]) :-
    backchain(Premise),
    deduce_premises(Rest).
