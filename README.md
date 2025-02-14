# tsh - A tiny shell program with job control

This is a tiny shell program with job control.

Each command line is evaluated by the eval function. The code
of the eval function is broken up into several helper functions,
each for a specific kind of command. For example, the eval_exec
function forks a child process, executes a program and adds the job
into the job list. If it is a foreground job, the function waits
it to terminate or stop.

Every time the shell receives a SIGCHLD signal, the handler
changes the state of the child in the job list appropriately.

Other handler functions send signals to child processes to
control them when corresponding signals are received by the shell.