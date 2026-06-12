---
title: "Umlauts Unicode and KDE"
date: 2005-05-22
forum: Desktop Environments
---

### Post by t.knopp on 2005-05-22
Hi!

I have installed Hoary and after that kubuntu. The Problem in all kde programs are umlauts. Example: in kwrite i can't see the umlauts of a text file. There is just a rect. In gedit, vi i see them. I made dpkg-reconfigure locales an set it to UTF-8.
The strange thing is, when i start kwrite with

LANG=UTF-16 kwrite

all is fine. But in dpkg-reconfigure locales i can't set to UTF-16. Can I set that option anywhere in kcontrol for kde programs?
Any Ideas?

Thanks

Tobi

---

### Post by Takis on 2005-05-22
How about using an alias in your .bash_aliases file (if it exists)?

Create/edit ~/.bash_aliases, and add lines like this every time you need them:
```
alias kwrite='LANG=UTF-16 kwrite'
```
You might need to edit your .bashrcfile (~/.bashrc) and change
```
#if [ -f ~/.bash_aliases ]; then
#    . ~/.bash_aliases
#fi
```
to
```
if [ -f ~/.bash_aliases ]; then
    . ~/.bash_aliases
fi
```

---

### Post by t.knopp on 2005-05-23
That can't be the solution, because the Problem exists in all KDE programs. Am I the only one having that Problem?

---

### Post by Sam on 2005-05-23
I had a similar problem, and I set the locale to ISO-8859-1 and this worked.

---

