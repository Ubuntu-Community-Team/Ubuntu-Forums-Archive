---
title: "(weird?) problem with Ubuntu and USB MP3 player"
date: 2005-12-12
forum: Desktop Environments
---

### Post by Bou on 2005-12-12
Hi, I'd like to comment a problem I have with a recently bought MP3 player: it doesn't seem to need any kind of drivers like some other players, and when I plug it it shows up in the mounted devices list and opens in a Nautilus window... sometimes.

But sometimes, when I plug the player its screen just freezes if it's on, or doesn't do anything if it's off. Then, the USB device doesn't appear anywhere, and it's just like I hadn't plugged anything at all.

Sometimes it mounts OK and the Nautilus window appears, but in the middle of copying files the process just freezes, meaning it gets stuck with one file and the stimated time starts to rise (it goes 3:12, 3:14, 3:20...), and then happens what I wrote in the previous paragraph. I have to restart my computer for it to recognise the device again, and sometimes not even that works. This behavior seems to happen randomly and I don't know what can be causing it... I phoned for technical support, but the girl who attended me didn't sound like she had an idea, and just told me that Microsoft's monopoly extends to the MP3 players, literal.

So, can you tell me if this is normal or not? Is there any kind of explanation? If the player is not compatible with Linux, why does it work most of the time? I tried with two different players and two cables, so it's not broken or anything.

Thank you all.

---

### Post by Franko30 on 2005-12-15
HI,

Sorry I cant' help you here.

But others might if you gave them more information on make and model of the player, on the used Ubuntu version etc.

Cheers

Franko30

---

### Post by Mustard on 2006-01-20
On thing you should do when you encounter this problem is go to your Applications>>System Tools and look over the System Logs for possible error messages recorded in the logs, that may relate to the problem.

---

### Post by bbogart on 2008-03-13
This is happening to me too, nautilus seems to copy a few files, but freezes after some time and never exits or recovers. No errors in the logs. 

The strange thing is that if I manually mount the mp3 player and copy the files from terminal everything works fine. I can even copy the files using a root nautilus, so its not a nautilus problem but a mounting issue. 

Here is what I did: 

1. First unmount the filesystem

2.  What filesystem is it? 

> df

3. Which gives me something like this for my mp3 player:

/dev/sda1              2048992    287136   1761856  15% /media/IAUDIO

4. Umount it: 

> sudo umount /dev/sda1

5. Then remount it: 

6. Make sure there is a /mnt directory (if there is not create it.)

> file /mnt
/mnt: ERROR: cannot open `/mnt' (No such file or directory)
> sudo mkdir /mnt

7. Mount the filesystem

> sudo mount -t vfat /dev/sda1 /mnt

8. Copy files

> cp [files to copy] /mnt/music (the name of the music folder on the mp3 player)

9. Umount the filesystem

> sudo umount /mnt (this might take some time, as the copying only happens now)

I did notice that with the above method 8.3 filenames show up as lowercase, but the automount shows them as all upper case. 

I'll look for a bug about this now, and file one if I can't finding anything.

.b.

---

