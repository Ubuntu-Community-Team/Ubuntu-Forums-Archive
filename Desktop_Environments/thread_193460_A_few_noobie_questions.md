---
title: "A few noobie questions"
date: 2006-06-10
forum: Desktop Environments
---

### Post by Orixyu on 2006-06-10
Hey guys, Im a first time linux user, ever. Whilst I like it alot, it's such a big flip around from windows. Im using Ubuntu, the newest one.

I have to say, I like it alot more, except for a few little things that I can work around.

The download manager for programs, I like this alot, I installed Azuerus and VLC Media player. Azuerus plays up alot for some odd reason, it pops up with errors in the bottom right hand corner of my screen, and they dont go away even when i click "Hide". I also have trouble opening torrent files, azuerus says "It's not a file"

How can I update drivers? Alot of the drivers in the device manager seem to be iffy, like not right. Im running 64x and I've got the 64x Ubuntu, but what about the rest of my drivers? What do I do?

Also how can I make VLC the default media player for video files?

So many little things that I am unaware of, thanks for the help in advance guys. Im looking forward to kicking back with linux for a long time.

---

### Post by npodges on 2006-06-10
Which drivers are you looking for? i'm guessing video card, probably. there are how-tos in these forums that are real good for installing most of the common ones. what exactly are you looking for?

---

### Post by glotz on 2006-06-10
To make a file type to be displayed with a certain software, right click on the file and select open with...

---

### Post by cskeide on 2006-06-10
[QUOTE=Orixyu]Also how can I make VLC the default media player for video files?[/QUOTE]

Right click on a video file and select properties. In the "Open With" tab, you can select default media player.

---

### Post by Orixyu on 2006-06-10
Uhm, my Radeon 9200SE drivers I guess. Motherboard drivers for A8V Asus Motherboard, 64x 3500 CPU drivers.

I guess Ubuntu already has inbuilt drivers, because the system isnt running to slow, and I've got sound which tells me some motherboard drivers are working.

But it should be running faster than this, I suppose.

---

### Post by Orixyu on 2006-06-10
[QUOTE=cskeide]Right click on a video file and select properties. In the "Open With" tab, you can select default media player.[/QUOTE]

Done that, cheers.

---

### Post by der_joachim on 2006-06-10
[QUOTE=Orixyu]Uhm, my Radeon 9200SE drivers I guess. Motherboard drivers for A8V Asus Motherboard, 64x 3500 CPU drivers.

I guess Ubuntu already has inbuilt drivers, because the system isnt running to slow, and I've got sound which tells me some motherboard drivers are working.

But it should be running faster than this, I suppose.[/QUOTE]

I do not know which chipset your motherboard has, but most nForce chipsets have drivers which are downloadable at NVidia's site. Mind you, I never bothered to, since everything was supported out of the box.

I recommend that you install the athlon kernel. The standard 2.6.15-k8 kernel is blazingly fast and it supports your second core out of the box. Just do a ```
sudo apt-get install linux-k7
``` in a console. 

You only real problem may be your Radeon card. Ati's support for linux is a pain in the bottom to say the least. I bought Nvidia, so I cannot help you here.

---

### Post by Orixyu on 2006-06-10
Isnt the 3500 a k8 athlon?
Im in the Synaptic Package Manager now, I've currently got the;
"linux-amd64-generic" the complete kernal for x86_64 installed.

Theres also a "lunux-amd64-k8" complete kernal for AMD K8?

I followed an ATI guide for installing the latest ATI drivers, I've done this, and I "think" its working now.

Another question, I've installed aMSN, but I dont seem to have any of the default windows fonts avaliable to me, is there a package out there with all the XP fonts, such as Tahoma, Verdana ect?

Cheers.

---

### Post by fastb on 2006-06-10
Here is a solution to your azureus problem. I had the same problem.

Check out the third post. It works great!
[http://www.ubuntuforums.org/showthread.php?t=188825&highlight=azureus](http://www.ubuntuforums.org/showthread.php?t=188825&highlight=azureus)

---

### Post by cskeide on 2006-06-10
[QUOTE=Orixyu]Another question, I've installed aMSN, but I dont seem to have any of the default windows fonts avaliable to me, is there a package out there with all the XP fonts, such as Tahoma, Verdana ect?[/QUOTE]

msttcorefonts provides the most common windows fonts. Install the package through synaptic, or open a terminal and run the following command:
```
sudo apt-get install msttcorefonts
```

---

### Post by Orixyu on 2006-06-10
[QUOTE=cskeide]msttcorefonts provides the most common windows fonts. Install the package through synaptic, or open a terminal and run the following command:
```
sudo apt-get install msttcorefonts
```[/QUOTE]

Nope, i've already installed that package, but I still dont have access to Tahoma ect; ](*,)

---

### Post by ayoli on 2006-06-10
maybe you should refresh your font cache with:

sudo fc-cache -fv

---

### Post by Orixyu on 2006-06-10
msttcorefonts gets this error;

Package msttcorefonts is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package msttcorefonts has no installation candidate

and I used that fc-cache -fv line, but I still dont have access to windows fonts in aMSN.

---

### Post by ayoli on 2006-06-10
i ve just install msttcorefonts_1.2ubuntu3_all.deb with synaptics without pb.
fc-cache wont bring you these fonts if the package is not installed.
maybe  you have to activate universe multiverse repositories to get this package, i havent verified that

---

### Post by Orixyu on 2006-06-10
Im also getting abit of lag at times.
I dont believe my system really should be getting any lag just from mp3s playing and browser processes open.

It's very slight, and it makes my sound distort abit. Any suggestions?

I also find opening the recycling bin to see graphical glitches on my desktop before the recycling bin completely expands over my desktop?

Also, what is the 'best' MSN Messenger programme for Linux? I've been using aMSN, and I cant stand it, it's just so damn dodgy.

---

### Post by mgmiller on 2006-06-10
Try running GAIM.  It's under Applications>Internet.  This will talk to msn, aim, yahoo messenger, the whole works from a single interface.

---

