---
title: "how do i do fdisk on external hard drive?"
date: 2009-06-23
forum: General Help
---

### Post by ejames82 on 2009-06-23
every couple of weeks i experience problems with my fantom 1tb GF 100EU external hard drive.  it is only about 5 months old.  it either doesn't show up on the desktop, can't be found in "my computer", or if it is found, cannot be accessed.  sometimes i receive an error message and part of the "details" of this error message say to run a "windows checkdisk:" which i know how to do, but it takes over a day.
i have done a little research and read that the linux equivalent to checkdisk is fdisk.  lets say for instance, the external fantom is G, what would be the proper command to run fdisk on G?
thanks.

---

### Post by 67GTA on 2009-06-23
It sounds like there was an unclean shutdown or unmount. NTFS? You can force mount it, but would be better to do the checkdisk. It should mount fine afterwards. You can use gparted to do the check from Ubuntu. Install ntfsprogs and gparted. Then plug in the drive, open gparted and select the drive from the drop down menu in the top right. Right click on the partition and select check.

---

### Post by ejames82 on 2009-06-23
67GTA,

yes, it is ntfs.  
how do i force mount it?  not that i would, but it would be nice to know.

**You can use gparted to do the check from Ubuntu. **

how do i do this?  
thanks.

---

### Post by 67GTA on 2009-06-23
You can try adding "force" to the end of the mount command in a terminal. It would be something like ```
mount -t ntfs-3g /dev/disk/sdb /media/ntfs -o force
``` This asumes you would change /dev/disk/sdb to the path of your external hard drive while plugged in, and create a folder named ntfs in /media. You can name it whatever you want. If you created a directory named external ```
sudo mkdir /media/external
``` It would be ```
mount -t ntfs-3g /path_to_external_HDD /media/external -o force
``` I edited my post above with instructions on how to check NTFS with gparted before you read it:D[FONT=Courier New][/FONT]

---

### Post by bodhi.zazen on 2009-06-23
Usually you have to specify the partition.

mount /dev/sdb**[color=darkred]1**[/color]

/dev/sdb is the entire disk, which is not quite the same, and will usually fail.

You should mount the desk in windows. If you no longer use windows, consider uisng a linux native file system.

Mounting the disk with the force option can (rarely) cause data loss :(

---

### Post by ejames82 on 2009-06-24
the checkdisk started several days ago, is still running.  as soon as it finishes, i will try the suggestions provided.
thanks.

---

### Post by ejames82 on 2009-06-26
still no go.
i installed gparted with no problem, it sits on my desktop, however ntfsprogs is questionable.  according to the terminal it is installed.  it is not like gparted with a GUI, and i can't find it anywhere as a whole program, just a file exists in one of the usr directories.  
the tell-all sign is when i plug in the external drive and proceed to "check" it, the word "check" is greyed out.  i tried clicking it anyway, but it didn't do any good.
i'm gonna keep researching what i'm doing wrong.  any advice would be great, i know it's been a few days.  the checkdisk took a long time to run.  i'm lucky to have more than one computer.

---

### Post by 67GTA on 2009-06-27
Make sure the drive isn't mounted when you try to check it. Ntfsprogs is only a library file that gparted uses. Library files are like DLL's in Windows.

---

### Post by ejames82 on 2009-06-27
67GTA,

i tried using ntfsprogs via command line while the 1tb was mounted:

sudo ntfsfix /dev/sdf1

i received some kind of error message that could not work on read-write device while mounted.


then i unmounted and ran the same command.  i received a message that the process was completed successfully.
does this mean ntfsprogs checked the disk?  what does this process actually consist of?  what does it do?  if i have the problems with it not showing up where it's supposed to be or not being able to access it?  is this fixing it?
thanks once again for the expertise.

---

### Post by 67GTA on 2009-06-27
Ntfsfix was made to fix errors on NTFS file systems. It is kind of like chdisk. Here is the man page for ntfsfix: [http://man.linux-ntfs.org/ntfsfix.8.html](http://man.linux-ntfs.org/ntfsfix.8.html)

If you are able to mount it now, then it is fixed.

---

### Post by ejames82 on 2009-06-27
67GTA,

yep, it's fixed, plus i have some new information that i have yet to dissolve.  these things usually come in bits and pieces before i fully understand them, but this fix came relatively easy.  bottom line is, it is very important to "unmount" and "remove hardward properly".  by just unplugging the device from the usb port can cause days of repair.
thanks for the help.

---

### Post by 67GTA on 2009-06-27
> it is very important to "unmount" and "remove hardward properly". by just unplugging the device from the usb port can cause days of repair.

I'm 99.9% sure this is what happened to you. NTFS can't handle an "unclean" shutdown and develops file system errors. Glad you got it working.

---

### Post by bodhi.zazen on 2009-06-27
And the other problem with ntfs - there really are not very good Linux tools to fix the problem, so if you use ntfs you will almost certainly need access to Windows from time to time.

---

