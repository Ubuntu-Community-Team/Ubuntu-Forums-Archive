---
title: "Plan for ditching Windows XP, assist?"
date: 2005-07-25
forum: Gaming &amp; Leisure
---

### Post by blueturtl on 2005-07-25
I've been reading reviews about Cedega and it made me consider my current dual boot situation once again. Right now Half-Life 2 and a few other games are the only reason to ever boot Windows, so I reasoned myself, I could get the bastard completely off my hard-disk if I get Cedega. There are only a few issues I had to comfront first:

**1. Will Cedega succesfully run my games?**
Looking at their checklist all my games (Half-Life2, WarCraft III, Homeworld, No One Lives Forever and Unreal/Unreal Tournament) seem to be well supported, so 15 euros compared to a Windows XP license is well justified.

**2. Will my hardware be capable/supported in Linux?**
All I can say is Ubuntu was very easy to configure. My (now foregone) SoundBlaster Live! 24-bit was giving it the hiccups propably because it was such a new card. I switched to an older version of Live! and now everything works perfectly, including hardware accelerated graphics (gotta love NVIDIA for their driver support). Shouldn't be a problem.

**3. How do I rearrange my current setup without messing either Windows or Ubuntu?**
I have two hard-disks, 120 gigabyte one, and a 40 gigabyte secondary. My initial idea was to partition the 120 gig disk for Windows (since all the really space hogging things, aka games) would reside on this disk. This left my Ubuntu setup and personal files with 40 gigs of space which was just fine at the time. Also having heard Windows wouldn't boot from a secondary drive and knowing I didn't want to have both operating systems on the same hard-disk I came to the conclusion this was the only way. Now I have to accomplish the following:

[list]
[*]Re-partition the primary 120Gb disk so that by removing the extended NTFS partition I can dedicate more space to my /home for personal files and intended game installs. This would leave the Windows install on the primary partition still intact "in case".
[*]Subscribe to Transgaming and install Cedega & Point2Play.
[/list] 

Only one of the two is a problem: I have no idea how to manage partitions in Linux (although I did configure them manually during the Ubuntu installation). I also hate the idea of possibly erasing Grub by accident. Also, is it even possible to mount /home to two different partitions on separate disks? Could somebody possibly assist me by guiding me through? Would be greatly appreciated.

My hardware in case required:
AMD AthlonXP 2200+ (1800MHz) CPU, ASUS A7V333 mobo, 1 Gb RAM, dual Seagate HDs: 120Gb, 40 Gb, Gainward Geforce4 Ti4200 Golden Sample, LG dual-layer DVD burner and SoundBlaster Live! 1024

---

### Post by Perfect Storm on 2005-07-25
Always a good Idea is to have boot (grub) on a serperated partition /boot make sure that you set boot flag "on" this partitition. Then the chance to mess it up minimized.

Mine looks like this on my 240 gb :


Partitition...........| Filesystem ...|......Size | 
---------------------------------------------------------------------
/dev/hda1..................ext2...............70 mb..../boot  
/dev/hda2...............extended
....../dev/hda5............ext3................80 gb..../
....../dev/hda8............ext3..............160 gb..../home
....../dev/hda7............ext3..................1 gb..../tmp
....../dev/hda6.........linux swap.......600 mb....Swap area

You can use Gparted to edit your partition, but beware it's easy to mess up stuff ;)

---

### Post by Perfect Storm on 2005-07-25
> Only one of the two is a problem: I have no idea how to manage partitions in Linux (although I did configure them manually during the Ubuntu installation). I also hate the idea of possibly erasing Grub by accident. Also, is it even possible to mount /home to two different partitions on separate disks? Could somebody possibly assist me by guiding me through? Would be greatly appreciated.


