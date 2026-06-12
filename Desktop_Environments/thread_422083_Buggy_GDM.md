---
title: "Buggy GDM"
date: 2007-04-24
forum: Desktop Environments
---

### Post by Durden on 2007-04-24
I have a strange problem. I'm on a toshiba laptop and when I boot I get the GDM screen just fine and if I login quick I can get to my desktop fine. The problem occurs if I wait a minute or more, GDM stops accepting keyboard input even though the trackpad works fine and I can click on the session management and reboot/shutdown buttons. The keyboard just stops working, This doesn't happen in gnome or anywhere else. This also happens with KDM so it's not just GDM. Anyone have any ideas for me?

---

### Post by von Ippenstitch on 2007-04-26
I have the exact same problem on my ThinkPad. I can use the keyboard for less than a minute, then I can't type after that time if I don't login quickly. I think this is a problem with gdm because I've also installed xdm and logged in without any problems. 

However, after purging gdm and reinstalling, I think it should work fine after a fresh install. Try "sudo dpkg --purge gdm" then "sudo apt-get install gdm". When I tried that though, I had the same problem. Try using the non-graphical plain login window, I haven't had the same issue yet.

---

### Post by von Ippenstitch on 2007-04-28
After some googling, I found this:

```
# This is here to serve as a note to myself, and future developers.
#
# Any Display manager (gdm,kdm,xdm) has the following problem:  if
# it is started before any getty, and no vt is specified, it will
# usually run on vt2.  When the getty on vt2 then starts, and the
# DM is already started, the getty will take control of the keyboard,
# leaving us with a "dead" keyboard.
#
# Resolution: add the following line to /etc/inittab
#
#  x:a:once:/etc/X11/startDM.sh
#
# and have /etc/X11/startDM.sh start the DM in daemon mode if
# a lock is present (with the info of what DM should be started),
# else just fall through.
#
# How this basically works, is the "a" runlevel is a additional
# runlevel that you can use to fork processes with init, but the
# runlevel never gets changed to this runlevel.  Along with the "a"
# runlevel, the "once" key word means that startDM.sh will only be
# run when we specify it to run, thus eliminating respawning
# startDM.sh when "xdm" is not added to the default runlevel, as was
# done previously.
#
# This script then just calls "telinit a", and init will run
# /etc/X11/startDM.sh after the current runlevel completes (this
# script should only be added to the actual runlevel the user is
# using).
#
# Martin Schlemmer
# aka Azarah
# 04 March 2002
```

Since Ubuntu does not use /etc/inittab, this will have to go in /etc/init.d. Can anyone please translate this into plain English?

---

### Post by von Ippenstitch on 2007-04-29
Sorry for the triple post, but I think I solved it. Open a terminal and type:
```
sudo gedit /etc/gdm/gdm.conf
```
And where it shows:
```
0=Standard
```
Replace that with:
```
0=Standard vt8
```
There was advice on other forums that said to add vt7 but for some reason that didn't work for me, but vt8 works.

**Edit:** nevermind, this fix only worked after one reboot :confused:

---

