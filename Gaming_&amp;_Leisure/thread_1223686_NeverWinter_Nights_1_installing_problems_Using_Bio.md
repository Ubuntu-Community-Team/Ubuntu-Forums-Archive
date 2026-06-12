---
title: "NeverWinter Nights 1 installing problems: Using Bioware Native Client"
date: 2009-07-26
forum: Gaming &amp; Leisure
---

### Post by Mandala 13 on 2009-07-26
Hi! Here's the deal. Recently I got myself the disks of NeverWinter Nights. Now, when I put them in, this UDF problem appears, that as I have read, is pretty common in Jaunty. Just when I was trying to convince someone to get me the same discs in other format for me to be able to install them, I remember that actually NWN had a native client. Lucky me, I said.

So I followed this [Guide in Spanish]("http://dukkon.blogspot.com/search/label/Juegos") on how to installing it. The only difference was that I didn't download any Spanish Language Packages because I just want to play the game in English, just as the original D&D. Well, I did the whole thing but things didn't really worked out. Here's what I did:

1) Get game resources wget [http://files.bioware.com/neverwinternights/updates/linux/nwresources129.tar.gz](http://files.bioware.com/neverwinternights/updates/linux/nwresources129.tar.gz)
2) Get Client/Binary Package     wget [http://files.bioware.com/neverwinternights/updates/linux/nwclient129.tar.gz](http://files.bioware.com/neverwinternights/updates/linux/nwclient129.tar.gz)
3) Get last Patch [http://nwn.bioware.com/support/patch_linux169.html](http://nwn.bioware.com/support/patch_linux169.html)
4) Extract Resources 
5) Extract Client and Patch inside extracted NWN folder
6) Before extracting Patch, erase override content : rm -f override/*
7) Execute game script with ./nwn
8) Segmentation Fault Error
9) Edit nano nwn to leave it like this:


```
#!/bin/sh

# This script runs Neverwinter Nights from the current directory

export SDL_MOUSE_RELATIVE=0
export SDL_VIDEO_X11_DGAMOUSE=0

# If you do not wish to use the SDL library included in the package, remove
# ./lib from LD_LIBRARY_PATH
export LD_LIBRARY_PATH=./miles:$LD_LIBRARY_PATH

./nwmain $@
```

10) Execute game script with ./nwn

Now, when I first execute the ./nwn command, monitor when black for a while, and the come back. When I did it the second time, after "fixing" the nano nwn file, monitor went black again, but for ages! Actually, I waited at least 20 minutes before deciding that things weren't actually working fine. It's suppose to prompt me to insert the serial key, but instead, I got nothing at all.

So, what should I do for doing it? I could followed the instructions on how to installing the disk, but as I said before, this #%$$ UDF problem doesn't let me, :(. So, installing the client is for me the best option considering that, after all, Bioware made it specifically for us Linux-Users. 

Any help that you could provide? Now using Jaunty, but if someone would tell me that in Hardy things would be better, I would format the computer in no time. After all, I really, really want to play the game.

---

### Post by Mandala 13 on 2009-07-26
Here's the error that I'm getting when trying to open the game. Obviously, as many Jaunty users, I'm having sound problems... Is that the cause of it then?

```
mandala13@Amaterasu:~/nwn/nwclient129$ ./nwn
ALSA lib pcm_dmix.c:975:(snd_pcm_dmix_open) unable to create IPC semaphore
Segmentation fault
```

---

### Post by oldrocker99 on 2009-07-26
Definitely a sound problem. Try OSS (in System/Preferences/Sound) or maybe PulseAudio. Another reason why I'm still using good ol' Intrepid 8.10 and have yet to have a sound problem in NWN.

:guitar:

---

### Post by Mandala 13 on 2009-07-26
So sad... Well, I'm already using OSS in Sound Preferences, but one of the first things that I do after installing Jaunty is unistalling PulseAudio... Let's say that PA and me have a hate history...

But well, there are two options that I could consider then:

1)Installing PA again and trying to make it work.
2)Downgrading to Hardy, where I do have 100% sound, but graphic card problems.

:(

---

