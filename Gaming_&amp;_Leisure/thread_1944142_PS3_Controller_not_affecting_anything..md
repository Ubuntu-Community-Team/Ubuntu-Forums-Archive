---
title: "PS3 Controller not affecting anything."
date: 2012-03-20
forum: Gaming &amp; Leisure
---

### Post by jrisreal on 2012-03-20
My problem is pretty much identical to this one:
[http://ubuntuforums.org/showthread.php?t=1931627&highlight=PS3+Controller](http://ubuntuforums.org/showthread.php?t=1931627&highlight=PS3+Controller)
It's not just my computer as I have installed linux on multiple computers and each one has given me this same issue.  I have also tested it with more than one PS3 controller.  I always hear that the PS3 Controller works automatically in Ubuntu, but it has never worked for me.  The controller is recognized, but nothing happens if I press a button...it acts as if I hadn't pressed a button at all.  Does anybody know what could be the problem, here?

Info:
Sony Dualshock3 PS3 Controller.
Connected through USB.
Trying to use it in Dolphin and Mupen64.
Ubuntu 11.10
Toshiba Satellite A665

---

### Post by lite1979 on 2012-03-21
Do you have sixpair.c and the hidd patch already?

---

### Post by frostwork on 2012-03-21
not required for usb-only mode.
I'd suggest to press the PS button and check if /dev/input/js0 is ready.
if so I'd test the joypad with jstest or some similar tool.

---

### Post by jrisreal on 2012-03-28
^^ What do you mean by "check if /dev/input/js0 is ***ready***?"
Sorry, I'm relatively new to linux, so bear with me please.

---

### Post by frostwork on 2012-03-28
I meant you should check if the devicenode even exists.
after having pressed the PS button (probably even already before) you should see at least see some entry at the end of the "dmesg" output.
would be interesting if tests with jstest or some similar tool suceed.
maybe also the evdev drivers take over control over your joypad and use it as some xf86-input device. /var/log/Xorg.0.log should know then.
good luck so far!

---

### Post by jrisreal on 2012-03-29
Thanks for the help!  I just switched to XFCE yesterday...will try it out again later, its possible that the Xubuntu install could have fixed it.

EDIT: Nope, XFCE didn't do any better.

---

### Post by jrisreal on 2012-03-29
Ooh!  I tried "jstest /dev/input/js0" and I can see values changing as I press buttons on the controller!!  Now, there is a new problem, however.

In mupen64plus, the moment I click on a parameter to assign to the controller, the dialogue box appears and disappears.  Any ideas?

---

