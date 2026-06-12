---
title: "How to install Tomb Raider 1 in dosbox/ubuntu 20.04"
date: 2021-06-09
forum: Gaming &amp; Leisure
---

### Post by lou6 on 2021-06-09
Had this up and running years ago (and a few laptops ago) but would like to do it again for a new grandson.  I have dosbox installed but can't remember how to setup TR1.  Can someone help me?  Thanks in advance...

EDIT: should have mentioned, I have the original cd's...

---

### Post by Dennis N on 2021-06-09
In general for old DOS games, you copy all files from the original disk into a folder on your computer. Determine the full path to the file (usually an .EXE file) that starts the game. 

In the terminal run:
```
dosbox <full path to the game's .EXE file>

```
That should open dosbox and start the game. If starting a game like this from the Ubuntu terminal everything in the path is case sensitive, even though in DOS it was not.

If it works as expected, you can create a .desktop file so it will appear in your menu and overview search.

---

### Post by lou6 on 2021-06-09
By some miracle of memory I managed to get this game installed and running BUT...it won't start without the CD in the drive.  Obviously, I've done something wrong because I don't remember needing the CD to play the game.  Thanks again for any and all help - perhaps something or someone will jog my memory (or tell me precisely what to do next).

---

### Post by CharlesA on 2021-06-09
> **lou6 said:**
> By some miracle of memory I managed to get this game installed and running BUT...it won't start without the CD in the drive.  Obviously, I've done something wrong because I don't remember needing the CD to play the game.  Thanks again for any and all help - perhaps something or someone will jog my memory (or tell me precisely what to do next).

I'm pretty sure that's intentional unless you used one of the no cd patches that were floating around.

As an alternative, you can grab [this version]("https://www.gog.com/game/tomb_raider_123") and play without the CD without any issues. I'm not too sure how to install it on Linux as it comes as a Windows exe, though as I don't have any experience with WINE.

The only question is how to get it running on Linux, but I found [a forum post]("https://www.gog.com/forum/tomb_raider_series/gog_tomb_raider_1_on_linux/post1") saying you just need to modify your dosbox commands from step #3 onward.

---

### Post by mastablasta on 2021-06-10
also if you plan more dos games i found that using DBGL (DossBOx game Launcher) makes it easy to install and maintain the games library. i only played demo of the first one back in the day, but i did play through all of Tomb Raider 3. hidden levels and all. good times.

---

### Post by mIk3_08 on 2021-06-10
You can try the script here. They used Lutris script installer. I don't know yet how it works but they say  it works properly when you just follow the instructions.The code maintainer / contributor always have their script updated. If you have more questions just ask them. 
They have a lot of games out here that runs on Linux successfully. [URL="https://github.com/legluondunet/MyLittleLutrisScripts/"]
Click Here[/URL]

---

### Post by CatKiller on 2021-06-10
> **lou6 said:**
> it won't start without the CD in the drive. 

That's intentional by the game devs. Sometimes official patches will remove the need for the cd, sometimes unofficial cracks will remove the need for the cd.

In this case, though, you aren't using the cd as DOS did; it's just a file (since everything is a file). So you can make a file (an iso file) that's an image of the cd, but stored on your hard drive, and tell the game to use *that* file rather than the file that represents your cd-rom drive. I can't remember the exact syntax but, once you've created your image (which you can do with any cd burning software, or just dd) you mount that image as a loopback device. Point DOSBox/the game at where you've mounted it, and you're good to go.

It's a while since I've played with DOSBox, but it might have something to do that built in.

---

### Post by lou6 on 2021-06-10
I tried several ways of creating an iso (k3b, disks) with no joy - apparently none will copy mixed media cd's.  Also tried the gog version but it will not run in wine. I may yet try the lutris route but, at this point. I'm getting pretty discouraged.

The gog version of tr2 seems to work well in wine so I may just abandon tr1 and settle for what works.

Thanks to all who replied to this antiquated question  :)   I'll leave this post open for a while just in case someone has a miracle solution.

---

### Post by CharlesA on 2021-06-10
> **lou6 said:**
> I tried several ways of creating an iso (k3b, disks) with no joy - apparently none will copy mixed media cd's.  Also tried the gog version but it will not run in wine. I may yet try the lutris route but, at this point. I'm getting pretty discouraged.

The gog version of tr2 seems to work well in wine so I may just abandon tr1 and settle for what works.

Thanks to all who replied to this antiquated question  :)   I'll leave this post open for a while just in case someone has a miracle solution.

That's good news.

I ended up having to create a bin and cue file from the mixed CD (cuz it has cd audio on it and you can't store that as an ISO) and then convert the bin and cue to an ISO (without the CD audio). The last time I did it was to pull off an installer that I didn't have.

I used the instructions referencing bchunk here: [https://unix.stackexchange.com/questions/29671/how-can-i-convert-a-cue-bin-with-cdr-tracks-image-into-a-single-iso-file](https://unix.stackexchange.com/questions/29671/how-can-i-convert-a-cue-bin-with-cdr-tracks-image-into-a-single-iso-file)

---

