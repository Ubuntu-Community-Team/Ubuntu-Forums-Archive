---
title: "Remove usb icon"
date: 2008-02-07
forum: Desktop Environments
---

### Post by dhanuka on 2008-02-07
Hi all

 In windows we have a task bar icon to remove usb devices (devices like pen drives ). Is there any tool in ubuntu, to get an icon like that to task bar. Then I can easily remove pen drive without using commands.

Thanks in advance
Regards
Dhanuka

---

### Post by stooshbunutu on 2008-02-07
when the Icon appears on your desktop (once plugged in) if you right-click on the option and select the "unmount volume" option then it will allow you to remove the drive after a couple of seconds.

Just so you know, it took me a while to figure this out.

Hope this helps:)

PS, how do you like my simple but effective signature

---

### Post by dhanuka on 2008-02-07
Thanks for your reply stooshbunutu. I haved disabled visible_volumes by using gconf-editor. Bcz it is disturbing me to have them on my desktop. So, any one know a tool that i can use with taskbar.

Regards
Dhanuka

---

### Post by Haus Neuerburg on 2008-02-08
yes, you could right-click on the panel (taskbar), choose "add to panel", scroll down until you find something called "mount volume" (might be called slightly different, the icon shows an old-fashioned floppy-disk) in the category "hardware and system". Add this to either your top or bottom panel and it will show all mounted volumes. Once you want to remove one, you can just click on that specific one and choose "unmount": ready to remove. You can set the icon's position by right-clicking it and choose "move" btw.
Hope that helped.
Rgds Haus

---

### Post by dhanuka on 2008-02-08
Thanks a lot Haus Neuerburg. Can I remove my hard drives from that panel? Other partitions of my hard drive are mounted as removable devices when loading ubuntu. Therefore there are lots of icons visible in my taskbar. Can i remove my hard drive partitions from the list ? Otherwise for sure I might remove my hard drive partition, instead of pen drive.

---

### Post by Haus Neuerburg on 2008-02-08
sorry dhanuka, I have no idea :confused: , maybe some one else knows?
Sunny Regards
Haus

---

### Post by nesos on 2008-02-08
> **dhanuka said:**
> Thanks a lot Haus Neuerburg. Can I remove my hard drives from that panel? Other partitions of my hard drive are mounted as removable devices when loading ubuntu. Therefore there are lots of icons visible in my taskbar. Can i remove my hard drive partitions from the list ? Otherwise for sure I might remove my hard drive partition, instead of pen drive.

Those partitions(Windows partitions?) are mounted in /media folder. I edited fstab to get rid of this.

---

