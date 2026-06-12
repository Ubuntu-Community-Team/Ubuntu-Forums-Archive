---
title: "Cannot drag music into ipod problem!!!!!"
date: 2009-04-18
forum: General Help
---

### Post by NathanDS101 on 2009-04-18
hello im recently trying to drag music into my ipod nano chromatic and it says this "Error transferring track Error opening file '/media/disk/iPod_Control/Music/f08/Soulja Boy - Kiss Me Throug.mp3': Read-only file system"(no quote) i use limewire to get my music please find me an solution please!!!!

---

### Post by SkippoGuangiacomo on 2009-04-18
It might be that you need to change permission to the folder. Try: 
man chmod

---

### Post by NathanDS101 on 2009-04-18
> **SkippoGuangiacomo said:**
> It might be that you need to change permission to the folder. Try: 
man chmod

in the terminal??

---

### Post by frecon on 2009-04-18
Try using the music player Rhythmbox for transferring music to your ipod. And by the way, please try to use only one exclamation mark. ;-)

---

### Post by NathanDS101 on 2009-04-18
> **frecon said:**
> Try using the music player Rhythmbox for transferring music to your ipod. And by the way, please try to use only one exclamation mark. ;-)

i do and its giving me the problem i posted

---

### Post by Penguin Guy on 2009-04-18
Your ipod doesn't support Linux, so Linux gives it random permissions every time it's plugged in. Two ways to avoid the problem:
[LIST]
[*]Operate as root.
[*]Plug you ipod in and out until it works.
[/LIST]
If anyone does know a solution then please post it, but I'm quite sure there is none.

---

### Post by NathanDS101 on 2009-04-18
awww

---

### Post by hikaricore on 2009-04-18
I had to setup a line in /etc/fstab for my ex's ipod once.
It worked perfect but it would never dismount properly and I ended up having to write a script for it.

More trouble than it's worth trying to do it properly.

---

### Post by SkippoGuangiacomo on 2009-04-18
> **NathanDS101 said:**
> in the terminal??
yes! Then you can set up the permission, and write in your ipod

---

### Post by NathanDS101 on 2009-04-20
> **SkippoGuangiacomo said:**
> yes! Then you can set up the permission, and write in your ipod

But how do i write it in the ipod?

---

### Post by NathanDS101 on 2009-04-25
sOme one plz help!

---

### Post by spillin_dylan on 2009-04-25
I think that there is something to do with Apple's encryption on the newest iPod 6g and iPod Nano 4g's.  There is a way to "jailbreak" them by finding the correct hash in the firmware memory, and using this hash to allow ubuntu to write to the iPod.  Also, maybe these will help:

[http://ubuntuforums.org/showthread.php?t=103071](http://ubuntuforums.org/showthread.php?t=103071)
[http://ubuntuforums.org/showthread.php?t=619615](http://ubuntuforums.org/showthread.php?t=619615)
[http://fsrc.freehostia.com/Ubuntu-iPod-Nano.html](http://fsrc.freehostia.com/Ubuntu-iPod-Nano.html)

---

### Post by SPARTAN-118 on 2009-06-19
Well, I don't have a Nano Chromatic, but I do have the previous Nano (first to play vids). 
I have a similar problem with Rhythmbox; whenever I try to drag a song onto the iPod now, it says "Could not write to device". When I ejected it and checked out the free space (by scrolling to the "Shuffle Songs" option) it said 0 KB! No matter how many songs (and videos) I delete, it just won't go down! It's worked before!

PS my iPod is a 4 GB (I know small, especially since I have over 500 songs on my computer).

---

### Post by Soul-Sing on 2009-06-19
There are several musicplayer that support media transport protocol or: mtp. Banshee /amarok maybe rhythmbox. That sometimes will help.
But i think also that it has something to do with the new firmware or "protection" (encr.) by apple.

---

### Post by MusicMan374 on 2009-06-19
Easier solution: get an mp3 player that has the same features and more T_T iPods are designed to work with iTunes, which is only available on windows and macs. It's more trouble than it's worth to attempt to get it to work with linux. a creative zen xfi 32GB is about the same price as a high end ipod, its got wifi, video, music, pics, fm radio, sd slot, etc etc. Then all you have to do is copy music files over. I've never found a way to put music on an ipod.

---

### Post by MusicMan374 on 2009-06-19
and i do believe yes apple does make it very difficult for someone to put music on there without iTunes. My friend tried it once and he never figured it out. There may be some random site on the internet that has managed to hack it but it might take awhile to hunt down the solution. I wouldn't bother.

---

### Post by RobOrr on 2009-06-19
It's pretty easy to put music on most iPods without iTunes. Rhythmbox works perfectly with my iPod, as does GTKPod, a program in the repositories that lets you manage iPods just like iTunes. If worst comes to worst, you may also want to consider using a different firmware for your Nano. I use RockBox as it doesn't use that stupid file storage system and can play mp3, ogg and so forth.

If you are unsure about any terms I use, google them and there's a wealth of information about. Just make sure you check out the info for your specific iPod, as every version has different firmware.

---

### Post by SteveBurt on 2009-06-19
Linux seems to work fine with older iPods, but newer ones often have problems. I have a recent iPod Classic.

Amarok completely scrambled all the cover art on my iPod.
Rhythmbox will read stuff off the iPod but not write to it.
Playlists don't seem to be properly supported.
Automatic photo synchronisation (as iTunes does) isn't supported - you have to drag by hand using gtkpod.
No Linux tools have the 'single click synchronisation' which iTunes offers. You have to remember what's changed, which is a pain when you have 10s of Gigs of music on the iPod.

And so on.

In the end it was easier just to use a Windoze machine to manage my iPod.

And to those who say 'why not use a different music player' - I will as soon as I find one with as intuitive a user interface and as good a range of accessories.

---

### Post by RobOrr on 2009-06-20
its a shame you had all those problems. I use an iPod Video (30Gb) and the only bugbear I had with linux was the one-click synchronisation, but I used XP so rarely that my iTunes library rapidly got out of date compared to my Rhythmbox library ;) 

RockBox makes my synchro life easy though. All my music stored in a file tree on the drive that's an exact copy of my music file tree on the PC, so a simple copy without replace script I wrote now makes my music synchronisation pretty easy. It's the main advantage I've found with changing the apple firmware, along with being able to play multiple music file formats.

---

### Post by kingchipo on 2009-06-20
Thread op an quick an easy work around may be to use a virtualbox.. i know its inconvenient but eventually a media player should start supporting the newer generation ipods

---

### Post by snapback77 on 2009-06-20
Switch to Banshee.

---

### Post by three08 on 2009-07-03
i get the same error message as the OP, but the gpod script doesn't work because the ipod is apparently a read-only file system. for the same reason, i can't mod the permissions or owner. fdisk says it doesn't have a partition table. gparted gives it 3 partitions - sdc1-3 - of which the first two are of an unknown or nonexistent filesystem type, and the third is HFS+. sdc1&2 are 31kb and 64mb, respectively - sdc3 is the remaining ~28 gb. this is talking about a 3-year-old, 5th-generation 30gb ipod. my brand new 3rd gen 8gb nano has worked like a dream since i plugged it into my linux box.

is there any option other than formatting it? and, if not, would it have to be formatted as a specific filesystem type?

---

### Post by solotwit on 2009-07-03
I had to reformat mine on a windows machine to FAT32 format. Using diskmanager. I still can't get anything to write to it using Rythmbox though.

---

