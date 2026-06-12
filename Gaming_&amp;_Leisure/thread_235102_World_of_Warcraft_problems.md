---
title: "World of Warcraft problems"
date: 2006-08-12
forum: Gaming &amp; Leisure
---

### Post by YetiHunter on 2006-08-12
Hi,
I have some problems with my WoW running on wine.
I'm running kubuntu dapper-drake. I use wine 0.9.18 with the wow-patch ([https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft)). 

My system:
AMD Athlon XP 2600+
MSI NVidia 6600 gt agp-version

1.Problem:
  I have sound, but it isn't very clear. I think I have to increase the sound-buffer, i've read about this problem somewhere around here, but i wasn't able to find the post anymore and I couldn't remember the command.

2.Problem:
  When I change things in the /wtf/config.wtf file, and I start wow the hole file is reset to how it is after instalation.

3.Problem:
 Well I think pictures say more than words ;)

---

### Post by Sammi on 2006-08-12
I'm sorry I can't help you, but my god those are some scary pictures. Glad I'm not experiencing that problem :)

---

### Post by AngryKidJoe on 2006-08-13
run 
```
wine WoW.exe -opengl
```

Don't click reload default settings, ever.

---

### Post by YetiHunter on 2006-08-13
> Don't click reload default settings, ever.
I haven't used this button since I play wow.

I start wow with -opengl but the settings are reset everytime i start wow. And I think I have those problems, because wow starts without the SET gxApi "opengl" attribute which is in the config.wtf.

---

### Post by eqisow on 2006-08-13
OK, first things first, make sure the following three lines are in your Config.wtf. 

```
SET SoundOutputSystem "1"
SET SoundBufferSize "100"
SET gxApi "OpenGL"
```

After that, change your Config.WTF file to read only.

```
chmod 555 '~/.wine/drive_c/Program Files/World of Warcraft/WTF/Config.wtf'
```

The only problem with this solution is that you will have to change Config.wtf to read/write and edit it manually to effect any changes. To make it read/write again use the previous command but change 555 to 755. Be sure to change it back to read only when you are done!

Also, here's my [Config.wtf]("http://thepiratecove.org/files/Config.wtf") for you to use as a reference for changing other stuff in yours.

---

### Post by YetiHunter on 2006-08-13
Hmm that didn't work. I think perhaps it doesn't work because my wow lies on my old windows fat32 partition, or is that all the same?

---

### Post by eqisow on 2006-08-13
Yes, Yetihunter, that's why it dind't work. Fat32 doesn't have file permisions like ext3, Reiser, etc. You could try copying over the files reinstalling in an ext3 partition. Other than that, I'm not sure what to tell you.

---

### Post by YetiHunter on 2006-08-14
Ok thank you. I didn't know that. But there is the next problem. I've never thougt that I would use linux for gaming so the partition is too small. Is there a way resizing the partition? My partition is raiserfs is that helps.

---

### Post by eqisow on 2006-08-14
It depends on how your HD is partitioned out. You'll only be able to grow your partition out to the right, not left. So if it's the last partition, then no. You could still shrink another partition and make a new one, however.

To resize your partition it will have to be unmounted, which basically means doing it either from Windows or from a live CD such as Knoppix.

---

### Post by YetiHunter on 2006-08-14
Do you know a programm or something how I can look how my partitons are arranged?

---

### Post by nsteussy on 2006-08-14
I have WoW running under Transgaming's Cedega emulator ( a fork from a BSD licensed early version of Wine).  It works very well, and is more stable than my Windows install.

duke out

---

### Post by eqisow on 2006-08-14
Install GParted on Gnome, or QTParted on KDE. Partition magic will also do it under Windows.

---

### Post by YetiHunter on 2006-08-14
Hmm well my linux partiton is at the end of the harddisk. Wouldn't it be enought to create another ext3 or raiser partition somewhere on the harddisk where I would copy wow to?

---

### Post by ReaperManzz on 2006-08-14
As long as I understand the question, you should be able to type fdisk $hardDrive

Example: If your hard drive is located in the primary IDE and is Master, then "fdisk /dev/hda", then hit p to print out the partition table.  If Primary Slave - hdb;

Note - Be very careful in that application, I'm not sure how much you know about it, but it could wipe out your entire partition table.

---

### Post by ReaperManzz on 2006-08-14
Uhh...Sorry, Please disregard my previous message, I didnt realize there was a second page.

---

### Post by YetiHunter on 2006-08-14
No problem. =)

---

### Post by eqisow on 2006-08-14
If you create a new ext3 or reiser partition you can simply set up your fstab to have it mount to a convenient location, for example you could have it mount at '~/.wine/drive_c/Program Files/World of Warcraft', which is where Wine normally would install it to.

---

### Post by YetiHunter on 2006-08-15
Ok I've made a new Partition (raiserfs) and copied my wow there. Then I've set the permissions and started wow with opengl. These graphical problems are gone except that some people are totaly white but that's not so bad. But everytime I start wow I have to change my settings again although the config.wtf doesn't change. So it shows me on every startup the EULA and these things.

Here is my config.wtf:

---

### Post by AngryKidJoe on 2006-08-15
When you load up WoW, does it ask to reload the default settings? Do you click yes? If so, don't do that anymore.

---

### Post by YetiHunter on 2006-08-15
No, it doesn't ask me to reload the settings.

---

### Post by AngryKidJoe on 2006-08-15
Sorry, I posted quite late. The screen took forever to load and jetted straight to the bottom of the thread.

Anyway, if all else fails - get a small harddrive that'll fit WoW on it. Could save a load of trouble.

---

### Post by YetiHunter on 2006-08-15
Well my WoW is alone on a raiserfs partition at the moment.

---

### Post by Mooie on 2006-08-17
I have that EXACT same gfx problem (w/ the pointy buildings), but only when I run the game with wine in directx. when I run it with wine in opengl, when the game should load, it just quits w/ an error in my post [http://ubuntuforums.org/showthread.php?p=1390671#post1390671](http://ubuntuforums.org/showthread.php?p=1390671#post1390671)
when I run the game from the exact same file with cedega (its in my cedega c drive) it works flawlessly in opengl and in directx. can anybody offer any help? thanks

---

### Post by zzottt on 2006-08-17
can any of you smrt guys help me with my wow problem?


[http://www.ubuntuforums.org/showthread.php?t=238007](http://www.ubuntuforums.org/showthread.php?t=238007)

---

### Post by DJRockoBobo on 2006-08-18
I've had the same problem.....but if u can't get it working with -opengl then go into the directory you've installed the game in and then type the next command:

wine WoW.exe -d3d

After that just change some video settings and come back with -opengl

---

### Post by Mooie on 2006-08-18
My error in opengl was caused by the way that the minimap is rendered in buildings, when I got a mod to hide it when I log in, opengl worked fine.  could sombody help w/ the gfx in d3d? there is no minimap problem w/ the game in d3d...](*,)thanks

---

