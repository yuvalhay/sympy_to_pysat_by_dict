This function converts any sympy statement to a CNF statement in pysat by using a dictionary as a key to the sympy symbols.
function explanation:
line 1-5: if the statement is coverable to CNF statement we proceed to line 5 
{ 
  e.g. statement = statement = (A & B | ~C)   >>   CNF_statement =(A | ~C) & (B | ~C)   >>   cnf_args = (A | ~C ,  B | ~C) 
  dict = { "A" : 1, "B" : 2, "C" : 3, "D" : 4, "E" : 5 }
}
line 7: decomposing the CNF statement (by the & link)
line 8: craeting the list of clauses that will go into the pysat one by one
line 9-18: 
10-11: running over the 'cnf_args' list , converting the 'arg' into string and than spliting it by | (or) link 
'str_arg_splited' is a list that contains the variables { e.g. in the first iteration of the for loop: ['A', '~C'] , in the second iteration of the for loop: ['B', '~C'] }
12: creating the list ('or_clause') of clauses that will go into the 'and_clause' list - between the elements in the 'or_clause' the pysat will add | (or) link.
13-16: running over the symbols in every element on the 'str_arg_splited' >> if the symbol if in False status we will convert the ~ (not) into '-' (the pysat don't work with '~') and add it into the 'or_clause' list 
18: insert the 'or_clause' list into the 'and_clause' list
line 20: return the 'and_clause' list
