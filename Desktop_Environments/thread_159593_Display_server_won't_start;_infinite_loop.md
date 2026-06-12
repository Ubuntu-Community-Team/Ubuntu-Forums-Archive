---
title: "Display server won't start; infinite loop"
date: 2006-04-13
forum: Desktop Environments
---

### Post by qyot27 on 2006-04-13
Recently, to try to get a particular [GNOME panel applet](http://gnomefiles.org/app.php?soft_id=745) to display, I figured I needed GTK+ 2.6.x since the 2.8.x that I had wouldn't allow it to show up, even though the applet was able to index my bookmarks just fine.  When looking on the GTK+ website, there was a footnote about earlier versions being able to be installed alongside each other, so taking that in mind (mistakenly, I guess, but I didn't find any disclaimer about it on there), I tried to install GTK+ 2.6.  Of course, I had to start with the dependencies since trying to compile GTK+ 2.6 straight out would fail.

Glib-2.6.6 compiled and installed fine, but when I tried to install pango or atk (not sure which, as this was like two weeks ago) it wouldn't, saying that the version of Glib was incorrect.  So eventually I just gave up on the idea and decided to move on.  I figured I needed to remove Glib-2.6.6 but I couldn't find it.  When I shut down the computer that night, I didn't see the normal verbose dialog telling me the processes were stopping, and then it just shut off.

The next time I booted into Ubuntu, it worked fine, I updated the version I had of wine, and then tried to go download the deb package of FrostWire from Sourceforge.  Firefox chokes, everything, in fact, chokes, I was forced to shut down, and now when I try to boot into Ubuntu, I see the waiting icon appear, the screen kicks over a few times continually trying to start the display server, and then I get an error message telling me that it's tried to start so many times in 2 minutes and it'll try again after another few minutes.  If I manage to get back to the command prompt it goes alright and I can at least tell the computer to shut down so I can boot my XP partition instead.

I'm figuring that this is a problem arising from Glib-2.6.6, but what would be the course of action to fix it?

Thanks in advance.

---

### Post by oscar on 2006-04-13
If I read your post right the only thing you installed was glib so you are right that this is probably what broke it. To reinstall the ubuntu package:
Hit Ctrl+Alt+F1 to get to a terminal window. Login and.
```
sudo apt-get --reinstall install libglib2.0-0
```
I think that will work but it might not be the only package that needs to be reinstalled.
You could restart but I think hitting Ctrl+Alt+F7 will get you back to what is normally the graphical "mode" and the gdm will start again as it keeps on trying. If it has stopped trying:
```
sudo /etc/init.d/gdm start
```
should start it.

If reinstalling libglib2.0-0 doesn't work other packages might need the same treatment:
```
 sudo apt-cache search glib
```
Should list packages that mention glib, pick suitable ones to try reinstalling.

---

### Post by qyot27 on 2006-04-14
No, it didn't work, even after reinstalling glib and pango.  It kept saying that things were already associated to other points in the system (which I have no clue what that means) whenever I typed in 'startx'.  Restarting and trying to go in again still exhibits the problems from the first post.

I'm thinking that maybe I should index what I've set my configuration for and the programs I've installed and just completely wipe the partition and start over.  Either that or hope that maybe upgrading to Dapper in June will fix the problems.

Is there any specific log file I should look at or post on here that might be able to show what the problem is?

---

### Post by oscar on 2006-04-14
It is the gdm that isn't starting right?
/var/log/gdm/\:0.log could contain something
as could
/var/log/Xorg.0.log
Not so sure about the Xorg log

Starting over always fixes the problem and I enjoy a clean pc but it is annoying getting all the settings and apps the same as they were before.

---

### Post by qyot27 on 2006-04-15
Well, I managed to get the logs.  The errors seem to be uniform for both.

:0.log
```

X Window System Version 6.8.2 (Ubuntu 6.8.2-77 20051010174523 root@vernadsky.buildd)
Release Date: 9 February 2005
X Protocol Version 11, Revision 0, Release 6.8.2
Build Operating System: Linux 2.6.10 i686 [ELF] 
Current Operating System: Linux ubuntu 2.6.12-10-686 #1 Sat Mar 11 16:22:51 UTC 2006 i686
Build Date: 10 October 2005
	Before reporting problems, check http://wiki.X.Org
	to make sure that you have the latest version.
Module Loader present
OS Kernel: Linux version 2.6.12-10-686 (buildd@terranova) (gcc version 3.4.5 20050809 (prerelease) (Ubuntu 3.4.4-6ubuntu8.1)) #1 Sat Mar 11 16:22:51 UTC 2006 
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Fri Apr 14 09:09:00 2006
(==) Using config file: "/etc/X11/xorg.conf"
Skipping "/usr/X11R6/lib/modules/extensions/libGLcore.a:m_debug_clip.o":  No symbols found
Skipping "/usr/X11R6/lib/modules/extensions/libGLcore.a:m_debug_norm.o":  No symbols found
Skipping "/usr/X11R6/lib/modules/extensions/libGLcore.a:m_debug_xform.o":  No symbols found
Skipping "/usr/X11R6/lib/modules/libfb.a:fbmmx.o":  No symbols found
Warning: font renderer for ".pcf" already registered at priority 0
Warning: font renderer for ".pcf.Z" already registered at priority 0
Warning: font renderer for ".pcf.gz" already registered at priority 0
Warning: font renderer for ".snf" already registered at priority 0
Warning: font renderer for ".snf.Z" already registered at priority 0
Warning: font renderer for ".snf.gz" already registered at priority 0
Warning: font renderer for ".bdf" already registered at priority 0
Warning: font renderer for ".bdf.Z" already registered at priority 0
Warning: font renderer for ".bdf.gz" already registered at priority 0
Warning: font renderer for ".pmf" already registered at priority 0
```

---

