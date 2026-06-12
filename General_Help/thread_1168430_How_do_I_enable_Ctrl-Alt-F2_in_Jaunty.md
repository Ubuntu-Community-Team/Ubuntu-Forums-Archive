---
title: "How do I enable Ctrl-Alt-F2 in Jaunty?"
date: 2009-05-24
forum: General Help
---

### Post by pathorn on 2009-05-24
I have been using ubuntu since Dapper with no real issues (except for the nvidia splashscreen thing which is finally fixed in the latest release!). However, with the latest upgrade, I am no longer able to turn off the X server easily. Yes, I can reboot into failsafe mode which will disable the web server on this computer--not something I want to do unless I have to.  And yes, I can SSH in but only if I happen to have my laptop booted, and this is again a major inconvenience in some cases.

Ctrl-Alt-Backspace is disabled.  This I understand since it is far too easy to accidentally press.  I do not want to enable this.

However The problem is that Ctrl-Alt-F1,F2,F3... do not work any more from within the X server. In addition, GDM provides no "Switch to terminal" command, which leaves me with no way to get to the console aside from mashing Alt-SysRQ-k 5 times in a row.. not only does this cause my monitor to flicker madly but it just doesn't feel like the right way.

I realize this is due to a change in XOrg itself. While it might not be possible to change via a configuration variable, I am willing to compile xorg from source and make the necessary modifications if necessary.

Yes, I have tried setting this option in /etc/X11/xorg.conf but it does nothing useful:
```
Section "ServerFlags"
        Option  "DontZap"       "False"
EndSection
```

And the package is installed:```
dontzap:
  Installed: 0.1.2
  Candidate: 0.1.2
```

Any ideas?

---

### Post by pathorn on 2009-05-24
I found out about the DontVTSwitch, AllowDeactivateGrabs and DontZap variables.
I tried them all to no avail, in both the ServerFlags and ServerLayout sections.  I know the config was being read because I could change the resolution in xorg.conf and it would listen to that.

I have a feeling that these are all related. I also cannot zoom in the screen with Ctrl-Alt-Numpad+ or Numpad-, and I found a post mentioning xkb, so perhaps it is something to do with how my modifier keys are set up.

Anyway, I found a workaround, but not one I exactly like: If you type "Alt-Sysrq-r" it will take the keyboard out of Raw mode, which means that the Alt-F1,... will work just as in a console.  The problem is that the keys are stuck this way until you restart the x server, and then hitting Alt-F1 (with or without ctrl) will switch to the console.

So basically this works, but with the side effect that I cannot use a couple function key shortcuts without switching to the console.  It also has another side effect that will cause it to spam Print Screen shortcuts endlessly. However, gnome is much more efficient than kde in this regard and it's actually possible to close them without having the computer lock up. This one has happened to me on several occasions, so I think there is something else going on here. Oh well.

Would still like to know how everyone else gets the crtl-alt-F1 and friends to work.

---

### Post by Liquid Sky on 2009-09-18
I too am unable to use ctrl-alt-f1(6).  I am using Jaunty server, and put xubuntu-desktop on.
 
I use an NVIDIA driver (the new one, umm...190).
 
I have two monitors, and use Twin.  with Xinimatic.
 
What I think is happening, is when you try to drop down into the shell, it doesnt know what graphic mode to be in...because, even though my monitor's are off....I can still log in, and type commands.  I proved it by logging in, typing sudo reboot, and then my password.  Sure enough, I rebooted. 
 
So the ctrl-alt-f2 is working, its just I cant see what is going on...I am going to try a few things, like changing my video in grub...

---

### Post by Liquid Sky on 2009-09-18
Okay, I definitely tracked the problem down to Xinimatic.  When I use my NVidia Twinview, I can ctrl-alt-f1 into a terminal window, and see what I am doing.  Ctrl-Alt-F7 brings me back to my GUI.  Lots of fun in xorg.conf

---

