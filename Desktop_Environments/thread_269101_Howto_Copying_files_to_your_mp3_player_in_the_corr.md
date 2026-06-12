---
title: "Howto: Copying files to your mp3 player in the correct order"
date: 2006-10-01
forum: Desktop Environments
---

### Post by transient on 2006-10-01
There are a lot of mp3 players out there that don't play the songs in an alphabetical order - instead, they ignore the filenames and play the files in the exact order they were copied to the device. And with these players, a problem rises from the fact that Nautilus handles file transfers in a somewhat random order instead of sticking to an alphabetical order.

What i'm going to suggest here is a simple workaround to this problem. I found this little tool called [fatsort]("http://fatsort.berlios.de/"). You can either get it from this link, or through Synaptic, it's up to you.

How it works:
You just copy the files/directories to your mp3 player without worrying about the copying order. You then run fatsort, and it sorts everything in your mp3 player in an alphabetical order.

As an example, if your mp3 player is located at /dev/sda (as mine does), you type:

```
fatsort /dev/sda
```

And within less than a second, everything in the player is sorted alphabetically :KS

[B]edit_1: Note that you need to make sure the file transfer is totally over before running fatsort. Please read the 5th post in this thread for more information.

edit_2: With the latest version of Fatsort(0.9.7) you first have to unmount the usb device (right-click on its icon on the desktop and select eject) before running fatsort. This prevents the problems i mentioned in edit_1.[/B]

...
emre

---

### Post by lagagnon on 2006-10-01
You should post this great little idea to the HOWTO Forum!

---

### Post by joris1977 on 2007-01-26
real nice howto looks so simple...

but why doesn´t it work then. 	](*,)

Any ideas?   This is my terminal output: 

joris@Ruuf:~$ fatsort /media/usbdisk
FATSort Utility 0.9.4 by Boris Leidner <fatsort@formenos.de>

sort_fs: Is a directory

---

### Post by transient on 2007-01-26
Well, try to figure out the "dev" path to your device. In my case it was /dev/sda.

An easy way of finding that out is:
First make sure the usb device is plugged. Then from the top ubuntu panel,
System>Administration>Disks (note that i'm using dapper, the "disks" item might be located under some other menu in newer/older ubuntu versions)

The left part of the window will show your hard disks, one of which will be the usb device. You can recognize the usb one by its size. Click once on it, and somewhere on the right side you'll see the "dev" path to your usb device.

.
e

---

### Post by transient on 2007-01-26
By the way, one important thing i forgot to add to this howto...

**Before fatsort'ing your device, make sure that the file transfers are complete**. While the transfer may seem to be done in just a few seconds, don't let the progress bar fool you, it might actually go on in the background for a few more minutes. 

If you run fatsort before the transfer is finished, it will probably **corrupt** the FAT file system on the device.

This is how i make sure the file transfer is over:
After the transfer, safely remove the usb device (right click on its icon on the desktop and select "eject"). The "eject" command makes sure the transfer is totally over before ejecting (so it may display a progress bar and make you wait for a few minutes). When the progress bar disappears, unplug the device, plug it again, run fatsort, run the eject command again, and finally unplug the device.

.
e

---

### Post by joris1977 on 2007-01-27
Thanks, that did the trick! Works real nice now.  

I also found out that you can list the partition table on the terminal with the command: fdisk -l
(Watch out with this command, because it is a partitioning program)

:D

---

### Post by phil2890 on 2007-02-04
Hi i downloaded the file, but i dont know how to use it :P can somerone please help me?

---

### Post by transient on 2007-02-05
Well, the easiest way of installing fatsort is through Synaptic Package Manager.

If you want to use the latest package from the fatsort site instead, you'll have to compile it:
Extract the contents of the tar.gz file into a folder. Enter this folder in terminal and type "make". You now will have the "fatsort" executable. Then copy this executable to the "/bin" directory.

.
e

---

### Post by phil2890 on 2007-02-05
sorry i really dont get any of this at all :s, thanks for the help anyway (Y)


ooops sorry realised this was all for a different operating system other than windows, and ive got windows, sorry about that, any other windows equivalents available?

---

### Post by MJN on 2007-05-07
Transient, you deserve a medal for this!

I recently upgraded my car stereo to one which can play mp3's from a memory stick and whilst generally it works perfectly it does seem to take the easy way out of playing tracks in the FAT order... Bizarre given it has full support for ID3 tags, can read filenames fine, and indeed is happy to traverse directory/file structures so it's suprising it can't handle a simple sort-by-name function.

Anyway, when I copy my mp3s across with Konqueror on the whole the order is preserved however there always seems to be the odd album which features a track out-of-order so this 'fatsort' is a God-send - good find!

Quite how I missed this during hefty trawls of the Internet I don't know... I didn't even find a Windows utility which could do this which was surprising...

Anyway, thanks again for sharing this with us...

Mathew

---

### Post by transient on 2007-05-07
Glad i could help :)

Actually, the guy who develops fatsort is the one who deserves thanks... So, thank you, Boris Leidner.

.
e

---

### Post by clubsoda on 2008-01-10
Fatsort rocks!

---

### Post by loko on 2008-03-09
After looking a long time for a solution of the problem with the order of mp3-files i found this thread.

fatsort solved all my problems with the files. it's a shame that the the players play the files not in the right order even with correct id3tag.

---

### Post by sergiom99 on 2008-04-10
great one! thanks.

---

