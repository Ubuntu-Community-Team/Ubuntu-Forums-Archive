---
title: "Another Cedega / HL2 thread"
date: 2005-06-15
forum: Gaming &amp; Leisure
---

### Post by Ride Jib on 2005-06-15
Sorry for yet another C/HL2 thread, but a search couldn't help me out any. Hoping someone can shed some new knowledge for me....

I got the cedega .deb file, and installed. I was running low on space on my HD so I made the transgaming drive a symlink to a second hard drive (over 120 GB free space). I ran cedega SteamInstall.exe and all went well. After installation, Steam opened (and I got a good bit excited as I could finally give Winders the boot). Well, I open it up and try to fire up a game. Any attempt to install a game results in the installer getting to "creating local game cache files..." and it just sits there.

It won't do a damn thing.

So, then I say, "hmm... I do have the install cd's" so I pop them in the tray and cedega the setup.exe. The installer comes up and I work my way through it. It gets up to one screen that says "Directx9.0b or greater is needed for this game. Your system already meets this requirement." Ok cool, so I click next. ... nothing. click next next next next... DAMNIT nothing is happening. 

So this is the point I am at now....

Any pointers, things to look at, etc would be greatly appreciated.

**EDIT:  After trying to install after the 6th time, it appears to be going now (from disc). I made it past the Directx screen. I'll update if I encounter any other problems.**

---

### Post by Ride Jib on 2005-06-15
Ok, I cannot get the cd-tray out to put in CD #2.

I've tried running ```
cedega  --monitor-cdrom-eject hl2.exe
``` and also tried the ```
killall -USR2 wineserver
```

Neither of these permit the cd tray to be ejected.

Any tips?

---

### Post by rpgcyco on 2005-06-16
Is it possible for you install the game on your Windows partition, update the game and then copy the GCF files (contained in the SteamApps folder) to wherever you installed it in Linux?

- Rpg Cyco

---

### Post by Ride Jib on 2005-06-16
This is entirely possible.... if I knew how to access the partition of Windows. Hmm.... I'll look into that. Thanks!

---

### Post by rpgcyco on 2005-06-16
Assuming your Windows partition is NTFS, then this may help: [http://www.ubuntuguide.org/#automountntfs](http://www.ubuntuguide.org/#automountntfs)

Info for FAT32 is there as well. :)

- Rpg Cyco

---

### Post by Ride Jib on 2005-06-16
Fantastic! Your help is greatly appreciated!


Too bad this forum doesn't have the "affero" feature that linuxquestions.org has...

---

### Post by Ride Jib on 2005-06-16
Ok, I've got all the files copied over, and just to be safe it wasn't a permissions problem I did ```
chmod 777 *
``` on the contents of the SteamApps directory. Now, when I load Steam and try to "Play Games" the list says "Scanning Steam for updates..." And doesn't seem to do anything beyond this.

---

### Post by Ride Jib on 2005-06-16
Ok, there seems to be some sort of problem with my system. I have tried the isntallation on my laptop, which has (to the best of my knowledge) all the same settings as my desktop, and it worked perfectly. 

Then I tried to ssh into my desktop, and couldn't succeed, but could on the laptop. It appears that maybe a connection is being blocked somehow, although Firestarter shows it being permitted and connected. Then I tried ssh my desktop from the desktop (ssh localhost) and that worked fine. 

Guess I will do a search on that issue and hopefully it will resolve my steam issue as well......

**Edit**... ok I'm just an idiot, ssh is working fine. Still no luck on S[HI]Team

---

### Post by rpgcyco on 2005-06-17
That's odd. I know there was recently problems with CS:S and Cedega, but your problems sound like something more to do with Steam itself. Although, there was recently an update released for the Steam client. Hhhmmm, I dunno man, sorry. :( It's hard for me to provide answers when I haven't had the same problem.

I wish Valve would just bite the bullet and port it to Linux already! Surely there is enough brain power in their ranks for this to happen.

- Rpg Cyco

---

### Post by Ride Jib on 2005-06-17
[QUOTE=rpgcyco]That's odd. I know there was recently problems with CS:S and Cedega, but your problems sound like something more to do with Steam itself. Although, there was recently an update released for the Steam client. Hhhmmm, I dunno man, sorry. :( It's hard for me to provide answers when I haven't had the same problem.
[/QUOTE]

I do appreciate the help!

> I wish Valve would just bite the bullet and port it to Linux already! Surely there is enough brain power in their ranks for this to happen.


Hahah yeah right! DoD:S was supposed to be out back in February. I'm still waiting on that.

---

### Post by rpgcyco on 2005-06-17
> I do appreciate the help!

No problem. :) When I get my new HDD today, I'll move all the files that are eating my free space on this partition, so I will have enough space to try out CS:S and Cedega again. I'll let you know how I go. I will also write down the steps I used. :)

**EDIT:** Ok, I installed Cedega 4.3.2 and Steam last night on two PCs. On mine and on my friends. It works fine in both cases.

All I did was install Steam, exit, copy GCFs, run Steam again and play. I really dunno what could be the problem for you.

Sorry. :(

- Rpg Cyco

---

### Post by WMCoolmon on 2005-07-05
I've been trying to get HL2 working on Linux as well. It installed fine, runs fine, it's just that when it starts, it tells me that it can't do sound because something else is using the device. Esd isn't in the process list, and I switched to ALSA in the ~/.transgaming/config file, although I haven't been able to do the tutorial [here](http://ubuntuforums.org/showthread.php?t=32063) because the package "libesd-alsa0" isn't available for AMD64.

Edit: Well, it does CTD when I try to start a new game, not sure if that's because of sound or not though.

---

### Post by Soulfly on 2005-07-05
I've solved a few Steam upgrade problems by deleting the ClientRegistry.blob (or similar) file in the Steam folder.

---

