---
title: "info"
date: 2005-09-11
forum: Desktop Environments
---

### Post by belred on 2005-09-11
i can't seem to find the info pages for the ls command in the help (lifesavor) in  kmenu).  the entire alphabetical L section is missing.  i also typed info:ls in konquerer and it said try man instead.  my gentoo coworkers have it so i know it's available.  how do i install all the missing info pages for kubuntu?

thanks,

bryan

---

### Post by mlomker on 2005-09-11
Have you tried **man:/** in Konqueror?

---

### Post by belred on 2005-09-11
[QUOTE=mlomker]Have you tried **man:/** in Konqueror?[/QUOTE]

yes, but i'm trying to learn about info too.  how do i install the missing info pages?

bryan

---

### Post by cwaldbieser on 2005-09-11
[QUOTE=belred]yes, but i'm trying to learn about info too.  how do i install the missing info pages?

bryan[/QUOTE]
Is it available from the terminal if you type "info ls"?  It should have been provided as part of the "coreutils" package.  If it is just missing from KDE/Konqueror, maybe something like Scrollkeeper needs to be run?

---

### Post by belred on 2005-09-11
[QUOTE=cwaldbieser]Is it available from the terminal if you type "info ls"?  It should have been provided as part of the "coreutils" package.  If it is just missing from KDE/Konqueror, maybe something like Scrollkeeper needs to be run?[/QUOTE]


it works from the command line, but it seems to be using the man pages... maybe i'm wrong:

$ info ls

File: *manpages*, Node:  Ls, Up: (dir)

LS(1)          User Commands      LS(1)

NAME
          ls - list directory contens

SYNOPSIS
          ls [OPTION]... [FILE]...


is info using the man pages for ls?  so ls doesn't show up in KDE help.  and it shows an error when you type info:ls in konquerer and gives you a link to the man pages.  

i'm using kubuntu hoary.


bryan

---

### Post by cwaldbieser on 2005-09-11
[QUOTE=belred]it works from the command line, but it seems to be using the man pages... maybe i'm wrong:

$ info ls

File: *manpages*, Node:  Ls, Up: (dir)

LS(1)          User Commands      LS(1)

NAME
          ls - list directory contens

SYNOPSIS
          ls [OPTION]... [FILE]...


is info using the man pages for ls?  so ls doesn't show up in KDE help.  and it shows an error when you type info:ls in konquerer and gives you a link to the man pages.  

i'm using kubuntu hoary.


bryan[/QUOTE]
No, when I do an "info ls" in Hoary, I get an info screen (File: coreutils.info).
Try:
```
dpkg -L 'coreutils' | grep coreutils.info.gz
``` 
It should tell you 
```
/usr/share/info/coreutils.info.gz
```
If not, you probably just need to get that file.  I am not sure if I'd be brave enough to try reconfiguring the coreutils package.  If you want, I could just post the file for you.

---

### Post by belred on 2005-09-11
[QUOTE=cwaldbieser]No, when I do an "info ls" in Hoary, I get an info screen (File: coreutils.info).
Try:
```
dpkg -L 'coreutils' | grep coreutils.info.gz
``` 
It should tell you 
```
/usr/share/info/coreutils.info.gz
```
If not, you probably just need to get that file.  I am not sure if I'd be brave enough to try reconfiguring the coreutils package.  If you want, I could just post the file for you.[/QUOTE]



when i do the dpkg command as you suggested i does return the same as what you got.  but "info ls" does not pull up the info stree wiht File:coreutils.info.  at least i can't tell if it is.  just looks like the man pages to me.

bryan

---

### Post by cwaldbieser on 2005-09-11
[QUOTE=belred]when i do the dpkg command as you suggested i does return the same as what you got.  but "info ls" does not pull up the info stree wiht File:coreutils.info.  at least i can't tell if it is.  just looks like the man pages to me.

bryan[/QUOTE]
What if you do:
```
$ info -f /usr/share/info/coreutils.info.gz ls
``` 
(i.e. manually speficy the info file)?  Maybe some environment variable (INFOPATH) just needs to be set in your .bashrc.

---

### Post by belred on 2005-09-11
[QUOTE=cwaldbieser]What if you do:
```
$ info -f /usr/share/info/coreutils.info.gz ls
``` 
(i.e. manually speficy the info file)?  Maybe some environment variable (INFOPATH) just needs to be set in your .bashrc.[/QUOTE]


using this command i now see info's ls instead of man's ls, so you are right.  there must be some environment path that is not set.  this might explain why i don't see it in konquerer or kde's help.  i just installed the stock kubuntu hoary and it should have been set.  it would be nice if someone made sure it works in breezy out of the box.   can you print out what your INFOPATH variable? i don't have one in my .bashrc.

thanks,

bryan

---

### Post by mommebu on 2007-12-11
Same problem still present in Gutsy...any hints?

---

