---
title: "Load screen stuck at Check Battery State 9.04"
date: 2009-06-21
forum: General Help
---

### Post by Cole7617 on 2009-06-21
Frogive me if there is something in the forums to correct this I just didnt see it.
 
Ok, This is my first time even using Ubuntu so your going to have to treat me like a total newb :D, every thing installed fine along side windows 7, I had no problems at all, all my system drivers worked perfect no driver conflicts or anything, I decided to do a hardware update and found that Nvidia needed an update to 180 not 185. anyway I activated the driver and restarted and now the system hangs on the load screen Check Battery State. Im at a total loss becuse Im a newb so be gentle. 
 
im Running 
Quad Cor 3.9 Ghz (I did load every thing back to stock just incase)
2 8800 GTS' G92
8 GB DDR 1066
2 TB Western D
EVGA 790 SLI
 
 
Im not sure if this is a problem with my SLI or not so I did disable it and try again and had the same problem, again Im a newb Im not sure if there is some command line I need to typ in but did try some things I found in the forum
Tried
sudo dpkg-reconfigure xserver-xorg 
sudo apt-get update (this command fails to get an update) again prolly somethin im doing wrong
"" "" "" "" "" "upgrade

---

### Post by Cole7617 on 2009-06-21
anyone? :popcorn:

---

### Post by Cole7617 on 2009-06-23
> **Cole7617 said:**
> anyone? :popcorn:
 
Wow for a first time user and poster to this forum I guess this dont look at that to good for you.
 
Thanks for the "help"

---

### Post by RJ12 on 2009-06-23
... *removes post*

---

### Post by Cole7617 on 2009-06-23
sorry posted to early

---

### Post by Cole7617 on 2009-06-23
[FONT=Consolas][SIZE=3]---End Quote---[/SIZE][/FONT]
[FONT=Consolas][SIZE=3]Ok thats kinda rude maybe you should wait longer sometimes it can take up to a week becuase people are reaserching your problem so do not even try to say "be gentle on me" Yet you wont be gentle on someone else. You should also try Bumping the thread <---just incase you didnt mean to remove your post :o[/SIZE][/FONT]
 
 
> **Cole7617 said:**
> [COLOR=black][FONT=Verdana]Ah I don’t see that as being rude, what I do see is someone only posting a comment because I say something negative, great when someone see's a post but when they only reply to something negative you said just makes it even look worse, no pun indented on anyone, and I wasn’t trying to be rude, frustrated is more like it and I will say be gentle on me there I just said it? First time user ye I would like to think that I don’t get belittled and spoke to like I know the OS inside and out because I don’t know as much as some of you guys in here. I’m sure plenty of people in here get great help I don’t doubt that, great if someone is researching the problem, why not post a reply like " I'm looking into this" etc I know that’s what I’d say. and for one I do not like bumping posts then you end up knocking someone elses down that need help but if thats let in the forums I will do so, I did not know you can do this.[/FONT][/COLOR]
[COLOR=black][FONT=Verdana][/FONT][/COLOR] 
[COLOR=black][FONT=Verdana]**[SIZE=3]So to anyone else that see's this I was not trying to be rude I’m just a wee bit frustrated :([/SIZE]**[/FONT][/COLOR]

---

### Post by vincencollins on 2009-06-23
I am having a similar issue but now I can't find the Check Battery State message anywhere in the dmesg but I definitely saw this message when I was booting into recovery.  

I am having similar symptoms to this forum post - [http://ubuntuforums.org/showthread.php?t=982621](http://ubuntuforums.org/showthread.php?t=982621)

> 
[   21.571926] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   21.572018] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   21.605652] hda_codec: Unknown model for ALC880, trying auto-probe from BIOS...
[   21.653397] udev: renamed network interface wlan0 to eth1
[  559.321397] lp: driver loaded but no devices found
[  559.419844] apm: BIOS not found.
[  559.548999] Adding 2048276k swap on /dev/sda2.  Priority:-1 extents:1 across:2048276k
[  560.089007] EXT3 FS on sda3, internal journal


Any ideas?

---

### Post by vincencollins on 2009-06-27
Please post your dmesg.  The issue for me was udev, try this out - [https://answers.launchpad.net/ubuntu/+question/75240](https://answers.launchpad.net/ubuntu/+question/75240)

---