yes it's possible. check what's the seperated /home hard-drive is called open it a terminal and mount /dev/***
reboot
when the login screen appears write the account name which is  on the seperated hard-drive and password.
Well It's what I have done...but sure someone perhaps have a better way :)

---

### Post by blueturtl on 2005-07-25
My configuration looks like this:

hda:

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2611    20972826    7  HPFS/NTFS
/dev/hda2            2612       14592    96237382+   f  W95 Ext'd (LBA)
/dev/hda5            2612        7833    41945683+   7  HPFS/NTFS
/dev/hda6            7834       14360    52428096    7  HPFS/NTFS
/dev/hda7           14361       14592     1863508+   b  W95 FAT32

hdb:

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1         809     6498261   83  Linux
/dev/hdb2             810        4865    32579820    5  Extended
/dev/hdb5             810         933      995998+  82  Linux swap / Solaris
/dev/hdb6             934        4865    31583758+  83  Linux

/dev/hdb6 currently holds my /home

I would like to remove all but the the primary partition on hda and create an ext3 partition on it. Then mount it together with hdb6 as /home. Is this possible? Will Grub be erased if the partition table of hda is rewritten? Is Grub even located on hda?

edit: Or would it be possible for me to mount the new filesystem as something other than /home and still have it dedicated to user files? Like /mnt/hda or something?

---

### Post by Gnobody on 2005-07-25
Warcraft III will run great in Cedega. Homeworld, UT, UT2003, UT2004 and Unreal all have native Linux clients so you'd be better to run them without using Cedega.  Half-life 2 and Counterstrike: Source work pretty good now in Cedega (especially in DX8 mode) the only thing is the fonts may be a little messed at certain resolutions.  So your games should all work great, although I am not familar with running No One Lives Forever 2 in Linux.

With your 1GB of ram you shouldn't really need a swap partition it will only slow your machine down.  You will really only need a root partition and the Ubuntu installer will create this for you. Since you already have Ubuntu installed: sudo apt-get install gparted <--- This will download and install you a great partition manager similar to Partition Magic on Windows. It will allow to remove your Windows partition and grow an existing partition, or enable you to create a new one with the free space.

---

### Post by blueturtl on 2005-07-25
My current plan of action is this after some more research:

[list]
[*]Backup patches and saved games from /dev/hda6 to CD-RW
[*]Remove all but the primary NTFS partition and create a new large EXT3 partition with cfdisk
[*]Format the disk using the sudo mkfs.ext3 /dev/hdaX
[*]Mount the new partition in /etc/fstab as /mnt/shared
[/list]

Is there something I should know concerning read/write rights?
This is because when I manually mount a FAT32 partition for temporary use (for transferring files between operating systems) it seems only the root user has writing privledges despite how I use the chmod command to try and give everyone equal rights. Naturally this cannot be if I'm to use the bigger hard-disk as data storage in Ubuntu.

What about these native clients mentioned? I tried searching Google for one for Homeworld, but the search didn't really turn up anything useful.

DOSBox for the golden oldies, Cedega for new Windows games, that's the plan thus far...

---

### Post by Perfect Storm on 2005-07-25
I havn't any luck with Homeworld to run in Cedega (well, it's choppy...perhaps I should try fine adjust the settings), but Homeworld 2 works out of the box with cedega.

---

### Post by blueturtl on 2005-07-26
While backupping files I've studied some more and come across this:

There is a ptrace bug in 2.6.9 and 2.6.10 kernels that I hear causes problems with copy protection that lead to Cedega not working, or not working fully. Sounds like something to worry about as Hoary is built around 2.6.10... Ubuntu has applied some patches to this kernel, but I don't know if they've fixed this one. Mailed Transgaming to ask for their status on 2.6.10 or Ubuntu...  :-? 

Installed Gparted, seems able enough to replace cfdisk in my plans.

Proceeding as planned...

---

### Post by blueturtl on 2005-07-31
Resumed project after a slight break from the computer.

GParted rocks! This baby let me do my partitioning in an extremely simple fashion, I had no problems whatsoever! A little editing of the /etc/fstab and now I have an external /mnt/shared_hd to use for extra storage.

Transgaming has not answered my inquiry, so I assume I won't have any problems (could be risky, but it's only 15 euros.. could be worse). I will subscribe to them very soon to start the whole gaming experiment (still have to arrange some files now that I have a new partition at my disposal).  \\:D/

---

### Post by blueturtl on 2005-08-07
\\:D/  I got my subscription yesterday. Downloaded and installed Point2Play. Ran WarCraft III. It was as easy as that! I'm very impressed indeed. I'll post some more results as I try different games.

---

### Post by artinla on 2005-08-07
I can help with an answer your question concerning 2.6.10 kernel and copy protection.

As far as I know, it is still a problem.  I have experienced it a couple of times, but have never found a fix.  I think that 2.6.11 is fixed but I have not tried it.

It will only affect a very limited number of games, because it is a specific copy protection scheme that has the problem.  I know that Doom3 Resurrection of Evil will only run if you have a legit copy of the game and the original CD.


Art

---

### Post by evilghost on 2005-08-07
The Sound Blaster Live 24bit is a piece of trash.  The card, despite Creative's best efforts to trick the consumer into believing it's a great card, **does not support hardware mixing**.  The Sound Blaster Live 5.1 you have uses the emu10k1 chipset; capable of hardware mixing and huge leaps in performance.

See [http://klumpp.net/blog/archives/22-Linux-Soundcards-CA0106-sucks,-EMU10k1k2-is-the-way-to-go..html](http://klumpp.net/blog/archives/22-Linux-Soundcards-CA0106-sucks,-EMU10k1k2-is-the-way-to-go..html) for more details on why the Sound Blaster Live 24Bit/CA0106 is trash.

I've got an openal.so built for UT2004 that has been optimized for the emu10k1 cards.  Here is the URL/Tweak-guide for UT2004:
[http://ubuntuforums.org/showthread.php?t=49329&highlight=howto](http://ubuntuforums.org/showthread.php?t=49329&highlight=howto) and focus on [http://ubuntuforums.org/showthread.php?p=257782](http://ubuntuforums.org/showthread.php?p=257782) for your openal.so optimized for the emu10k1.

I hope you have an NVIDIA card, as they are quite more robust under Linux than ATI.

---

### Post by blueturtl on 2005-08-08
> The Sound Blaster Live 24bit is a piece of trash. The card, despite Creative's best efforts to trick the consumer into believing it's a great card, does not support hardware mixing. The Sound Blaster Live 5.1 you have uses the emu10k1 chipset; capable of hardware mixing and huge leaps in performance.

This is what I heard, and I switched to my old SoundBlaster Live! 1024 (not 5.1 unfortunately). I don't know if the older Live! cards support hardware mixing, but atleast it's directly supported by Ubuntu, unlike Live! 24-bit...

> I can help with an answer your question concerning 2.6.10 kernel and copy protection.

As far as I know, it is still a problem. I have experienced it a couple of times, but have never found a fix. I think that 2.6.11 is fixed but I have not tried it.

It will only affect a very limited number of games, because it is a specific copy protection scheme that has the problem.

Well I was afraid I wouldn't get my games to install, but so far I've had no problems so maybe none of my games use this spesific copy protection then? Or is this only related to copied discs? All my games are genuine...

I'm currently in the process getting HL2 to work. It installed nicely through Steam and even runs fast, the problem is it keeps resetting my graphics settings to low every time I run it which is really annoying. 640x480 with low texture quality and DirectX 7 level pixel shaders isn't the best my system can do, so I've been looking into the startup parameters for the game and have so far come up with a way to fix the hardware DirectX level, and the resolution, however I don't know if I can set the texture quality before running the game... Experimenting continues. I started with HL2 because I suspect out of the games I have it has to be the toughest to configure to run under Linux...

> I hope you have an NVIDIA card, as they are quite more robust under Linux than ATI. 

I have a Gainward GeForce4 PowerPack Ti4200 Golden Sample.
I actually thought at some point I would rather own an ATI card, but after switching to Linux I can't really say I'm sorry I have NVIDIA.  ;-)

---

### Post by blueturtl on 2005-08-08
My experiments so far have lead to the following results:

**Half-Life 2**
Graphics: refuses to remember settings, low texture quality and resolution by default, buggy
Sound: Good
Speed: Framerates below that of Windows

**Max Payne**
Graphics: Excellent
Sound: Excellent
Speed: Excellent

**StarCraft**
Graphics: Very good
Sound: Excellent
Speed: minor lag when scrolling around

**WarCraft III / Frozen Throne**
Graphics: Excellent
Sound: Excellent
Speed: Excellent

**Homeworld**
Graphics: Excellent
Sound: stutter and clipping
Speed: Excellent

**Unreal**
Failed to run

**No One Lives Forever**
Graphics: Minor bugs during loading
Sound: No music
Speed: Playable at 640x480

I'm going to try a few others and then see if I can fix the ones that don't work...

---

### Post by artinla on 2005-08-08
What version of Unreal?  UT, UT2003 and 2004 all run perfectly under Ubuntu for me.

The original Unreal.. well I don't know if it will work or not.

As for HL2, It runs fine also..  Maybe your permissions are incorrect for the config folder?  Maybe advanced settings in P2P such as shading or Windows emulation type? Hmm.. I am also running an old sblive, (not the 24 bit) so that isn't the trouble..  

Expect it to be about 70% as fast as the win32 setup.

I know that for UT series games, there are some entries that have to be made in the UTxxxx.ini file regarding graphics..  Let me know what version you have and I will try to find the info for you.  I don't have an ATI card, so I can't say whether that works OK or not.


Art

---

### Post by evilghost on 2005-08-08
Your SoundBlaster Live 1024 supports hardware mixing, because it's running on the EMU10k1 chipset.

You can easily tell by doing in a terminal:

lsmod|grep -i emu10k1

Example output (my system, using a Live 1024):
```

luser@400sc:~$ lsmod|grep -i emu10k1
emu10k1_gp              3872  0
gameport                4864  2 analog,emu10k1_gp
snd_emu10k1            98532  3
snd_rawmidi            25024  1 snd_emu10k1
snd_seq_device          8716  2 snd_emu10k1,snd_rawmidi
snd_ac97_codec         74336  1 snd_emu10k1
snd_pcm                95780  4 snd_emu10k1,snd_ac97_codec,snd_pcm_oss
snd_page_alloc          9988  2 snd_emu10k1,snd_pcm
snd_util_mem            4640  1 snd_emu10k1
snd_hwdep               9700  1 snd_emu10k1
snd                    56580  14 snd_emu10k1,snd_rawmidi,snd_seq_device,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer,snd_hwdep
luser@400sc:~$

```

I've got UT2004 running, what version, and more specifically, what's the problem?

You do understand that Cedega is not a cure-all, and it's **much** better to run a game using it's native Linux port than using a Cedega D3D->OpenGL emulation/translation method right?

Natively, you should see full speed if not faster frame-rates that in Windows.  Using Cedega, you see about 70% of what you would see in Windows due to the emulation overhead.

Either way, we're all here to help so be sure to cite specifics so we can help you out.

---

### Post by blueturtl on 2005-08-09
> You do understand that Cedega is not a cure-all, and it's much better to run a game using it's native Linux port than using a Cedega D3D->OpenGL emulation/translation method right?

Natively, you should see full speed if not faster frame-rates that in Windows. Using Cedega, you see about 70% of what you would see in Windows due to the emulation overhead.

I know. Every game I get to run in Linux I just consider one less reason to boot Windows. If so happens that Half-Life2 remains more playable in Windows then so be it, but some games no longer require me to boot and so I will have won in this no matter what.  ;-)

Concerning emulation (which I suppose WINE doesn't really do, or atleast that's how I understand it).. so far the only games to run slower in Linux than in Windows are those that are heavily built around Direct3D such as NOLF or HL2. OpenGL based games like WarCraft III and Homeworld run with all around perfect framerates. Max Payne runs well but I suspect it's because my machine is quite overpowered for it.

> What version of Unreal? UT, UT2003 and 2004 all run perfectly under Ubuntu for me.

The original Unreal.. well I don't know if it will work or not.

*Embarrassed* I was actually trying to run the original Unreal (226F).
It's not the best game, but it holds some memories, and with a working OpenGL patch I know it should run without any overhead issues. Surprisingly though, the game won't even boot. I have no idea what could cause this. It's a relatively easy game to emulate, it doesn't require a disc in the drive, it runs in software mode and has adjustable OpenGL settings. I'll have to look into it. Don't know about a native port for this game, but if there is a working one drop a link.

> **Homeworld**
Graphics: Excellent
Sound: stutter and clipping
Speed: Excellent

This is an odd bug I think, the game runs so fast the sound stutter cannot be a performance issue, therefore I assumed it has something to do with a buggy DirectSound implemention in Cedega and tried different settings: switching to ALSA or enabling MMap doesn't seem to do anything so I then looked into the original game's documentation and discovered this: I can feed the game options through the shortcut used to launch it. Among the options is /waveout (disables DSound, slower but should be more compatible). Unfortunately looking into the fake Windows dir I didn't find any shorcut files to edit. Is there a way to pass the game these parameters through Cedega?

I know there is a port of this game for Linux, but it seems to still be in it's Alpha stages and fairly unstable.

---

### Post by blueturtl on 2005-08-31
Ok, time for a status update. It's been a while and I've been working a bit to find out if I can squeeze any more out of my subscription and here's what so far:

**Half-Life 2**
Graphics: Good.
Sound: Excellent
Speed: Playable
note: DirectX 8 is not supported for HL2 on Geforce4 cards under Cedega. DirectX 7 level graphics don't bring out the best in HL2, but at least there seem to be no bugs.

**Max Payne** 
Graphics: Excellent!
Sound: Excellent!
Speed: Excellent (outperforms Windows)!

**StarCraft**
Graphics: Excellent!
Sound: Excellent!
Speed: Excellent (outperforms Windows)!
note: disabling Accelerated InterProcess Communication fixed lag!

**WarCraft III / Frozen Throne**
Graphics: Excellent!
Sound: Excellent!
Speed: Excellent (outperforms Windows)!

**Unreal**
Graphics: Excellent!
Sound: Excellent!
Speed: Excellent (outperforms Windows)!
note: has to be installed under C:\Unreal to work

**No One Lives Forever**
Graphics: Excellent!
Sound: No music
Speed: Slowwwwwww
note: In-game music based around midi, does not work. Game horrendously slow, only playable at 640x480 and still leaves frames to be desired.

**Resident Evil, Resident Evil2**
Install but cannot play (some MCI open error).

**King's Quest VIII: Mask of Eternity**
Installs but cannor play

Games tried using native ports:

**Unreal Tournament**
Installs and runs great. Only the music seems to clip from time to time.

**Homeworld**
Refuses to switch into OpenGL mode so the game doesn't run. :(

All in all out of my 11 games 7 can be played under Linux. I'm also discluding older games that run under DOSemu and DOSbox here, so all in all not a bad trade.
TransGaming tech support has helped me solve two problems that have turned games from unplayable to perfectly running! In this light I guess the tables could still turn greatly, especially if the next Cedega update improves DirectX support both upward and downward from 7.0.   :)

---

### Post by Perfect Storm on 2005-08-31
I got similiar results like you :). Though I have diffrent hardware. If you like homeworld and can't get it to run wih cedega (I can't either), go for homeworld 2. It runs without any problems without glitch and bugs.

---

### Post by blueturtl on 2005-11-08
Cedega 5.0 is out and I still have an active subscription (for a few days anyway). Just installed it a while ago and I'm getting excited already; they've fixed Homeworld! Yay. Post back later for more results... Oh, and since I finished HL2 some time ago, XP has already been given the boot. :P

---

### Post by sevenrechlin on 2005-11-11
All I gotta say is if they have full support for CSS I'm sold.  That was my biggest fear when moving to linux :p.

---

