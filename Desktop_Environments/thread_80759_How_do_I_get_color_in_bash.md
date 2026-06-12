---
title: "How do I get color in bash?"
date: 2005-10-22
forum: Desktop Environments
---

### Post by Mizzou_Engineer on 2005-10-22
I was curious as to how to get colorized outputs in the bash shell when I did something like "ls -l." I used to run SuSE and this was a nice feature of the OS. 

Any add-ons or cheat codes to get this enabled would be appreciated.

---

### Post by adwait on 2005-10-22
There already are colours there.......
What are you using? Terminal right?

---

### Post by orzechowskid on 2005-10-23
try:

$ ls --color=auto

If that works, then do:

$ alias ls='ls --color=auto'

though an alias for ls should really already be stored somewhere.  I know Breezy came with it turned on by default, if you're using the Bash shell.  Check ~/.bashrc or /etc/profile.

If all else fails, or you want to set your own colors, try:

$ man dircolors

for more help.

---

### Post by naomi on 2005-10-23
I have another question regarding colors in bash: I use a light background, but the auto colors are better for a dark background. However I remember there was some command to set the auto colors for a light background... can anybody tell me the command, please?

Thanx,
Naomi

---

