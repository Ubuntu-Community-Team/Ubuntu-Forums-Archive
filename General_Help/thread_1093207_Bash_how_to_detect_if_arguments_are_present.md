---
title: "Bash: how to detect if arguments are present"
date: 2009-03-11
forum: General Help
---

### Post by lorderico on 2009-03-11
Currently, I use $1 and $2 in my bash script.  It gives me a "unary operator expected" if I don't include a first and second argument.  Is it possible to detect whether there is an argument.  If not, print out my own error message.

Thanks for your help,
Eric

---

### Post by heindsight on 2009-03-11
The special parameter # gives the number of arguments (positional parameters).

Thus you could use something like:
```
if [ $# -ne 2 ]; then
  echo "Expected 2 arguments!"
  exit 1
fi
```

You may want to read [The Advanced Bash-Scripting Guide]("http://tldp.org/LDP/abs/html/index.html") and the bash manual:
[http://manpages.ubuntu.com/bash](http://manpages.ubuntu.com/bash)

---

### Post by lorderico on 2009-03-11
Thanks a lot.  That solution works well.

Eric

---

