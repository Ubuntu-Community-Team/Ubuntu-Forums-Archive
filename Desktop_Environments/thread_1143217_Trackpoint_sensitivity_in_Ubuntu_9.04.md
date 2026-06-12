---
title: "Trackpoint sensitivity in Ubuntu 9.04"
date: 2009-04-29
forum: Desktop Environments
---

### Post by lukas.mach on 2009-04-29
Hi, 

I've been using Ubuntu 8.10 for some time now. When I installed 9.04, I noticed that trackpoint on my notebook/tablet is moving very slowly. The mouse settings (in System > Preferences) are not affecting the sensitivity of the trackpoint (I have both on maximum and it still moves extremely slowly). 

Does anybody know how to change the sensitivity? My notebook is HP 2730p. I tried configure-trackpoint package, but it says that trackpoint is not detected.

---

### Post by Chubbafied on 2009-05-11
I too have this exact same problem.  I've installed on a ibm x41 tablet.

I'm new to linux and most of the stuff i read says to edit information in the xorg.conf file pertaining to "Configured Mouse".  The problem is with the new build there is no mouse section. 

I've tried copy pasting other xorg.conf files and even dabbling in writing in some sections on my own, but that has only resulted in crashes or no change at all.

Any one with a solution?  

The search continues for me...

---

### Post by rainwalker on 2009-05-11
Have you tried adjusting the acceleration rather than sensitivity?

---

### Post by AncientPC on 2009-05-11
> **Chubbafied said:**
> I too have this exact same problem.  I've installed on a ibm x41 tablet.

I'm new to linux and most of the stuff i read says to edit information in the xorg.conf file pertaining to "Configured Mouse".  The problem is with the new build there is no mouse section. 

I've tried copy pasting other xorg.conf files and even dabbling in writing in some sections on my own, but that has only resulted in crashes or no change at all.

Any one with a solution?  

The search continues for me...
[configure-trackpoint]("http://tpctl.sourceforge.net/configure-trackpoint.html") doesn't work for lukas.much, but have you tried it?

You might also try: [http://www.thinkwiki.org/wiki/How_to_configure_the_TrackPoint](http://www.thinkwiki.org/wiki/How_to_configure_the_TrackPoint)

---

### Post by Chubbafied on 2009-05-12
Ah the thinkwiki is such an incredible resource!  It WORKS!!

I initially tried running the 
"echo -n 160 > /sys/devices/platformi8042/serio1/serio2/speed"
command, but encountered 2 hurdles: 1) The location of the "speed" file was different on my computer.  Simple fix, just find the file and correct the command.  and... 2) I had problems with the terminal telling me i didn't have access.  This was solved by entering "sudo su" in the terminal to get into root mode, and after entering the commands the sensitivity was immediately noticable.

In order to have the changes work after a suspend/resume/restart i edited the etc/rc.local file with the added sensitivity commands (in root mode).

This Linux stuff is crazy bewildering, but the feeling of accomplishment reminds me of the ol' days coding stuff for my computer science class in fortran and C+.

---

### Post by undoIT on 2010-04-14
> **Chubbafied said:**
> Ah the thinkwiki is such an incredible resource!  It WORKS!!

I initially tried running the 
"echo -n 160 > /sys/devices/platformi8042/serio1/serio2/speed"
command, but encountered 2 hurdles: 1) The location of the "speed" file was different on my computer.  Simple fix, just find the file and correct the command.  and... 2) I had problems with the terminal telling me i didn't have access.  This was solved by entering "sudo su" in the terminal to get into root mode, and after entering the commands the sensitivity was immediately noticable.

In order to have the changes work after a suspend/resume/restart i edited the etc/rc.local file with the added sensitivity commands (in root mode).

This Linux stuff is crazy bewildering, but the feeling of accomplishment reminds me of the ol' days coding stuff for my computer science class in fortran and C+.

Hi. I was able to get the settings adjusted for the current session using sudo su and then issuing the commands.

However, the settings do not stick after adding the commands to the rc.local file.

I added the following to rc.local:
```

echo -n 250 > /sys/devices/platform/i8042/serio1/serio2/speed 
echo -n 250 > /sys/devices/platform/i8042/serio1/serio2/sensitivity 
```

Any ideas how to get the settings to stick for Ubuntu Lucid?

---

### Post by pgriffiths on 2010-05-26
You can add a WAIT_FOR condition in  /etc/udev/rules.d/trackpoint.rules. See [http://ubuntuforums.org/showthread.php?p=9365735](http://ubuntuforums.org/showthread.php?p=9365735)

---

