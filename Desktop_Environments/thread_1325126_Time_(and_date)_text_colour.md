---
title: "Time (and date) text colour"
date: 2009-11-13
forum: Desktop Environments
---

### Post by Lord Stig on 2009-11-13
Just a minor thing: is there any way to change the text colour on XFCE's time display? I'm currently using a glossy balck theme and the text colour is also black. Tried the obvious rightclick, properties but there isn't a text colour option.

Hopefully just a quick change to a hidden config file somewhere?

---

### Post by Lord Stig on 2009-12-16
Bump.
Sorry, I know there are more important issues for people to look at but if anyone has a quick workaround it'd be appreciated.

---

### Post by rabidbadger on 2009-12-17
Have a look [here]("http://wiki.xfce.org/tips#gtkrc_files"); the 'fg[NORMAL]' panel colour affects the clock. HTH.

---

### Post by Lord Stig on 2009-12-20
Thanks. The .gtkrc-2.0 file only says 
> include ".gtkrc-white"
so guessed that it was in fact pointing this file because of a particular theme I'm using. I changed fg NORMAL to "fff000" (I'm not overly familiar with colours in hexadecimal so took a guess. It's changed my default icon text labels to yellow but left the clock with black text. Don't know if Emerald is overwriting something.

---

