---
title: "How do I install Darwinia on Edgy?"
date: 2007-02-05
forum: Gaming &amp; Leisure
---

### Post by Falkon on 2007-02-05
I downloaded the Darwinia demo (darwinia-demo2-1.3.0.sh), but have no idea how to install it.  Can someone please give me a step-by-step walkthrough?  I'm very new to linux.
Thanks!

---

### Post by aidanr on 2007-02-05
first make the file executable by right clicking on it -> properties -> permissions
then open a terminal, applications -> accessories -> terminal
and then type "sudo sh darwinia-demo2-1.3.0.sh" and follow the instructions from there

edit:// this is assuming you've saved it to your home folder, if you saved it to the desktop, type "cd Desktop" first

---

### Post by Falkon on 2007-02-05
First off, thanks for posting so quickly, and the installation went fine.  However, it won't run.  When I go into usr/local/games/darwinia-demo2 and open darwinia,  nothing happens.  The default opening application for it is Add/Remove, so I assume this is wrong, but I don't know what to do here.

---

### Post by aidanr on 2007-02-05
it should have created a shortcut in applications -> games
if that shortcut doesn't work try typing "darwinia" in a terminal or "darw" and then tab to autocomplete because i'm not sure of the exact name of the command to launch it

and see if it prints out any error, you should also check if you've got your graphics drivers set up properly "glxinfo | grep direct" should give back "direct rendering: yes" if your drivers are set up ok

---

### Post by Falkon on 2007-02-05
Ok the shortcut did nothing, and here's what I got with "darwinia-demo2":

:~$ darwinia-demo2 
/usr/local/games/darwinia-demo2
/usr/local/games/darwinia-demo2/lib/darwinia.bin.x86: /usr/local/games/darwinia-demo2/lib/libgcc_s.so.1: version `GCC_4.2.0' not found (required by /usr/lib/libstdc++.so.6)

I'm assuming the 'GCC_4.2.0' not found (required by /usr/lib/libstdc++.so.6) is the important part here.  Is there something I need to install?

Also,  I did get 'direct rendering: Yes', but I do have integrated graphics at the moment (I'll be getting a new graphics card in a week or two) so that could be part of the problem.

However, when I ran OpenArena, it gave me a warning about my graphics card and then changed my resolution and froze my comp, which was at least more indicative of what the problem was than nothing happening as with Darwinia.

So, sorry for the long post...any ideas?

---

### Post by aidanr on 2007-02-05
try ```
sudo mv /usr/local/games/darwinia-demo2/lib/libgcc_s.so.1 /usr/local/games/darwinia-demo2/lib/libgcc_s.so.1.backup
```
and then run "darwinia-demo2"

---

### Post by Falkon on 2007-02-05
Fantastic.  I tried that and now it runs just fine.  Thanks a lot for the help!

---

### Post by glotz on 2007-02-05
Nice support job aidanr! Another satisfied customer... :D

I read it just for kicks but fail to comprehend what the libgcc thing was all about? Care to explain?

---

### Post by aidanr on 2007-02-05
renaming or deleting the included library makes the game use the system installed library instead

(read: i googled it :D)

---

### Post by glotz on 2007-02-05
Hehe, now that was too easy. :D

It's funny how when you know you're interfacing with something *new* (GNU/Linux), your brain just stops thinking because you automatically assume the old laws of physics don't apply anymore for some reason... Kudos anyways!

---

