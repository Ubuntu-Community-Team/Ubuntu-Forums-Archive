---
title: "Blank screen issue"
date: 2010-07-12
forum: Desktop Environments
---

### Post by skolor on 2010-07-12
(I'm fairly sure this is at least a decent place to post this, but if not, I apologize in advance)

I have been a long time Windows user, and recently switched my desktop to Ubuntu 10.04 to give it a try. After getting it installed, I've spent a few weeks using it without issue. Over the weekend, I decided to upgrade the NVidia drivers since I may or may not have been having issues running CUDA applications.

So, I went online, and found one of the many "Upgrade NVidia drivers" posts, and followed it. I stopped X/GDM, and removed the existing drivers. I then went to run the driver supplied by NVidia (I am not sure what exactly it was, although I can find the version if it is important. It was whatever the most recent version is). When running the driver, it said something about X not being stopped, and to restart the computer. I did so.

After restarting the computer, I cannot get past the initial Ubuntu splash screen. From what I have read about this, I have already tried the following:

[LIST]
[*]Using the Ubuntu LiveCD, reverted to my xorg.conf.backup, and then xorg.conf.failsafe, with no change.
[*]Tried pressing ctrl+alt+f1 at various times during the boot up process to get a console. Once I do this the monitor goes blank.
[*]Used the recovery console, and tried the same ctrl+alt+f1 to try and get a console there. Both way, the screen goes blank and does not come up
[/LIST]

In any case, no sound is played when starting up, and I cannot get the computer to respond. If I do ctrl+alt+del once the screen goes blank, the Ubuntu splash comes up, and then the PC restarts. 

Any ideas I could try? I could just re-install, but I'd like to take this as a learning experience and try and fix it. I don't have a lot of data I would lose, but it would be some (admittedly less than it would take to replicate in the time I've spent troubleshooting so far). Any help would be appreciated.

---

### Post by pytheas22 on 2010-07-13
It sounds like your system might be seriously shot, if you can't even get to a command prompt using the recovery console.  What exactly happens when you try to boot in recovery mode?  If it hangs, what's the last thing you see on the screen before it stops responding?  Also, when it stops responding, if you press numlock of capslock on your keyboard, do the respective lights come on?

---

### Post by skolor on 2010-07-13
It does the same thing: Ubuntu splash screen, then goes blank (and the monitor says there is no signal).

I've also tried both the on-board video, and the NVidia 9800 GT I was using. 

I was thinking about it last night, and I think I might have a solution: tonight I'll try and use the LiveCD to enable SSH on the machine, boot and try and SSH in, and then finish the driver install.

---

### Post by pytheas22 on 2010-07-13
> I was thinking about it last night, and I think I might have a solution: tonight I'll try and use the LiveCD to enable SSH on the machine, boot and try and SSH in, and then finish the driver install.

That could work, assuming the machine is getting far enough along in the boot process to start an ssh server.  However, I can't think of an easy way to install an ssh server using the live CD.

One thing you could try, and which would be possible to do from the live CD, is editing /etc/X11/xorg.conf (or creating it if it doesn't exist) and adding this section:
```

Section "Device"
        Identifier      "Configured Video Device"
        Driver          "nouveau"
EndSection
```

This will tell the system to use the open-source "nouveau" driver, which may work better than the proprietary one that you tried to install and which seems to be causing your system not to boot properly.

If "nouveau" doesn't help, you could also try "vesa" by putting that in your xorg.conf file.  vesa is a very simple fallback video driver that should always work.

---

