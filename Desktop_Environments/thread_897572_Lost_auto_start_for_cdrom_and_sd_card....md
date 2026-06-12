---
title: "Lost auto start for cdrom and sd card..."
date: 2008-08-22
forum: Desktop Environments
---

### Post by neocortex on 2008-08-22
Hello all,
I am using latest (and the greatest) Ubuntu 8.04 on my ThinkPad T61. After a few update I lost automatic start of Nautilus, when I insert cd/dvd or sd card. They seem to be mounted, because when I open Places and click on the icon, Nautilus eventually shows their content. But automatic open function, which was present upon installation and in all previous versions of Ubuntu, does not work.
Please, help me!

Best,
PM

---

### Post by bmac on 2008-08-22
I believe this will help....

[http://ubuntuforums.org/showthread.php?t=897714](http://ubuntuforums.org/showthread.php?t=897714)

---

### Post by neocortex on 2008-08-24
Unfortunately, it did not helped. I checked Configuration Editor, and everything was properly checked. I still do not have automount as before.

Any other idea?

Best,
PM

---

### Post by bmac on 2008-08-24
I apologize - after re-reading your post it appears your problem was auto start of nautilus when inserting a cd/sd. 

Open Nautilus:
edit/preferences/media tab

select option for each activity


Hope this helps......

---

### Post by neocortex on 2008-08-28
Unfortunately, still no luck! Interestingly, usb does autostart, but cd and sd not. Any new ideas?

Best,
PM

---

### Post by bmac on 2008-08-28
Just one possible:

In your Nautilus file browser:
edit/preferences/media tab
Is the Browse media when inserted box checked?

Hopefully, if that isn't the problem, someone will have some other ideas....

---

### Post by neocortex on 2008-08-30
Yes, the Browse media when inserted box is checked. And Media Handling is set to Open Folder. I really do not know what is going on. Moreover, usb is doing fine; just cd/dvd and sd are silent after inserting. This never happened in my older versions of Ubuntu and i thing I have it since 6.06 or so.

Best,
PM

---

### Post by bmac on 2008-08-30
DVD / CD will be silent if you select "Open Folder" and not an application.
For example on the nautilus/edit/preferences/media tab:
cd Audio - Open Rhythmbox Music Player or some alternative if you want your audio to start on insertion. Same with DVD Video: Open Movie Player
Open folder would only display your contents in Nautilus...

---

### Post by neocortex on 2008-09-02
That is exactly what I would like, but it does not make anything...
Please, why is this happening? Help!

PM

---

### Post by neocortex on 2008-09-07
Anyone?!? Anything?!?

PM

---

### Post by neocortex on 2008-09-18
Now, I dig deeper into this. It seems that Configuration Editor (gconftool-2) has everything checked as it should -- all automount are set to TRUE:
gconftool-2 --type bool --set /apps/nautilus/desktop/media_automount True
gconftool-2 --type bool --set /apps/nautilus/desktop/media_automount_open True
One look at fstab give me, again, nice view, since it looks fine:
# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
# /dev/sda2
UUID=9e3a090a-d71f-4370-9a0e-fff670c6e024 / ext3 relatime,errors=remount-ro 0 1
# /dev/sda3
UUID=1883818f-699e-4f2c-9d2f-a9f234c18b56 /home ext3 relatime 0 2
# /dev/sda1
UUID=BE54A5E854A5A41D /media/windows ntfs defaults,umask=007,gid=46 0 1
# /dev/sda4
UUID=6da3517c-44b3-4382-b5f7-9e2771c43368 none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0

Any idea? Is this about mounting not working on insertion? What is going on? Please, help!

Best,
PM

---

