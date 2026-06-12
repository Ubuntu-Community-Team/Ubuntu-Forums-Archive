---
title: "disapperaing panel buttons/functions"
date: 2010-12-22
forum: Desktop Environments
---

### Post by MakOwner on 2010-12-22
I incorrectly posted this in the wrong forum originally.
[http://ubuntuforums.org/showthread.php?p=10267327#post10267327](http://ubuntuforums.org/showthread.php?p=10267327#post10267327)


This issue happens fairly frequently on 10.04 LTS Lucid Lynx.
I have no idea how or where to report this as a bug, and while I have searched looking for other posts with the same issue, I really have no idea what to search for....

I'm on a Thinkpad and the icon in the Gnome panel for powering off the laptop some times just goes away, or doesn't appear after a boot.
I occasionally also see things like the speaker volume control appear twice, replacing the panel applet next to it.

This is just annoying as hell, but I have no idea what or where to report this. Does this happen to anyone else?
I have some screenshots just to prove I'm not as crazy as I feel and I can attach them to the post later today, or you can see them in the original post I put in the wrong forum... 


](*,)

---

### Post by karthick87 on 2010-12-22
Try refreshing your panel icons..
```
killall gnome-panel
```

---

### Post by movieman on 2010-12-22
I have similar problems at times. Lately a couple of the applets have started randomly crashing at startup too.

---

### Post by Zero2Nine on 2011-01-17
Same problem here. I could start my own thread but I can't supply more information, only confirm these issues. I know about the killall command, a convenient short-term fix but no real solution.

The weather applet is sometimes shown half even at startup. killall fixes this but what frustrates me the most is that I can't explain why things go wrong. It just seems to happen randomly.

---

### Post by Jeff Gu on 2011-01-18
I've had these issues with the last couple of releases of Ubuntu... sometimes it's the network connection applet that disappears (sometimes adding the Notification Area back to the panel brings it back, but most times it's gone for good). Other times, it's the speaker volume, the email icon, log on/off (session) icon...

Very strange stuff. And, very common, it seems. Have seen so very many complaints about this and have yet to hear of a solution or an explanation of why it happens.

---

### Post by Zero2Nine on 2011-01-18
This seems to be the 'official' bug report: [https://bugs.launchpad.net/gnome-panel/+bug/44082](https://bugs.launchpad.net/gnome-panel/+bug/44082) Filed in 2006 but still not solved.

> 
Thank you for bringing this bug to our attention.
 - We missed this for Maverick. Natty will use Unity for the desktop as well, and gnome-panel will not be used.
**Also no one knows what is causing the bug.**


:(

---

### Post by Frogs Hair on 2011-01-18
Restore panel to defaults.```
gconftool --recursive-unset /apps/panel && killall gnome-panel
```

---

### Post by MakOwner on 2011-01-20
Anyone know how to search to see if a bug report has been filed?
It's getting pretty damn ridiculous restarting critical functions of my desktop in order to shut it down.

---

### Post by Krytarik on 2011-01-21
> **MakOwner said:**
> Anyone know how to search to see if a bug report has been filed?Have you checked those in post #6?
> **MakOwner said:**
> 
It's getting pretty damn ridiculous restarting critical functions of my desktop in order to shut it down.Though it's still just a workaround, but if you remove the "Indicator Applet Session" from the panel, normal logout/shutdown menu items appear in the "System" menu.

---

### Post by MakOwner on 2011-01-21
> **Krytarik said:**
> Have you checked those in post #6?
And there is the proof I'm mostly an idiot.  Not only did I not fully review the thread, but I have no idea how/where to look up bug reports. :redface: 


> Though it's still just a workaround, but if you remove the "Indicator Applet Session" from the panel, normal logout/shutdown menu items appear in the "System" menu.

I have been reduced to creating a shortcut on the desktop that does the killall thing.

Side Note: Slow death would be nice for the asshats with that launchpad login security crap.  I have been able to wade through the crap for a login at least once before using my email address, but can't remember the password.  the recover password function never sends the information needed to recover/change the password and I can't set up a new account because the email address is already in use.

---

### Post by Krytarik on 2011-01-21
> **MakOwner said:**
> 
Side Note: Slow death would be nice for the asshats with that launchpad login security crap.  I have been able to wade through the crap for a login at least once before using my email address, but can't remember the password.  the recover password function never sends the information needed to recover/change the password and I can't set up a new account because the email address is already in use.
Oh, that's just great, I know this from Paypal.

---

### Post by Tigger17E on 2011-01-23
> **Frogs Hair said:**
> Restore panel to defaults.```
gconftool --recursive-unset /apps/panel && killall gnome-panel
```

This has done the trick for me, at least it offers some means of panel restoration,which is better than nothing.

Thank you :D

---

