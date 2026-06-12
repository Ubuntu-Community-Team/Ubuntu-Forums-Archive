---
title: "Dual Boot Assistence"
date: 2007-06-10
forum: Dell  Ubuntu Support
---

### Post by Lowrie on 2007-06-10
Sorry if this question has already been asked. I briefly looked through the forums but found nothing. So if i missed something please forgive my incompetence.

To the problem at hand. I am currently attempting to dual boot by Dell inspiron 640m laptop with windows and Kubuntu. I am reading Matthew J. Miller's guide to dual booting without changing the MBR. [http://www.matthewjmiller.net/howtos/dual-boot-linux-and-windows/]("Here") is the link. Everything has worked perfectly to plan until installation step 8. 
> Now, we're going to use the Linux System Rescue CD to dual boot using Window's bootloader. Start by making a mount point for the OS Share partition:
mkdir /mnt/osshare
Then, mount the partition:
mount -t msdos /dev/hda6 /mnt/osshare
If you're not sure which device (e.g., /dev/hda6) your OS Share partition is, you can use QTParted to see the device number. Finally, we'll create a file that Windows can use to boot Linux:
dd if=/dev/hda2 of=/mnt/osshare/ubuntu.bin bs=512 count=1
Where /dev/hda2 is the device for your Linux partition (again, use QTParted to find the device number if you're unsure).
When i use the System rescue CD mount the partition i get the error that says something along the lines of "file or location does not exist". When i read that i automatically thought i had the wrong hard drives. So i when into Kubuntu's QTParted partitioning tool to see the directory files. Nothing was wrong.

Sorry for the inconvenience, any help is greatly appreciated.

---

### Post by ridgeland on 2007-06-10
I would first suspect the mount command
mount -t msdos
-t msdos means the file system type is msdos. 
Try with out the -t msdos just
mount /dev/hda6 /mnt/osshare
let mount figure out the file system type.

QTparted should show more detail of file system type and verify partition name.

The whole process seems scary to me.  I never go the dd route.

Why aren't you going the normal route of installing GRUB in the MBR and having a menu show up when you boot?  Then in boot (GRUB) you default to one OS, can choose the other, or even have the default=last used.

---

### Post by Lowrie on 2007-06-10
Thanks for the reply. I ended up installing grub. Love Kubuntu, i doubt ill uninstall it. So i don't need to keep the MBR intact

---

### Post by Dedoimedo on 2007-06-11
Hello,

If you mean MBR intact, you mean in its Windows form?

MBR is a location, and MS products like to overwrite this location any time they install themselves. GRUB is much more tolerant, it simply appends information. But even if you do happen to overwrite MBR, nothing critical will happen. You can always quickly and easily restore GRUB.

Dedoimedo

---

