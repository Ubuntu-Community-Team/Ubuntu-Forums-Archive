---
title: "Switch layout only by Shift Control Right (Shift + Control R)"
date: 2014-08-28
forum: Desktop Environments
---

### Post by ElizaSh on 2014-08-28
Ubuntu 14.04 updated from 12.04.
Gnome Desktop

I prefer to switch between language layout by right shift ctrl, but it switches by both right and left shift ctrl and it is annoying when you use terminal. 
I tried work around with 
dconf:
org -> gnome -> libgnomekbd > options -> ['grp\tgrp:ctrl_shift_toggle'] 
tweak tool:
switch layout Shift R + Control R
even: 
> sudo dpkg-reconfigure keyboard-configuration
Nothing works.
 Now I am using Shift + Control + Alt R, and Shift + Control + Alt L do not switch layouts.
Does any one have any idea what is it?And how to solve it?

Thanks in advance!

---

