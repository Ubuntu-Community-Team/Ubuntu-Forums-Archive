---
title: "noob question about permissions"
date: 2005-11-30
forum: Desktop Environments
---

### Post by bananaman on 2005-11-30
hi... now before anyone flames me, i already tried googling it and searched the forums...didnt find a satisfactory answer...

just to get things clear: im a super noob but i really want to make the switch...tried before with mandrake and gave up... giving it a second try with ubuntu which seems much better...

i need help with this:
ubuntu auto mounts my windows ntfs partition... but i cant access it, i dont want to write to it, just access my mp3s and other files... i cant access it because i as user dont have permission... i want to know how to permanently change permissions so that the windows partition (hda1) can be accessed from gnome so i can run the files here...

please...help...im desperate...
i know how simple the answer must be to most of you...but please bear with me...

---

### Post by taurus on 2005-11-30
You can change the permission of your Windows' partition in /etc/fstab.  Look for an entry for your /dev/hda1 and add "umask=000" to it...  If not sure, post your /etc/fstab and either I or somebody else will help you with it.

---

### Post by bananaman on 2005-11-30
well um... i dont wanna risk it so here is my fstab...thank you very much for your help


# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1       /media/hda1     ntfs    defaults        0       0
/dev/hda3       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0


after editing it should i restart?

---

### Post by taurus on 2005-11-30
Okay, replace /dev/hda1 with this line then,

sudo gedit /etc/fstab
/dev/hda1 /media/hda1 ntfs defaults,umask=000 0 0

Reboot and see if you, a regular user, can access your windows stuff...

---

### Post by bananaman on 2005-11-30
it didnt work...
when ubuntu was loading it said

Mounting Local Filesystems...      failed

and then it wasnt available...i undid the editing and its mounted again...but no access  :(

any clues?

---

### Post by taurus on 2005-11-30
Try this...

sudo mkdir /mnt/windows
sudo gedit /etc/fstab
(Now, put a # in front of /dev/hda1 that already in there and create a new one below it as)
#/dev/hda1 /media/hda1 ntfs defaults 0 0
/dev/hda1   /mnt/windows   ntfs   defaults,umask=000   0   0

Save it and reboot...

---

### Post by bb002 on 2005-11-30
try this this line in fstab.
```
/dev/hda1 /media/hda1 ntfs nls=utf8,umask=0222 0 0
```

then to make the changes take affect without a reboot:
```

sudo umount /media/hda1
sudo mount /media/hda1

```

I pulled this info from [www.ubuntuguide.org](www.ubuntuguide.org).

---

### Post by bananaman on 2005-11-30
it worked taurus! i can access the drive in the /mnt/windows folder...
but now the drive doesnt appear on my desktop...is that normal?

---

### Post by taurus on 2005-11-30
[QUOTE=bananaman]it worked taurus! i can access the drive in the /mnt/windows folder...
but now the drive doesnt appear on my desktop...is that normal?[/QUOTE]
The reason it doesn't appear on your desktop because it was mounted on /mnt/windows, not /media...  You can create an icon on your desktop if you wish or you can use rox to browse it.  ;)

---

### Post by bb002 on 2005-11-30
Yeah that's normal. Any drive that is mounted in the /media directory gets placed on the desktop. Now that your drive is mounted in /mnt it won't show on the desktop.

---

### Post by bananaman on 2005-11-30
thank you very much taurus, you to bb002... youve been great help... now i need to figure out why the mp3s wont play ;) but ill get someone else to help me hehe...thanks again! cheers!

---

### Post by tonysathre on 2005-11-30
create a launcher with /mnt/windows as the location...i think that will work, unless  they mean by it wont show no matter what, but it should work

---

### Post by taurus on 2005-11-30
Okay, may as well work on this too.  Which media are you using to play your mp3s?  Personally, I like xmms and in fact, I have xmms playing Emma Shapplin's right now...  :)

---

### Post by bb002 on 2005-11-30
Ubuntu doesn't install mp3 support by default.

Follow the instructions at [http://www.ubuntuguide.org/#codecs](http://www.ubuntuguide.org/#codecs). But on step 2 when you add the extra repositories change all instances of hoary to breezy. That should fix you up.


[edit]
taurus has a point. I assumed you were using rhythmbox which is what I use.

---

### Post by bananaman on 2005-11-30
thanks a lot to both of you...
yes i just read about mp3 support not present in ubuntu...i already enable the repositories and installed the appropriate libraries...thanks again to both of you...thank you

---

