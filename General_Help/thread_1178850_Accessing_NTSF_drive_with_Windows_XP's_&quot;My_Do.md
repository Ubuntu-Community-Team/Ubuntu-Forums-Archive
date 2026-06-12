---
title: "Accessing NTSF drive with Windows XP's &quot;My Documents&quot; folder"
date: 2009-06-04
forum: General Help
---

### Post by AE000 on 2009-06-04
After I installed Ubuntu I kept my old Windows XP hard disk as a slave drive with most of my files, the idea was to access it from Ubuntu and gradually copy the files I needed (documents and mp3 files).

I am able to see it from the Ubuntu menu, I can browse through the Windows' folders and eventually get to the "My Documents" folder to see these files. Anyway, to make it faster I created a shortcut to it and placed in my Ubuntu desktop and it works fine, but each time I reset the PC the link appears as broken and it only works after I've manually opened that drive from the Ubuntu menu (and it will keep working until I reboot/shutdown the PC).

Is there any other way to create this shortcut in such a way that it will continue to work after I reboot?

The properties for this hd say that its file system is ntfs-3g (3.1)

Thanks in advance!

Alex.

---

### Post by madverb on 2009-06-05
Just sounds like the drive isn't being automounted on startup.

---

### Post by sahabcse on 2009-06-05
Edit the fstab for automount the folder, then create symbolic link for short cut.

for more info follow [http://sahabm.blogspot.com/2009/03/mount-ntfs-fat32-windows-drive-in.html](http://sahabm.blogspot.com/2009/03/mount-ntfs-fat32-windows-drive-in.html)

---

### Post by AE000 on 2009-06-09
> **sahabcse said:**
> Edit the fstab for automount the folder, then create symbolic link for short cut.

for more info follow [http://sahabm.blogspot.com/2009/03/mount-ntfs-fat32-windows-drive-in.html](http://sahabm.blogspot.com/2009/03/mount-ntfs-fat32-windows-drive-in.html)

Dumb question: At the end of that procedure I need to edit the etc/fstab file but when I try to save the changes it says I don't have permission to do it but does not asks for my password.

Any help on how should I edit the file?

Thanks,

Alex.

---

### Post by sahabcse on 2009-06-09
try

sudo /etc/fstab

then give your system password...and edit the file

---

### Post by Entropy_Sam on 2009-06-09
From the gnome-terminal, use
```
gksudo gedit /etc/fstab
```
 
This will open fstab in Text Editor, with the permissions you need to save the changes.

---

### Post by AE000 on 2009-06-11
It seems that something is not working with the line I added to the /etc/stab file:

/dev/sda1 /media/disk ntfs rw,umask=0222 0 0

Because when I reset the PC I can't see it anymore (/media/windisk) appears empty.

It works fine before I restart.

Any help is appreciated.

Alex.

---

### Post by sahabcse on 2009-06-11
I think your partition has missed while you reset the system, pls verify the partition sda1 contains ntfs files. paste the o/p of fdisk -l.

---

### Post by nandemonai on 2009-06-11
> **AE000 said:**
> It seems that something is not working with the line I added to the /etc/stab file:

/dev/sda1 /media/disk ntfs rw,umask=0222 0 0

Because when I reset the PC I can't see it anymore (/media/windisk) appears empty.

It works fine before I restart.

Any help is appreciated.

Alex.

/dev/sda1 /media/**win**disk ntfs**-3g** rw,umask=0222 0 0

This is assuming that 1. You have ntfs-3g installed (which you should but can check via sudo apt-get install ntfs-3g) and 2. /dev/sda1 is the Windows partition.

---

### Post by akakingess on 2009-06-11
Everything has worked for me, but I would also like to automount just a particular folder within that drive, seperately on the desktop, is that also possible? Like I said, every piece of advice thus far has worked and my drive mounts automatically upon restart, just wondering if I could do the same for a folder within that windows mounted drive?  Thanks in advance for any info/even if it's to say not possible, or why the heck would you want to do that LOL...

akakingess

---

### Post by AE000 on 2009-06-11
> **nandemonai said:**
> /dev/sda1 /media/**win**disk ntfs**-3g** rw,umask=0222 0 0

This is assuming that 1. You have ntfs-3g installed (which you should but can check via sudo apt-get install ntfs-3g) and 2. /dev/sda1 is the Windows partition.

This did the trick, thank you very much, and of course everyone else who also helped.

Alex.

---

