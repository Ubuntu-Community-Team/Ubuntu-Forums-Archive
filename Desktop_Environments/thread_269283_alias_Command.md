---
title: "alias Command?"
date: 2006-10-01
forum: Desktop Environments
---

### Post by OPaul on 2006-10-01
How do I make an alias remain after I logout and back in? For instance, if I do the following;
```
alias poo=ls
```
And then log out and back in again, the alias is gone.

---

### Post by Ramses de Norre on 2006-10-01
Check for this lines in ~/.bashrc:```
if [ -f ~/.bash_aliases ]; then
    . ~/.bash_aliases
fi

```
Make sure they are uncommented.
Then add your aliases to ~/.bash_aliases like this:```
alias oowriter='oowriter --widgets-set gtk'
```one alias per line.

---

### Post by prateek_urmaliya on 2007-10-08
thanks :) Ramses

---

