---
title: "How to find  files on a floppy drive"
date: 2005-12-30
forum: Desktop Environments
---

### Post by Sef on 2005-12-30
I have some stuff on a floppy drive that I want to open, but how do  I find them?  There doesn't seem to be a way to access the floppy.

---

### Post by DaMasta on 2005-12-30
Did you mount the floppy?

---

### Post by sbasak on 2005-12-30
During mounting, keep the actual floppy in the drive.

sudo mkdir /media/floppy
sudo mount /dev/fd0 /media/floppy -t vfat -o umask=000

---

### Post by Sef on 2006-01-02
How do you unmount, I try and follow the directions, but I can't unmount.

Directions: umount: only root can unmount /dev/fd0 from /media/floppy0

---

### Post by GeneralZod on 2006-01-02
[QUOTE=Sef]How do you unmount, I try and follow the directions, but I can't unmount.

Directions: umount: only root can unmount /dev/fd0 from /media/floppy0[/QUOTE]

Did you use sudo?

---

### Post by Sef on 2006-01-02
I tried that.   Should I type it like this:  

sudo unmount /dev/fd0 from /media/floppy0

---

### Post by GeneralZod on 2006-01-02
[QUOTE=Sef]I tried that.   Should I type it like this:  

sudo unmount /dev/fd0 from /media/floppy0[/QUOTE]


```

sudo umount /dev/fd0

```

should do the trick, I think.

---

### Post by Sef on 2006-01-02
Yes, that did the trick.  Thank you.

---

### Post by rjay3 on 2006-01-02
[QUOTE=sbasak]During mounting, keep the actual floppy in the drive.

sudo mkdir /media/floppy
sudo mount /dev/fd0 /media/floppy -t vfat -o umask=000[/QUOTE]

Hi, would this instructions apply to importing .csv files to my Thunderbird address book? I tried the first line but got this:
mkdir: cannot create directory `/media/floppy': File exists

I was going to try the second line but not sure what "-t vfat -o umask=000" is. Could you please explain? Is there somewhere/place I could go to learn the command lines? Appreciate it very much...........

---

### Post by rjay3 on 2006-01-03
Never mind, I got it figured out............ I found the floppy mounted on my desktop, opened it, found my files, imported files to Thunderbird. Unmounting is simply right-click floppy icon and click on 'unmount'. :-\"

---

### Post by Sef on 2006-01-03
I tried to unmount it with a left click (for me), but it didn't work.  Said I didn't have permission (yet I am the only one on here.)

Question:  How could I write a script, so I could do this automatically?  (Clear and simple directions, please, as I have never written one.)

---

### Post by Sef on 2006-01-04
There is a bug in Breezy, so often the floppies won't automount.  To get them to automount, go to this site:

[http://archive.ubuntu.com/ubuntu/pool/main/p/pmount/]("http://archive.ubuntu.com/ubuntu/pool/main/p/pmount/")

1) Download pmount_0.9.6-1~breezy1_i386.deb

2) Install -->  sudo dpkg -i pmount_0.9.6-1~breezy1_i386.deb

3) enter password

4) After it finishes installing, your floppy should mount and umount automatically.

I found that bug and fix from this thread:  [http://ubuntuforums.org/showthread.php?t=93139&page=2]("http://ubuntuforums.org/showthread.php?t=93139&page=2")

---

