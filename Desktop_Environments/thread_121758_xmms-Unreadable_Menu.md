---
title: "xmms-Unreadable Menu"
date: 2006-01-25
forum: Desktop Environments
---

### Post by Proleter on 2006-01-25
When I start xmms the menus are unreadable. There are only some wierd characters.

This solves the problem:
```

export LC_ALL=bg_BG.cp1251
xmms %U

```
but I dont plan to open the terminal and code my way to xmms.
I tried to put this in my xmms shortcut but there is error.
```
"export" (No such file or directory)
```
I suppose it's easy to solve the problem but how?

---

### Post by heimo on 2006-01-25
[quote=Proleter]
```
"export" (No such file or directory)
``` I suppose it's easy to solve the problem but how?[/quote] 
I don't know if this works from shortcut, but you should be able to put those on the same line, like this:
```
LC_ALL=bg_BG.cp1251 xmms %U
``` Does this solve the problem?

---

### Post by Proleter on 2006-01-25
[QUOTE=heimo]I don't know if this works from shortcut, but you should be able to put those on the same line, like this:
```
LC_ALL=bg_BG.cp1251 xmms %U
``` Does this solve the problem?[/QUOTE]
Still the same message:
```
Details: Failed to execute child process 
"LC_ALL=bg_BG.cp1251" (No such file or directory)
```



Thanks anyway!

---

### Post by heimo on 2006-01-26
How about?
```
env LC_ALL=bg_BG.cp1251 xmms %U
```

---

### Post by Proleter on 2006-01-26
[QUOTE=heimo]How about?
```
env LC_ALL=bg_BG.cp1251 xmms %U
```[/QUOTE]

That worked great! Thanks.
Can you explain me wath I just did?

---

### Post by heimo on 2006-01-27
[quote=Proleter]That worked great! Thanks.
Can you explain me wath I just did?[/quote]

env lets you "run a program in a modified environment" (from manual page), normally you can change environment variables (like LC_ALL) just by adding it before the command, or using export - but this is also one way to achieve (pretty much) same thing. So, what you did, you set an environment variable for just xmms - more specifically you set so called *locale.*

> In [computing]("http://en.wikipedia.org/wiki/Computing"), **locale** is a set of [parameters]("http://en.wikipedia.org/wiki/Parameter") that defines the user's language, country and any special variant preferences that the user wants to see in their [user interface]("http://en.wikipedia.org/wiki/User_interface"). Usually a locale identifier consists of at least a language identifier and a region identifier.
 [*source*]("http://en.wikipedia.org/wiki/Locale")   

>  Environment variables have names and store a value, and they affect the way a program operates. Think of an environment variable as a calculator memory with a name. Certain programs expect certain environment variables to be set.  For example, the shell that interprets your commands uses an environment variable called PATH which tells the shell where to look for commands. 
 [source]("http://www-biocomp.doit.wisc.edu/env.shtml")

---

### Post by Proleter on 2006-02-07
Heimo thank you very much for the detailed explanation.

---

