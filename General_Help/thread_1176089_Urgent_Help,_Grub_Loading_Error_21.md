---
title: "Urgent Help, Grub Loading Error 21"
date: 2009-06-01
forum: General Help
---

### Post by ubna on 2009-06-01
let's cut to the chase, I had windows xp professional installed on my computer, and was going for the ubuntu dual boot. I had put ubuntu on the disk and printed out a guide on how to install windows xp with ubuntu dual boot. I installed ubuntu fine, and after it was done it asked to restart my computer, so I restarted it and it came up with grub loading error 21. 
Greatly appreciated if you could help me fix this problem! :popcorn:.

---

### Post by QIII on 2009-06-02
I've never had to use it, but I've often seen Super Grub Disk recommended.

I just checked, and unfortunately their website is down for maintenance.

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

---

### Post by lindsay7 on 2009-06-02
I am not clear on what you did. Did you start with a clean disk and install Ubuntu first and then install Windows?  Was windows on the disk and then did you install Ubuntu. Fill in the blanks for us.

Also, post the results of typing

Sudo fdisk -l in the terminal, that is a small letter l not the number 1.

---

### Post by ubna on 2009-06-02
> **lindsay7 said:**
> I am not clear on what you did. Did you start with a clean disk and install Ubuntu first and then install Windows?  Was windows on the disk and then did you install Ubuntu. Fill in the blanks for us.

Also, post the results of typing

Sudo fdisk -l in the terminal, that is a small letter l not the number 1.

I installed windows and then ubuntu, windows was on my computer already if that's what you mean, and yes it was a clean disk.

---

### Post by lindsay7 on 2009-06-02
That grub error would indicate the system not finding the correct drive.

Without more info it is just a guess on my part, but one thing to check would be to see if your bios is set to start with the correct disk if you have two or more disks. Or it could be a problem with the mbr on the disk.

Anyway, the way to start to find out what is going on is for you to 

 post the results of typing

Sudo fdisk -l in the terminal, that is a small letter l not the number 1.

---

### Post by gforster on 2009-06-02
What was your installation media? Was it an external (usb) drive? Or was it a CD? Error 21 seems to mean that grub was moved to a different drive than it was expected to be on. If I am understanding your post correctly, you need to reinstall GRUB. you can do so from the Super Grub Disk as mentioned previously. I would recommend starting with the
```
GRUB => MBR & !LINUX! (1)         AUTO     ;-)
```option first.

---

### Post by ubna on 2009-06-03
It's on a portable hard-drive, I will post my boot order when I get home, at school right now, and i'm just wondering if you can delete my ubuntu and windows xp professional and start fresh again.

---

### Post by Teutorix on 2009-06-03
make sure that usb is before HDD on the boot list

---

### Post by ubna on 2009-06-03
I was also wondering, instead of posting all of the things wrong, I can talk to one of you on the phone, I will make the call not you, and you can just private message me your phone number.

---

