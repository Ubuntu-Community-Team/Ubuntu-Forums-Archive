---
title: "Running a shell script from a launcher; environment variables not recognized"
date: 2009-01-25
forum: General Help
---

### Post by algernon83 on 2009-01-25
I've got a shell script set up that does exactly what I want to do when executed from the command line. I set up a launcher that points to it, but it gives me odd results. It's as if an environment variable set in my .bashrc does not exist when the launcher is used. How can I set up a launcher so that my environment variables still exist?

---

### Post by x22 on 2009-01-26
from man bash:

"When bash is started non-interactively, to run a shell
script, for example, it looks for the variable BASH_ENV
in the environment, expands its value if it appears
there, and uses the expanded value as the name of a
file to read and execute.  Bash behaves as if the
following command were executed: 

if [ -n "$BASH_ENV" ]; then . "$BASH_ENV"; fi

but the value of the PATH variable is not used to
search for the file name."

so you could have BASH_ENV=/home/you/.bashrc

---

