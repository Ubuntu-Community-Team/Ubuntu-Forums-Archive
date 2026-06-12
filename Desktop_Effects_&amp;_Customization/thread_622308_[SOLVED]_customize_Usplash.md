---
title: "[SOLVED] customize Usplash?"
date: 2007-11-24
forum: Desktop Effects &amp; Customization
---

### Post by staticvoid on 2007-11-24
Hi, when ubuntu boots up there is noscreen showing its loading. Same with when it logs in. How can I both make it visile and change it? I tried SUM so far. Where are the config files for Usplash? I heard about another thing called "splashy" is this better? can I replace usplash with this?

Thanx :)

sv

---

### Post by staticvoid on 2007-11-25
is an 18 hour wait to early to bump? sorry, anybody have this usplash problem?

---

### Post by staticvoid on 2007-11-26
still trying with no avail...

---

### Post by mrmiserable on 2007-11-26
sudo gedit  /etc/usplash.conf

# Usplash configuration file
xres=1024
yres=768

this is mine if yours is eg xres=1280
                                        yres=1024

change to lower resolution then reboot and see

good luck

 poor that it has taken so long

---

### Post by staticvoid on 2007-11-26
Yay!! Thank you so much mrmiserable!  :) I'll try my rez, then some lower ones. Thank you thank you thank you  :D

sv

---

### Post by mrmiserable on 2007-11-26
no problem

---

### Post by erginemr on 2007-11-26
> **mrmiserable said:**
> sudo gedit  /etc/usplash.conf

# Usplash configuration file
xres=1024
yres=768

this is mine if yours is eg xres=1280
                                        yres=1024

change to lower resolution then reboot and see

good luck

 poor that it has taken so long

Hello,

In addition to the above info, which is 100% correct, you may also have to issue the following command from the console:
sudo dpkg-reconfigure -phigh usplash

This command will put the above change in the config file in to effect.So, you may try using it, if the above change only does not make any difference in your system.

You may also consider reading the following thread, for an in-depth discussion of the problem:
[http://ubuntuforums.org/showthread.php?t=604216](http://ubuntuforums.org/showthread.php?t=604216)

Good Luck.

---

### Post by staticvoid on 2007-11-26
ok, thanks

i'll reboot and try it out

edit: it didn't work, i'll try running the command sudo dpkg-reconfigure -phigh usplash thanx.

---

### Post by staticvoid on 2007-12-01
ok, after toying around with SUM, and adjusting those resolution properties it worked. I'll marked this solved.

sv

---

