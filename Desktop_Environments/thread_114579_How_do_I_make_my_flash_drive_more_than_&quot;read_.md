---
title: "How do I make my flash drive more than &quot;read only?&quot;"
date: 2006-01-08
forum: Desktop Environments
---

### Post by firemedic1965 on 2006-01-08
I guess this is a Gnome issue, or maybe Linux in general...

My flash drive is viewed by Gnome/Linux as "read-only." I'd like to be able to write to it like I can with Windows and Mac. I can't figure out where to change this option.

Anyone solve this problem on your own box?

---

### Post by bikeboy on 2006-01-08
Do you know what filesystem it is formatted as? I'm not too good with mount options but I do know that if you have made it ntfs somehow it won't be writeable. Make sure it's fat32.

---

### Post by Ubluntu on 2006-01-08
Only thing I'm thinking is when you mount a network drive you add some commands like:
[FONT=monospace]
[/FONT]dmask=777,fmask=777

which allows you to read/write. I dono if these commands would work with a usb device but it might help you find some direction. I would have no idea how to add this to the system so it works everytime you plug a usb device in.

I would like to know because my laptop has a sony memory stick I use with my digital camera, I havn't tested it yet, but I doubt it writes

---

### Post by aysiu on 2006-01-08
Can you plug the flash drive in and then open a terminal (Applications > Accessories > Terminal) and post the output here of these commands? ```
sudo fdisk -l
df -h
cat /etc/fstab
```

---

