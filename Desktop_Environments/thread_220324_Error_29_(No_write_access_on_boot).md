---
title: "Error 29 (No write access on boot)"
date: 2006-07-21
forum: Desktop Environments
---

### Post by boyfromthedwarf9 on 2006-07-21
I have a laptop that dual boots between Dapper and XP, when I try a normal boot on Dapper it says Error 29 "No Write Access" or something, and XP just blue screens.

I am currently running a in "recovery" mode, but it doesn't look like it is working.

I just updated, and I removed the extra boot options from the menu.lst, I did make a backup of the menu.lst first, but I don't think that caused the error. 

I had my normal dapper desktop up, and then things started crashing, as in when I went to click the wifi at the bottom right, it went away, same when I tried clicking either of my gnome bars, same when I tried clicking any desktop icons, then I just had my background sitting there. I left it for a minute, then I thought it might not come back, so I thought I should reboot, and then this happened.

---

### Post by boyfromthedwarf9 on 2006-07-21
I was able to fix this by booting the ununtu livecd and runing fsck, for me the syntax was sudo fsck /dev/hda3 (hda3 is my ubuntu main partition).

---

