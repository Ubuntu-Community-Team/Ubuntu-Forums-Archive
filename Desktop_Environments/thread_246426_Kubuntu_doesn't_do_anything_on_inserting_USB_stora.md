---
title: "Kubuntu doesn't do anything on inserting USB storage"
date: 2006-08-29
forum: Desktop Environments
---

### Post by KubuntuKilledMe on 2006-08-29
I have an 256Mb USB stick that works but not in Kubuntu. dmesg shows it is recognised and it really should be no problem as it is standard usb storage. The problem is it doesn't get mounted, doesnt show in Storage Media, and no window pops-up to ask me what i wanna do. 

Kubuntu is very good and i'm very pleased with the switch. It does need some work on making sure things dont randomly stop working like this. In that aspect, it pains me to admit, its much more flimsy than windows xp.

---

### Post by KubuntuKilledMe on 2006-08-29
bump

My original post has descended into the deep pages of the forum without a SINGLE VIEW.

A quick search shows this problem to be extremelly common as there are a lot of threads like mine without a single reply. 

Googling shows a lot of ppl with problem, many non-working solutions and essentially nobody knows anything except that KDE gave up on usb storage. The situation with the devide desktop icons and HAL is a _tragedy_ since breezy, which already had this problem. The upgrade to dapper made the breezy fixes for this problem stop working, and nobody has come up with anything that works. The very solutions presented show such inconsistency with my install (which is a default install by all means) that it would seem the ppl on this forum arent even running the same distro i am.

I knew the "LTS" added to the name was little more than a gimmick, i never tought it would be loaded with so much irony. 

I know its Linux, i know its free and Free, but for the love of god, there's more to computing than network cards!

---

### Post by anaconda on 2006-08-29
Did you try to mount it manually?
```

sudo su
mkdir /media/usbi
mount t- auto /dev/sda1 /media/usbi
```

That should do it. if your usb-stick is sda. If you have SATA disk, then your usb is propably sdb1.. eg. the last s(csi)d(isk) 

(USB:s and SATA disks are handled as "scsi" disks..)

---

### Post by tymek666 on 2006-08-29
Well, my usb stick works fine, it's detected and mounted automatically. After plugging in window pop up, just like cd's.

---

### Post by Rog131 on 2006-08-29
Did you upgrade from breezy ?

If yes: Topic: USB storage devices fail to automount
[http://kubuntuforums.net/forums/index.php?topic=4890](http://kubuntuforums.net/forums/index.php?topic=4890)

> I upgraded from Breezy to Dapper some weeks before the official release, replacing "breezy" with "dapper" in sources.list, then "update" and "dist-upgrade". After this, I had the same problems described above with automounting etc, particularly USB camera and stick.

What I realized had happened, after reading the discussion in this thread, is that the upgrade process completely left out ivman daemon and hal (they were pherhaps removed from the Breezy release and not re-installed in the dist-upgrade, since there were ivman configuration files left over from Breezy). This might be due to the "early" upgrade before official release, but when the official was out, updating packages didn't change the situation.

After installing ivman package using adept, which pulls in 3 other as dependencies, I was finally able, without the need to play with (for me) obscure configuration files, to have the desired functionality back as expected and plainly working.

Hope this can be of help.

Note: When i upgraded many programs was removed not upgraded. (ivman was one of them )

---

### Post by KubuntuKilledMe on 2006-08-29
Thank you for your replies. I've solved the problem.

A long time ago in breezy there was a bug where device icons would not show up on the desktop. A suggested fix for that involved editing /etc/default/hal and uncommenting an option to "retain privilege", as in stay as root. I did that.

Later on, on a fresh install of dapper the same problem happened and i tried the same solution, which didnt work. But the change stayed, as i tought it couldn't hurt to stay root.

Now USB storage wasn't working and with many reboots i noticed the hald options listed on quick scrolling text. Unable to pause the text, which didnt show on dmesg, i just rebooted over and over again trying to read the beggining, which was hald:invalid option or something to that effect. It then listed the valid hald options as in its man page. A quick glance at that manpage shows no "retain privilege" option, so i guess it was deprecated on the version that ships with dapper. Editing back /etc/default/hal again and commenting the option, and rebooting, completelly solved the problem.

It would have been nice for hald to not just abort loading on an option that had just been removed, but i understand the developers position. KDE, however, should warn that it cant find hald running since i have the option to use hald enabled and saw no error message at all.

---

