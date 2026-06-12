---
title: "Help! Urgent! Tried to reformet 2nd HD, Now Grub won't Load. Error 15"
date: 2009-02-12
forum: General Help
---

### Post by utherpendragonfly on 2009-02-12
Well, I really screwed this up! Tried to reformat 2nd internal HD using GParted.  But when I mounted the 2 partitions, file inside both was "Lost & Found" and I don't have permission to do anything. So I restarted, and now I get:
:
Grub Loading Stage 1.5.

Grub Loading, please wait.... 
Error 15

I had Linux Mint on the 2nd HD and that was the first boot option, then Ubuntu Intrepid. I thought if Mint was gone it would revert to Ubuntu grub loader, but apparently not.
Please help!

---

### Post by dcstar on 2009-02-12
> **utherpendragonfly said:**
> Well, I really screwed this up! Tried to reformat 2nd internal HD using GParted.  But when I mounted the 2 partitions, file inside both was "Lost & Found" and I don't have permission to do anything. So I restarted, and now I get:
:
Grub Loading Stage 1.5.

Grub Loading, please wait.... 
Error 15

I had Linux Mint on the 2nd HD and that was the first boot option, then Ubuntu Intrepid. I thought if Mint was gone it would revert to Ubuntu grub loader, but apparently not.
Please help!

Do a forum search for restoring grub, there will be posts with detailed instructions on how to get back up.

---

### Post by utherpendragonfly on 2009-02-12
Thank you!

---

### Post by caljohnsmith on 2009-02-12
How about trying this from your Live CD in a terminal:
```
sudo grub
grub> find /boot/grub/stage1
```
The command above should return your main Ubuntu partition in the form of (hdX,Y) where X and Y are numbers, for example (hd0,2), but use whatever it returns as follows:
```

grub> root (hdX,Y)
grub> setup (hdX)
grub> quit
```
Then if you reboot, if all goes well you should at least get the Grub menu. If you are using Intrepid, you should be able to boot Ubuntu, but if you are using a previous version, it is likely you will need to tweak your menu.lst. Let me know how far you get, and we can work from there if you want.

---

