---
title: "KDE screensaver not working"
date: 2006-06-13
forum: Desktop Environments
---

### Post by tokyo on 2006-06-13
hey all, i recently installed KDE 3.5.2 onto my Ubuntu 6.06 install.  quick question: why don't the screensavers work?

the 'blank screen' screensaver is the only one that actually does its job.  if you set it to any of the other ones, it simply makes the screen freeze after the given duration (i set it at 1 minute for testing purposes) and the screen refreshes back to normal after any mouse movement.

did i forget something important when i was installing KDE?  any help would be greatly appreciated.

cheers.

---

### Post by Pellaeon on 2006-06-13
I have the same problem. Recently i've updated KDE to 3.5.3 (IIRC), and screensavers ceased to work. Anyone know what i've messed?

---

### Post by Castar on 2006-06-14
I have the other problem: the screensavers never start after the set 5min period... :confused: 

any workarounds?

---

### Post by arizonagroovejet on 2006-06-14
There is a screensaver bug in KDE 3.5.3 and I guess may be in 3.5.2 as well. See

[http://bugs.kde.org/show_bug.cgi?id=128610](http://bugs.kde.org/show_bug.cgi?id=128610)

for details. The bug is apparently now resolved and the fix incorporated in to the latest KDE code. I guess at some point new KDE packages will produced for Ubuntu that include that fix, though it may be that the fix will not be in a release version of KDE until 3.5.4 comes out.

I think currently the only way to get the fix is to install KDE from the very latest source snapshot. Which I for one am not going to attempt!

---

### Post by arizonagroovejet on 2006-06-18
[QUOTE=arizonagroovejet]
I think currently the only way to get the fix is to install KDE from the very latest source snapshot. Which I for one am not going to attempt![/QUOTE]


Yeah, so I change my mind

[http://www.ubuntuforums.org/showthread.php?t=199381](http://www.ubuntuforums.org/showthread.php?t=199381)

---

### Post by wpshooter on 2006-06-18
[QUOTE=Castar]I have the other problem: the screensavers never start after the set 5min period... :confused: 

any workarounds?[/QUOTE]

Just to let you know that from my experience in **Gnome** there is also some strange relationship between the working of the power management (for monitor) and the screen saver function that I am not used to (at least in my past experience with M/S windows).  In windows the monitor power saving function and the screen functions were two completely independent working functions.  But it appears to me that in Ubuntu that these two functions are **tied together** in their functioning.

I my experience with Gnome, you have to enable both of these functions, then let them operate and then turn them each off and on in the proper sequence in order to get the desired results.  Like in my case, I do not want a screensaver function, so I have to get them both operating, say screensaver 2 minutes and power saving 3 minutes, then preferably restart/reboot and then turn off the screen saver and leave the power management on to blank my screen in so many minutes.

It looks like to me that they still need to do some work on these.

Good luck.

---

