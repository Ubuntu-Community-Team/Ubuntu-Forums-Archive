---
title: "Probles using floppy with gui"
date: 2006-07-19
forum: Desktop Environments
---

### Post by tgrzejsz on 2006-07-19
Hello,
I have a problem with conveniently accessing floppy using krusader or konqueror. After selecting a floppy drive in media listing it gets mounted but gui hangs forever and doesn't display any content. I have to manually navigate to directory /media/floppy.
I wonder if the problem is somehow connected with naming. When typing media path for floppy, the name "media:/fd0" gets hinted and my floppy is mounted to directory "/media/floppy0". But I don't know if it is significant. Maybe changing mount point to /media/fd0 would help? I'll try it when I get home.

Greetings,
Tomek

---

### Post by Sef on 2006-07-21
Here's how I got mine floppy to work.

From a previous post:

> 1) Open Terminal (Konsole in KDE)

2) sudo gedit (Kate in KDE) /etc/fstab

3a) Go to the floppy module (on the bottom in gedit)

Code:

/dev/fd0 /media/floppy0 auto rw,user,noauto 0 0


3b) Change auto to vfat

Code:

/dev/fd0 /media/floppy0 vfat rw,user,noauto 0 0

4) To open the floppy, go to Places > Computer > click on the floppy (Not sure what it is called in KDE.)

5) Click on the floppy pic

6a) Floppy drive will mount

6b) You can read your floppy documents

6b) To unmount, right click on the floppy and highlight unmount

[Floppy]("http://ubuntuforums.org/showthread.php?t=181436&highlight=Floppy")

---

### Post by tgrzejsz on 2006-07-22
> **Sef said:**
> Here's how I got mine floppy to work.
...

Thanks for the answer. My configuration is identical with the mentioned one. I've checked it and it works in nautilus. But it doesn't in konqueror and neither in krusader. And I use KDE, so the problem persists. Maybe I should file a bug report.

Tomek

---

