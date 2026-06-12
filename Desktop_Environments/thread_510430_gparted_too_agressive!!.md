---
title: "gparted too agressive!!"
date: 2007-07-26
forum: Desktop Environments
---

### Post by BobSongs on 2007-07-26
Gparted is giving me grief.

I want to give Feisty Fawn a try. Windows XP is installed and I'm about to erase my Dapper partition and write Feisty to it.

the process[LIST]
[*]Double-click Install on desktop
[*]Language selected: (English)
[*]City selected: (Gotham City)
[*]Keyboard selected: (US English)
[*]Prepare disk space: (Manual)
[*]Now the dialog box says: "Prepare Partitions"[/LIST]Here's where things go far stranger in Feisty than in Dapper. The Windows XP partitions has this:

Device: /dev/hdc1
Type: ntfs
Mount point: /media/hdc1
Format? [ ]
Size: 15841 MB
Used: 6300 MB

So far, so good. The desire is to change the **mount point** of the Windows XP partition from **[COLOR=DarkRed]"/media/hdc1"[/COLOR]** to simply [COLOR=DarkRed]**"/win"**[/COLOR]. This is where things go strange.

Changing the mount results in a changes the partition's size too. I don't particularly want this to happen since predefined and pre-calculated sizes have already been allotted. 

Is there a way to do this without changing partition sizes? When clicked It defaults to ... 0 Mb. When the up/down arrows are clicked I get 6300 Mb as the suggested "new" size. :confused: Uhm, well, I use the "up" arrow to get it back to 15841
... and it won't go that high.

:(

---

### Post by pbcartwright on 2007-07-26
just don't use /dev/hdc as a mount point during the install, and add it to fstab after you are done.. it won't mess with it if you don't add it.. I have dual drives and 3 different operating systems, and I just didn't add each OS as a mount point for every insall...

---

### Post by ugm6hr on 2007-07-27
Just let the installer do what it wants - then change the mount point afterwards.  This is a good tutorial on how to do that:
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

