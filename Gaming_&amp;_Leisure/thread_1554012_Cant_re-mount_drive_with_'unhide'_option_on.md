---
title: "Cant re-mount drive with 'unhide' option on"
date: 2010-08-16
forum: Gaming &amp; Leisure
---

### Post by evo9 on 2010-08-16
I'm trying to install WoW on my Ubuntu machine and I'm having trouble right off the hop. I'm using an install DVD thru wine and it says since the Installer.exe is hidden I need to remount my drive with the unhide option on.

I'm following this guide [https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft)

This is the part of the guide I'm getting stuck at

[COLOR=Olive]**Note** that on some WoW DVD's the  installer executable is hidden and you need to re-mount the disc with  the 'unhide' option. To do this type in a terminal:
  sudo umount /dev/cdrom
  sudo mount -t iso9660 -o ro,unhide /dev/cdrom /media/cdrom0/[/COLOR]

The unmount part works just fine but when I go to remount the drive it gives me this error:

[COLOR=Olive]mount: mount point /media/cdrom0/ does not exist
[/COLOR] 
I'm probably just being a complete noob and missing something obvious here, so if someone could point out what it is that would be quite helpful. Thanks!

---

### Post by evo9 on 2010-08-16
I moved this thread over the general help since my actual issue at this point has nothing to do with gaming, how can I delete the thread from this part of the forums?

---

