---
title: "Compiz Fusion Help!"
date: 2007-06-28
forum: Desktop Effects &amp; Customization
---

### Post by speaker219 on 2007-06-28
I've been using compiz fusion with emerald fine the last couple of days, but I did an update last night and then tried to run compiz fusion with the emerald theme manager using the command:
```
compiz --replace -c emerald
```
That used to be working fine, but now I get the error:
```
/usr/bin/compiz.real (core) - Warn: Unknown option '-c'
```
Is it now a different parameter? It launches with GTK themes but I want to use emerald =(
help?:(

also, running:
```
emerald --replace
```
works, but I used to be able to automatically have compiz use emerald as the theme manager right away

---

### Post by speaker219 on 2007-06-28
:|

---

### Post by speaker219 on 2007-06-28
Bump

---

### Post by Mr Greencastle on 2007-06-28
I run Compiz Fusion with these two commands in the startup sessions:

Name: Compiz
Command: compiz --replace

Name: Emerald
Command: emerald --replace

Works for me... I never have to change anything.

---

### Post by dwebb86 on 2007-06-29
I am new to all this stuff, but I see many people saying you need to type the command:
compiz --replace -c emerald &

It might not matter... but
I've found that you should put the - after the c          like this
compiz --replace c- emerald &

the first command doesn't do anything for me, where the second one gets my compiz running.
hope this helps someone.

---

### Post by Mr Greencastle on 2007-06-29
You should try launching Compiz without the '-c'

Just a simple: compiz --replace
and: emerald --replace

Make sure they are in separate commands in your startup sessions.

---

