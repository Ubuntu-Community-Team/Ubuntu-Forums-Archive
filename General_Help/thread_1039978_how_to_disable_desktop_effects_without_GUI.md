---
title: "how to disable desktop effects without GUI?"
date: 2009-01-15
forum: General Help
---

### Post by hailholyghost on 2009-01-15
I was playing around with the desktop effects, inadvertently changing them so everything changes black when the cursor moves over an object on the GUI.  I can't do anything with the computer now.
I saw an article here [http://ubuntuforums.org/showthread.php?t=439895](http://ubuntuforums.org/showthread.php?t=439895) in which someone had a similar issue.  His/her solution followed: 

1) Log in to the terminal window in failsafe mode.
2) In the terminal window, type "gconf-editor"
3) Navigate to /desktop/gnome/applications/window_manager

Now, 2 key(entries) called "Current" and "Default" must be deleted.  The thing is, I don't know how to do that since there is no delete option, so I can't follow his instructions.  This is a very old posting, so I don't think the original author will check up on it.

please help?:confused:

Thanks in advance :)

---

### Post by Fale on 2009-01-15
Excatly same problem here.

Can't log in to change faulty settings in compiz advance manager...

---

### Post by halovivek on 2009-01-15
Same problem. i could  not get my desktop back.

---

### Post by Fale on 2009-01-15
I found solution for my problem.

On logins screen I choosed "Fail safe terminal" which let me go to terminal where I typed "ccsm" which is config for that Advanced Compiz config settings manager. That opened fine and I went to "Preferences" --> "Reset to defaults" 

No idea if this help on your problem, but at least mine is solved now.

---

### Post by hailholyghost on 2009-01-15
> **Fale said:**
> I found solution for my problem.

On logins screen I choosed "Fail safe terminal" which let me go to terminal where I typed "ccsm" which is config for that Advanced Compiz config settings manager. That opened fine and I went to "Preferences" --> "Reset to defaults" 

No idea if this help on your problem, but at least mine is solved now.

Changing the settings to default in the "failsafe terminal session" doesn't work unfortunately.  I also tried turning off all of the effects, and no deal.  Every time I move the cursor over anything on the desktop in the normal session, it has a black box over it that doesn't go away.  Sometimes it has a line of "snow" over the black box.  I've also tried GNOME and "failsafe GNOME".

I've tried numerous purges and re-installations of the GNOME desktop. I finally installed the Xubuntu desktop, which has the same problem.  
After each of the installations, the shell always gives the following:

Sub-process /usr/bin/dpkg returned an error code (1)

I've also tried typing "sudo dpkg-reconfigure ubuntu-desktop" which didn't work either.

Errors were encountered while processing:
Linux-image-2.6.24-19-generic
Linux-restricted-modules-2.6.24-19-generic
Linux-image-2.6.24-23-generic
Linux-image-2.6.27-9-generic
Linux-restricted-modules-2.6.27-9-generic
Linux-restricted-modules-2.6.24-23-generic
Linux-ubuntu-modules-2.6.24-23-generic
Linux-image-generic
Linux-restricted-modules-generic
Linux-generic


I am completely lost now.  help?:(

---

