---
title: "Installer demanding that I kill my partition."
date: 2009-05-01
forum: General Help
---

### Post by infinitelink on 2009-05-01
"You assigned a separate file system to /[directory], but in order for the system to start correctly this directory must be on the root file system."

is the message I get when trying to install. I have three primaries, the first just one from the computer OEM (not the problem the installer is complaining about), then 

/dev/sda2 

which has 
/dev/sda5 linux-swap
/dev/sda6 /ext3 /boot
/dev/sda7 /ext4 / 
/dev/sda8 /ext4 /home

and 

/dev/sda3

which complete in itself as a primary (/ext4 /media). I had the previous version of Kubuntu on here (now wiped to install fresh), and I'm not wiping /media since it has a bunch of files. So far both the Kubuntu and Xubuntu liveCDs have given me this message.

Solutions anyone?

---

### Post by KhurramM on 2009-05-01
I suspect that /boot needs to be on ext4 as well.

I hope this resolves the issue.

---

### Post by infinitelink on 2009-05-01
oops...

Okay, a detail I missed, /[detail] is /media. It's the /media partition it's demaning that I destroy. : (

This is one I've never seen.

---

### Post by cariboo on 2009-05-01
I would suggest you just ignore your /media directory. Just leave it as it is, you don't need to set a lable for it. I would also suggest that you don't need a seperate /boot partition, as grub has been patched to boot from ext4.

---

### Post by infinitelink on 2009-05-01
Well the boot idea was just to give it some space, but good to know! : D

Okay, so when I get this installed, now the real philosophical question.:lolflag:..what's the diff between mtab and fstab? :confused:

---

