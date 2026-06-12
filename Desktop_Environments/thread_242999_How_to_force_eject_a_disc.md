---
title: "How to force eject a disc?"
date: 2006-08-24
forum: Desktop Environments
---

### Post by Chrono86 on 2006-08-24
Hey guys~
Installing the game Escape from Monkey Island which supposedly works just fine in Wine. Anyways half way through the installation it asks me to put in Disc 2 but Ubuntu won't let me eject the disc, it says the device is busy. Is there a way to force eject it?
Thanks
Adam

---

### Post by sbassett on 2006-08-24
Haved you tried the console using

sudo eject /dev/hdc

Assuming that your Disc is /dev/hdc (can be found by looking at /etc/fstab)

---

### Post by Chrono86 on 2006-08-24
Tried that. It gives me:

adam@adam:~$ sudo eject /dev/hdc
umount: /media/cdrom0: device is busy
umount: /media/cdrom0: device is busy
eject: unmount of `/media/cdrom0' failed

---

### Post by steve.horsley on 2006-08-24
Try:
sudo umount -l /dev/hdc
sudo eject /dev/hdc

The -l (lower-case L) is the secret sauce.

---

### Post by Chrono86 on 2006-08-25
Alright using that command worked, I popped in disc 2, mounted it, and although opening up the cd shows the files for disc 2, ubuntu still calls it cd 1 and the installation program still thinks disc 1 is in there.

---

### Post by NESFreak on 2006-08-25
try to copy and run the installer from your harddrive. (You can only unmount a device (non forced) when there are no applications using it/running from it.

---

### Post by Rainbow_Magik on 2007-07-18
what you could try instead of copying to the hard disk.
[COLOR="Blue"]sudo umount -l /media/cdrom[/COLOR][COLOR="Red"]x[/COLOR]
mount the next disk in another drive, auto or manual.
[COLOR="Blue"]sudo mount /media/cdrom[/COLOR][COLOR="Red"]x[/COLOR]
then
[COLOR="Blue"]sudo mount --bind /media/cdrom[/COLOR][COLOR="Red"]a[/COLOR] [COLOR="Blue"]/media/cdrom[/COLOR][COLOR="Red"]b[/COLOR]
where [COLOR="Red"]a[/COLOR] and [COLOR="Red"]b[/COLOR] are numbers
and [COLOR="Red"]a[/COLOR] is the drive with the cd and [COLOR="Red"]b[/COLOR] is the one without a cd.
when you need to eject the cd from the other drive just
[COLOR="Blue"]sudo umount /media/cdrom[/COLOR][COLOR="Red"]b[/COLOR]

worked for me. if you don't have another cd drive then you could copy to your hard disk and use
[COLOR="Blue"]sudo mount --bind[/COLOR] [COLOR="SeaGreen"][cd location][/COLOR] [COLOR="Blue"]/media/cdrom[/COLOR][COLOR="Red"]b[/COLOR]
though i havnt tried that myself.

If your using wine you can use [COLOR="Blue"]wine eject[/COLOR]

---

### Post by der_joachim on 2007-07-18
[Edit]Nevermind

---

### Post by wenuswilson on 2008-05-26
> **Rainbow_Magik said:**
> what you could try instead of copying to the hard disk.
[COLOR="Blue"]sudo umount -l /media/cdrom[/COLOR][COLOR="Red"]x[/COLOR]
mount the next disk in another drive, auto or manual.
[COLOR="Blue"]sudo mount /media/cdrom[/COLOR][COLOR="Red"]x[/COLOR]
then
[COLOR="Blue"]sudo mount --bind /media/cdrom[/COLOR][COLOR="Red"]a[/COLOR] [COLOR="Blue"]/media/cdrom[/COLOR][COLOR="Red"]b[/COLOR]
where [COLOR="Red"]a[/COLOR] and [COLOR="Red"]b[/COLOR] are numbers
and [COLOR="Red"]a[/COLOR] is the drive with the cd and [COLOR="Red"]b[/COLOR] is the one without a cd.
when you need to eject the cd from the other drive just
[COLOR="Blue"]sudo umount /media/cdrom[/COLOR][COLOR="Red"]b[/COLOR]

worked for me. if you don't have another cd drive then you could copy to your hard disk and use
[COLOR="Blue"]sudo mount --bind[/COLOR] [COLOR="SeaGreen"][cd location][/COLOR] [COLOR="Blue"]/media/cdrom[/COLOR][COLOR="Red"]b[/COLOR]
though i havnt tried that myself.

If your using wine you can use [COLOR="Blue"]wine eject[/COLOR]


wine eject d: -- so gosh dang simple.

---

