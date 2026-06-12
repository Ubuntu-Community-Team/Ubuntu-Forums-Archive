---
title: "Can transfer mp3 but no playback on MuVo 128MB"
date: 2006-03-04
forum: Desktop Environments
---

### Post by puddin73 on 2006-03-04
Hi all--looking for some help getting mp3 files to play on my Creative NOMAD MuVo (128MB) flash mp3 player in Breezy. (I have a ThinkPad 600e notebook.)

No problem recognizing the drive (though it's a little squirrely sometimes showing the right amount of free space), and no apparent problem transferring mp3 files that I ripped using sound-juicer. And the notebook plays the mp3s fine in xmms. But the player won't play the files when I transfer them--there's an LED on the player that goes solid red when I try. No problem playing mp3s transferred from a ThinkPad X20 running XP Pro.

And I DID patch sound-juicer so it actually rips mp3s in addition to ogg.

Thanks!

---

### Post by anasofiapaixao on 2006-07-24
I also have a player (not MuVo) with wich happens the same. I can't playback ANY song provided I copied them under linux. I am getting so sick of all this... what's the hold of? I really don't want to waste HD space on a stupid windows copy, but looks like virtually everything I have is in the "designed for windows XP" bullshit. It is getting too much for me.
*sigh...*

---

### Post by anasofiapaixao on 2006-07-28
Hello again... I have gotten a workaround to this that is really weird but works. First, blaming like any good linux user Windows as the cause of all my disgraces, I tried formatting the drive in linux for the first time. But an advice... DON'T do it with gparted or you'll get really weird results (like two partitions showing when you only have one...). I did this:

Delete any partition in the drive and run cfdisk. Don't forget to choose FAT16 on the filesystem (I guess it was option #08 or 06, you'll have the partition type list there anyway) and write the new partition table.

You should have an empty FAT16 partition then. Exit and pass whatever you have to pass to the drive. And DON'T HOT-UNPLUG!!! Right-click the desktop icon and select "eject". For some reason what you did before was just select files for *a synchronization that is being done* when you eject the drive!....

Hope this helps! Not sure if the formatting is totally needed tho...

---

### Post by ifokkema on 2006-07-29
Hi,

> **anasofiapaixao said:**
> And DON'T HOT-UNPLUG!!! Right-click the desktop icon and select "eject". For some reason what you did before was just select files for *a synchronization that is being done* when you eject the drive!....
Just a note - when you tell Linux (or Windows, for that matter) to copy files over to your MP3 player, it tells you it's done earlier then it really is done. This is to minimize the waiting time for the user. In the backgroud, your OS is still copying files. If, soon after sending the copy command, you want to unmount the player, it takes some time to synchronize (finish copying). If you would wait a bit, synchronisation would not take long because all files are already done copying in the background.

---

### Post by anasofiapaixao on 2006-07-30
Now this is the wierd point... Once I was just passing a 3 megabyte file to my player and I just left it plugged after that in order to go do other things. When I got back to it and unplugged it, the file wasn't there when I plugged it back... And no matter how long I waited, I could see it would just start to copy files in the moment I clicked "eject". Probably just my Ubuntu install's fault...

**EDIT**: Bunny is alrady in at least half of my college's central building anfitheatres' seats. I am responsible for at least three of them.

And no, we're not vandals, just people who sometimes have to sit for two hours straight on those wooden seats, with tables already a LOT written. Now how could we NOT draw on them.

---

### Post by ifokkema on 2006-07-30
> **anasofiapaixao said:**
> Now this is the wierd point... Once I was just passing a 3 megabyte file to my player and I just left it plugged after that in order to go do other things. When I got back to it and unplugged it, the file wasn't there when I plugged it back... And no matter how long I waited, I could see it would just start to copy files in the moment I clicked "eject". Probably just my Ubuntu install's fault...
Hmm... well, I never tested the time it took to copy files. Maybe it's waiting with the last couple of megs thinking you might want to copy more files. Doesn't seem logical to me, though... :?: 

Anyway, you can force synchronisation without unmounting the USB drive with the 'sync' command. Maybe that comes in handy sometime.

> **anasofiapaixao said:**
> **EDIT**: Bunny is alrady in at least half of my college's central building anfitheatres' seats. I am responsible for at least three of them.

And no, we're not vandals, just people who sometimes have to sit for two hours straight on those wooden seats, with tables already a LOT written. Now how could we NOT draw on them.
LOL, they shouldn't keep us sitting for two hours listening to boring lectures anyway, it makes our artistic side come up ;)

[QUOTE=the bunny]:twisted:  MUHAHAHA!!! I will take over the world!!!  :twisted:[/QUOTE]
What was that?

---

### Post by berggren on 2006-09-28
Hi!
I also experienced the problems that are described in the first post of this thread. This:

[http://linux.highsphere.net/howtos/muvo.php](http://linux.highsphere.net/howtos/muvo.php)

finally helped me! Normally it should be enough to check these things:

1. Be sure you have the "settings" file on your muvo. If you don have it, you must format the muvo in windows, then you&#314;l get it. DONT delete it. Best is to make a backup on your linux-box.

2. Be sure to delete the content of the trash-folder on your muvo, otherwise  linux will tell you that your muvo is full. (to see the trash-folder, "show hidden files" must be set)

---

### Post by ifokkema on 2006-09-29
> **berggren said:**
> 1. Be sure you have the "settings" file on your muvo. If you don have it, you must format the muvo in windows, then you&#314;l get it. DONT delete it. Best is to make a backup on your linux-box.
The settings file is created by the player (or related software), not by Windows. Formatting the player under windows is not much use. You must use the software that came with the player or use the player itself to format the drive.

> **berggren said:**
> 2. Be sure to delete the content of the trash-folder on your muvo, otherwise  linux will tell you that your muvo is full. (to see the trash-folder, "show hidden files" must be set)
Another way to do this is to empty your personal trash bin, it will contain the deleted files from the player as well.

---

