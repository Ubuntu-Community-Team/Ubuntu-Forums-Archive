---
title: "Uncloseable windows"
date: 2010-11-12
forum: Desktop Environments
---

### Post by Fracta on 2010-11-12
I have two questions:

First, I am running ddrescue in a terminal and I want to know how I can make sure no one closes it. It is currently on another desktop as a temporary solution. But I can't trust myself to not accidentally close it. Surely there must be some simple way to use root or something to make it permanent?

Scondlt, dammit cat you are always friendly at the wrong times, how can i do the bash equivalent of the dos command "dir *.exe"? ignore the actual exe part, I know linux doesn't use extensions, its just an example. 

thanks ouch clawes

---

### Post by coffeecat on 2010-11-12
> **Fracta said:**
> dammit cat

:shock:

> **Fracta said:**
>  how can i do the bash equivalent of the dos command "dir *.exe"? ignore  the actual exe part, I know linux doesn't use extensions, its just an  example. 

Use one of:

```
ls *string
ls string*
ls *exe
ls *deb
```... and so on

```
ls -l
```... is somewhat more useful, but see 'man ls' for more options.

Also, you may know this, but because Linux doesn't recognise extensions as such, just as strings, you don't need to include the point with wildcards for all extensions. Linux treats a point as just another character, not a divider between filename and extension. So...

```
ls *
```... has the same effect as...

```
dir *.*
```Sorry I can't help with the first part.

---

### Post by Fracta on 2010-11-15
The only threads I can find are about uncloseable windows when people actually want to close them. Surely it can't be much of an issue to set a window to be controlled by root or something so that me (a not root user) can't close it?

---

