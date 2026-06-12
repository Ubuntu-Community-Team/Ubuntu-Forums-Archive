---
title: "See the windows partition"
date: 2005-01-15
forum: Desktop Environments
---

### Post by Benko on 2005-01-15
Hi,

I'm in dual boot windows xp pro/ ubuntu
Somebody can tell me how read and Write on my NTFS windows partition ?

Thanks

---

### Post by Quest-Master on 2005-01-15
You can read, but not write from NTFS. Open up a terminal and

$ mkdir windows
$ sudo gedit /etc/fstab

Add this line at the end. 

/dev/hda1       /home/yourusernamehere/windows    ntfs    umask=0222      0       0

Replace hda1 wherever your windows is, and yourusernamehere with your Ubuntu username. Go back to the terminal, and type in:

$ mount -a

---

### Post by Benko on 2005-01-16
[QUOTE=Quest-Master]You can read, but not write from NTFS. Open up a terminal and

$ mkdir windows
$ sudo gedit /etc/fstab

Add this line at the end. 

/dev/hda1       /home/yourusernamehere/windows    ntfs    umask=0222      0       0

Replace hda1 wherever your windows is, and yourusernamehere with your Ubuntu username. Go back to the terminal, and type in:

$ mount -a[/QUOTE]
 Thanks a lot its works.

But why cannot I write on the NTFS partition ?

---

### Post by ulefr01 on 2005-01-16
it ia also possible to have read and write access on a NTFS partition.
You have to install captive-ntfs
be sure you have read access to your windowsxp partition (mount as type ntfs)
execute the 'captive-install-acquire' to find the windows drivers;
the /var/lib/captive directory should have the :
ntfs.sys, fastfat.sys, cdfs.sys and ntoskrnl.exe
umount /mnt/windowsxp
mount -t captive-ntfs /dev/hda1 /mnt/windowsxp
now you have write access and you are using the windowsdrivers
please do 'umount /mnt/windowsxp' afterwards to be sure the updates are done completely before you reboot

---

### Post by coolbreeze on 2005-01-17
Oh my gosh I didn't know writing to ntfs was possible!  Are you sure files on ntfs won't get corrupted?  I must give this a try.  Right now I'm completing a huge download. Later I will try this.

---

### Post by Darrena on 2005-01-17
[QUOTE=coolbreeze]Oh my gosh I didn't know writing to ntfs was possible!  Are you sure files on ntfs won't get corrupted?  I must give this a try.  Right now I'm completing a huge download. Later I will try this.[/QUOTE]
 It works and in the past I have not seemed to have any problems and others I know who have used captive-ntfs have all had zero problems but I would backup everything important before messing with it  ;)

---

