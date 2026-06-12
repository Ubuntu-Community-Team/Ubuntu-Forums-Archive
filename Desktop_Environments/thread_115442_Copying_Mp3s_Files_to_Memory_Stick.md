---
title: "Copying Mp3s Files to Memory Stick?"
date: 2006-01-10
forum: Desktop Environments
---

### Post by kimvall on 2006-01-10
Hello all, I just bought a 1 gb memory stick to my Ericsson K750i. When I connect the cellphone to the PC (via USB cable) it immediately appears on the desktop. No problem there.

 Also, when I copy mp3 files to the memory stick they appear as they should, and everything indicates that nothing is wrong.

 However! When I unplug the cellphone and attempt to play the files, they are nowhere to be found. Frustrating indeed.

 Sometimes, almost exclusively when I copy the mp3 files one at a time (REALLY time consuming) one or two of these files appear in the cellphones media library. But usually, they cannot be played as a minimum of the files has been copied to the memory stick. Or they are all messed with up each other (I play one of them, but a hear about two or three second samples of a lot of different track).

 Perhaps I am doing it all wrong? Perhaps browsing the content of the memory and copying it manually is perhaps the wrong way of doing it?

 Thanks in advance.

---

### Post by nxn on 2006-01-10
Hmm, can you copy the files directly to the memory card, take it out, put it back in, and try to play the files from the card? This should tell you if the problem is more with the cell phone reading the files or if there's a problem with the files going on the card itself.

I'm not really sure, but maybe it is picking the wrong filesystem when it mounts the card?

---

### Post by Quartus on 2006-01-10
A lot of people are having problems with memory sticks, me too as I have a PSP. Haven't found a solution yet though.

---

