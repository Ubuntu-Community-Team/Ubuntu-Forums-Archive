---
title: "Fullscreen Totem Problem"
date: 2006-09-28
forum: Desktop Environments
---

### Post by asplode on 2006-09-28
I have this funny problem, which is one of my only irritants with totem...

When in fullscreen mode, it looks alright until the mouse is moved, and the navigation bar & leave fullscreen button appear.  They do not completely disappear.  The video only overlaps the parts of the screen that are not black... This problem also manifests itself with the volume bar popup.  I am using Totem 1.4.1 with the xine-lib version 1.1.1

See attached screenshots to see exactly what I mean.

Help?  Pretty please?

---

### Post by asplode on 2006-09-28
bump...

---

### Post by asplode on 2006-09-30
anyone got any ideas?

---

### Post by lawina on 2006-10-01
Totem does not work for me. I use VLC media player for everything including dvd, divx, avi, wmv and mp3.

---

### Post by ahaslam on 2007-05-05
I'm having the same problem In Feisty with Totem-xine. The bars don't disappear once the mouse is moved. Furthermore, [my screen enters sleep mode during playback]("http://ubuntuforums.org/showthread.php?t=393756").

These problems weren't apparent in Dapper, any ideas?

---

### Post by philmccaffrey on 2007-06-02
I have the exact same problem... very annoying! Anyone found a solution?

---

### Post by Qrome on 2008-01-03
I have the same issue.   If I play a video full screen and wait till it ends and hit escape or try to leave full screen it keeps popping back to full screen.   I run dual monitors and it happens in both monitors.   If I hit escape to leave full screen before the video is over it seems to work normally.   Very annoying!

---

### Post by tajunta on 2008-02-14
> **ahaslam said:**
> I'm having the same problem In Feisty with Totem-xine. The bars don't disappear once the mouse is moved. Furthermore, [my screen enters sleep mode during playback]("http://ubuntuforums.org/showthread.php?t=393756").

These problems weren't apparent in Dapper, any ideas?

My screen also goes to sleep mode after about 10mins of playback, and it does it with all the players I use (totem, mplayer, vlc at least). The funny thing is that I haven't got any screensavers or any power saving modes turned on at all, and it still goes blank. 

I have tried to find out if the cause of this is in bios but no avail. I just cannot find the reason for this behaviour. It started with gutsy, though I bought a new laptop near the upgrade so I'm not quite sure if it started after gutsy upgrade or the new laptop.

---

### Post by ev45ive on 2008-05-23
Had the same problem..

find xorg.conf ( most likely its in : /etc/X11/xorg.conf )

and add following at the end of file :

Section "ServerFlags"
 Option "blank time" "0"
 Option "standby time" "0"
 Option "suspend time" "0"
 Option "off time" "0"
EndSection

Probably relogin or system restart is needed.

original thread:
[https://answers.launchpad.net/ubuntu/+question/10149](https://answers.launchpad.net/ubuntu/+question/10149)

CAUTION!!!: Always remember to shutdown your monitor, because after setting those options to 0 your monitor would never SHUTDOWN and therefore it may broke someday ( burn pixels ).

ps. Know how to write totem plugins? it so go to [https://answers.launchpad.net/ubuntu/+question/101](https://answers.launchpad.net/ubuntu/+question/101) and help - PLZ :)

---

### Post by saijao on 2008-05-30
Solution to this problem::

Disable Compiz/Beryl, Load Totem while totem is active Re-enable Compiz/Beryl

---

