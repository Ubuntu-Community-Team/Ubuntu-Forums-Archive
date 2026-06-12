---
title: "Implementing Graphical Process/Application-killer in X (or other escape hatch)"
date: 2007-06-30
forum: Desktop Environments
---

### Post by Yfrwlf on 2007-06-30
If a program becomes unresponsive in Ubuntu, you currently can use several different methods to close it, including clicking on the X to close the window and hope the &#8220;force quit&#8221; dialog box comes up, adding xkill/Force Quit/System Monitor to a panel to use on the application, running kill/xkill/killall from an X terminal, run them from a tty other than F7, or hitting ctrl-alt-backspace (which makes you lose any unsaved work).  Some of those are fine and great for new users, and some are fine and great for advanced users, but there are big problems with this system for both new and advanced users.

1)  Currently, I don't think even Feisty has a standard hot key to use to either bring up a processes list to close an app, or to kill the currently running app, or run xkill.  There IS a &#8220;close window&#8221; hot key though, but I do believe that when an app is frozen &#8220;harder&#8221;, the hot key will not work because in some instances the force quit dialog will never come up and other, more drastic methods need to be used like sending a kill for the process.  My close window hot key, which is the default most likely, is currently set to Alt-F4.  Perhaps a more intuitive default hot key should be made for this, but that doesn't address the problem if it fails.  Perhaps one of the solutions is to fix the Close Window function so that it never fails, even in the following situation...

2)  When in full-screen mode, because of a game or what have you, there is no way to click on an X to close the application.  The Close Window function does not work in this mode, I've tried it.  The only way I know how to kill a full-screen app that won't let you out of it is to jump to a tty and do a kill or killall or top or whatever.  Normal nooblets who don't know the commands for such things, and would scream and run away from the command line, can't be expected to do this.  Perhaps X needs a system similar to (yes, I'm going to go there!) Windows' Control-Alt-Delete menu that provides a graphical escape route from the clutches of rude applications.  There needs to be some kind of emergency kill button that is NOT the power button, or a menu, or some way of being able to kill an app without having to restart X.  Maybe it should go deeper than X though, to the kernel, which brings me to my third point...

3)  Sometimes X itself will freeze.  It happens very rarely, but it can indeed happen.  Unfortunately, for some reason that I just can't fathom, it almost seems like no one has thought of making an escape route directly back to the kernel or tty.  Yes yes, Alt-F# you're thinking, but the problem is this doesn't always work.  Many times I've had X freezes where all the hot keys are frozen as well.  The mouse moves around on the screen, so the kernel is still active, and I can remote in through SSH or whatnot.  However, it seems  like X is blocking those hot keys like the Alt-F# and Ctrl-Alt-Back keys from reaching the kernel or whatever is controlling the tty displays.  I'm not sure if it's X to &#8220;blame&#8221;, or the kernel to &#8220;blame&#8221;, perhaps for not holding onto certain hot keys so that other applications can't take them over.  IMO, there should always be some kind of escape route, as long as the kernel is still functional.

Does anyone else have any thoughts about this, and possible solutions for these problems?  You can't just say &#8220;don't use apps that crash&#8221; as that's a cop out.  Applications can't be expected to be perfect, so an escape hatch should always be available to the user.  The Alt-F# escape has been pretty good for command line-savvy users, but clearly there needs to be some additional standardized mechanism(s) put into place to address the problem for noobs, and to address the hard X lock-ups that can and do happen.  Yes, I realize the escape hatch directly to the kernel or to the tty (like Alt-F#) can't be graphical, so maybe there are multiple issues here that should be addressed.

---

### Post by Endolith on 2007-06-30
Agreed that this is needed.  Maybe you should create a blueprint on launchpad?  Or at least a bug report/feature request.

Also see this discussion:

[http://ubuntuforums.org/showthread.php?t=315404](http://ubuntuforums.org/showthread.php?t=315404)

---

### Post by Yfrwlf on 2007-07-04
I had a really long reply for that other discussion, including saying that Ubuntu never completely hard locks for me, but I left it up over night and got a hard lockup in the morning, lol. >.<  Complete kernel lock too, couldn't even SSH in.  Extremely rare as in twice a year maybe, but still annoying.

Any way, perhaps this subject is too complex for most everyone here, maybe I should have put it in a different place, or maybe I should be posting it to kerneltrap.org or something instead, or on the Xorg pages.

---

### Post by Endolith on 2007-11-30
> **Yfrwlf said:**
> Any way, perhaps this subject is too complex for most everyone here, maybe I should have put it in a different place, or maybe I should be posting it to kerneltrap.org or something instead, or on the Xorg pages.

Post it on the Ubuntu wiki and then link to it from a Launchpad Blueprint.

---