### Post by toorima on 2006-01-10
I have the same phone with 1 gb memory stick and I also have the exact same problem, part 1 of this guide [http://www.ubuntuforums.org/showthread.php?p=645226#post645226](http://www.ubuntuforums.org/showthread.php?p=645226#post645226) did it for me tho, if it's a lot of music it takes a little time but most of the time it's just a few pics or a theme or a few songs so it works well and I don't have to find the cable or have it with me (laptop).

But a fix for this would be very nice

---

### Post by Jussi Kukkonen on 2006-01-10
Remember to unmount the stick before yanking the usb cable...

---

### Post by kimvall on 2006-01-10
Hmm, do you use a USB cable to connect, or do you connect via bluetooth?

[QUOTE=toorima]I have the same phone with 1 gb memory stick and I also have the exact same problem, part 1 of this guide [http://www.ubuntuforums.org/showthread.php?p=645226#post645226](http://www.ubuntuforums.org/showthread.php?p=645226#post645226) did it for me tho, if it's a lot of music it takes a little time but most of the time it's just a few pics or a theme or a few songs so it works well and I don't have to find the cable or have it with me (laptop).

But a fix for this would be very nice[/QUOTE]

---

### Post by kimvall on 2006-01-10
Do you know which file system it is? Then I could perhaps mount it manually.

[QUOTE=nxn]Hmm, can you copy the files directly to the memory card, take it out, put it back in, and try to play the files from the card? This should tell you if the problem is more with the cell phone reading the files or if there's a problem with the files going on the card itself.

I'm not really sure, but maybe it is picking the wrong filesystem when it mounts the card?[/QUOTE]

---

### Post by toorima on 2006-01-10
I use bluetooth with my phone.

Think I've tried with unmounting when using the cable but will try it again just to make sure

---

### Post by sinaen on 2006-01-10
[QUOTE=toorima]I use bluetooth with my phone.

Think I've tried with unmounting when using the cable but will try it again just to make sure[/QUOTE]


yup i have the sony ericsson w800i and its the same problem for me, if i umount it or not :/ well it seems to be worse when i don't unmount. Did you fellows put the media in the rigth folder, the one they mentioned in the manual? pictures to one folder and musik to another, and files the phone didn't recognize would go into another folder? I don't have the folders names in my head but it was in Media Files -> audio that sound went into anyway.

did it work better if you only used the card in a card-reader?
i have a built in card reader in my laptop but i dont have any drivers for it in linux, it doesn't show up anything when i put in a card in it, and ive tryed both types it can read.

Tomorrow i think ill go buy a usb-blutooth dongle, and then hope it has some drivers in it, so i can get it to work in linux, seems nicer if the interface is wireless too, as one of you mentioned before no cable to worry about :) cables are a real hassle :D and i have plenty of time. I tried the disc2phone in windows and finally gave up and went to bed :D well by then i had the transfer going over to my phone but, it was veeeeeery slow... it took about a hour or so to get over 66 files :D

---

### Post by sinaen on 2006-01-11
It works greeeeat to transfer files to the phone via bluetooth :D

im so happy whoho!
Thanks to pointing me to this thread (whoever that was)

---

### Post by pmj on 2006-01-11
The reason you get damaged files on your phone is probably due to a bug somewhere that makes file copying look quicker than it really is, and when you're told that it has finished copying it's actually still going.

I don't know if there's a real fix for this problem, my way of dealing with it is to simply let it stay connected for several minutes after Nautilus says it's done to make sure all files have really been copied over.

---

### Post by sunny_nwho on 2006-02-05
hi there...even i have the same problem with my K750i after i copy the files and unmount the volume i just wait for a few blinks of the hdd led on the laptop and then remove the cable....but mind it if the file sizes are large then u might want to wait a bit longer....i think it is a bug in Nautaulis showing tht the files have been copied inspite of not getting fully copied...

---

### Post by overgee on 2006-02-15
[QUOTE=pmj]The reason you get damaged files on your phone is probably due to a bug somewhere that makes file copying look quicker than it really is, and when you're told that it has finished copying it's actually still going.

I don't know if there's a real fix for this problem, my way of dealing with it is to simply let it stay connected for several minutes after Nautilus says it's done to make sure all files have really been copied over.[/QUOTE]

I think there is no problem with nautilus and co. It seems that nautilus just copies "placeholders" instead real files in the first place. When you unmount your usb-stick device it starts copying the actual files. So you have to wait for a couple of minutes before you unhook your device.

---

### Post by pmj on 2006-02-15
[QUOTE=overgee]I think there is no problem with nautilus and co. It seems that nautilus just copies "placeholders" instead real files in the first place. When you unmount your usb-stick device it starts copying the actual files. So you have to wait for a couple of minutes before you unhook your device.[/QUOTE]
I don't think this is a problem with Nautilus like you describe, but even if it was, how would that NOT be a problem? Shouldn't you be able to trust your file manager to tell the truth when it says it's done copying?

The reason I don't think this has anything to do with Nautilus is because it's the same when I do it from a terminal. Lines are spit out claiming files to have been copied, when in fact they haven't.

---

### Post by RAOF on 2006-02-15
[QUOTE=pmj]I don't think this is a problem with Nautilus like you describe, but even if it was, how would that NOT be a problem? Shouldn't you be able to trust your file manager to tell the truth when it says it's done copying?

The reason I don't think this has anything to do with Nautilus is because it's the same when I do it from a terminal. Lines are spit out claiming files to have been copied, when in fact they haven't.[/QUOTE]
This could well be the kernel/filesystem drivers.  I think that write cacheing is on by default, which means that the files get written to memory, and then from there to the USB stick.  So nautilus, cp, and the like finish really quickly and some of the work gets done in the background.  If that background work doesn't finish, though, you're left with unwritten data in memory.

---

### Post by pmj on 2006-02-15
Thanks RAOF. That makes a lot of sense.

---

### Post by hashimoto on 2006-02-15
I have noticed a similar with my mp3 player. It is a iRiver 1Gb one and even though Nautilus (when I use the usm firmware) and the iRiver software (with standard firmware) claim that teh files have been transferred it really is still going on. Luckily the player itself tells when the transfer has finished, othewise I would be just guessing.

Oh yes, and the player is a usb2 one but I only have a usb1 in my pc. Annoyingly slow.

---

### Post by sinaen on 2006-03-05
Hi! again
I rang the sony ericsson support and they told me to update my phone, the reason why I rang them was'nt because of this problem but i asked anyhow cause i wanted to know.

They said that if i updated the software in the phone with the automatic update software that is on the ericsson homepage the filetransfer problem and several other glitches would be fixed..

and it has worked for me anyway so its a tip...

---

