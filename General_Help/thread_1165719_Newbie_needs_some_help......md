---
title: "Newbie needs some help....."
date: 2009-05-20
forum: General Help
---

### Post by RazzyDaz on 2009-05-20
I am trying to install a second HD from an existing windows computer.  I recently installed 9.4 on another HD, amd I'm looking to install/mount the second HD as an extra space for music, pictures, etc.  The said HD jumpers are set to slave, since it was used only for my music and picture files on previous XP computer.  I DO NOT WANT TO FORMAT THE DRIVE, or else I will lose all my music and pictures.  Is there a way to automount second HD w/out formating or partitioning?      

Thanks for helping the newbie......:D

---

### Post by venator260 on 2009-05-20
Install the hard drive into the computer. 

Then follow the instructions [Here]("http://www.psychocats.net/ubuntu/mountwindows") for a graphical way to mount the drive, or [Here]("http://www.psychocats.net/ubuntu/mountwindowsfstab") to learn about how to edit your /etc/fstab file (this is the method that I prefer).

---

### Post by zeroseven0183 on 2009-05-20
What is the file system format of the second hard drive? If it's NTFS, you can use **NTFS Configuration Tool** to automatically mount the drive with read-write access to it.

Install it from **Add/Remove...**

---

### Post by colau on 2009-05-20
> **venator260 said:**
> Install the hard drive into the computer. 

Then follow the instructions [Here]("http://www.psychocats.net/ubuntu/mountwindows") for a graphical way to mount the drive, or [Here]("http://www.psychocats.net/ubuntu/mountwindowsfstab") to learn about how to edit your /etc/fstab file (this is the method that I prefer).
Nice link venator260.

---

### Post by RazzyDaz on 2009-05-20
Thanks, the second option seems a little easier.  It will not format or erase my data, will it?  I'm going to install the HD tomorrow, so I'll let you know how it goes.  Again, thanks for the help.

---

### Post by RazzyDaz on 2009-05-20
> **zeroseven0183 said:**
> What is the file system format of the second hard drive? If it's NTFS, you can use **NTFS Configuration Tool** to automatically mount the drive with read-write access to it.

Install it from **Add/Remove...**

It is NTFS, so is this easier to do, than the suggested links?  I just want to make simple as possible and be sure my HD doesn't get erased.

---

