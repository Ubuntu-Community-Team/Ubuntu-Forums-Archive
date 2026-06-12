---
title: "Disk Auto Mount on Desktop"
date: 2007-11-03
forum: Desktop Environments
---

### Post by changcheng on 2007-11-03
Hi pros, I installed Ubuntu7.10 today, and it is cool. There is a icon on my desktop which is the mount device of my windows system. How can I get rid of this icon without umount it? I need the hard disk to auto mounted but do not want a icon on my desktop. Thank you

---

### Post by Happy_Man on 2007-11-03
Press alt-f2 and type gconf-editor. Navigate to apps/nautilus/desktop and uncheck volumes_visible. And they disappear. But they're still mounted. Yay!

---

### Post by changcheng on 2007-11-03
Thanks man!!! Just love Ubuntu Forum because of you guys!! Thank you

---

### Post by Zoltarp on 2007-12-17
> **Happy_Man said:**
> Press alt-f2 and type gconf-editor. Navigate to apps/nautilus/desktop and uncheck volumes_visible. And they disappear. But they're still mounted. Yay!


HELP!! I tried this and they did indeed disappear so I put them back as I didn't know where else to find them. Here is the problem, I continued to play and went to preferences and unchecked "show desktop" and ofcourse everything on my desktop disappeared so I quickly put the check back in the box but nothing came back. I logged off and tried to log back on but gnome was hosed and wouldn't load. What can I do?

Thanks,

Bruce

---

### Post by Happy_Man on 2007-12-17
Well, volumes are mounted in /media. So to get to them, that's where you go.

Also, what errors (if any) did it give when you tried to log back on?

---

### Post by Zoltarp on 2007-12-17
Well I have since found the mounted drive (USB disk) in media what about mapped windows shares? I have the other issue under wraps now. Here is the post to my plea earlier [http://ubuntuforums.org/showthread.php?t=643133](http://ubuntuforums.org/showthread.php?t=643133)

If I can get to and save to mounted windows shares that would be very helpful indeed. For example when downloading drivers I want to save directly to the mounted windows share but I cant seem to find a link to it when browsing for a location.  Obviously the windows share is there because it appears on my desktop, but where else is it?

Thanks,
Bruce

---

