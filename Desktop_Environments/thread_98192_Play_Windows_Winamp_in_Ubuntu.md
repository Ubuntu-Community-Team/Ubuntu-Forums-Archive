---
title: "Play Windows Winamp in Ubuntu"
date: 2005-12-02
forum: Desktop Environments
---

### Post by anil_robo on 2005-12-02
Friends, I just discovered how to run winamp in Ubuntu. I'm amazed it runs!
 
First, make sure you have WINE installed (sudo apt-get install wine)

 1. Winamp was already installed in my windows directory (c:\windows\program files\winamp\winamp.exe)
 2. I [mounted]("http://www.ubuntuguide.org/#windows") the windows partition in Linux
 3. Browsed down to winamp installed in windows NTFS partition
 4. Double  clicked on winamp.exe
5. It runs, but can't play a file as yet. This is because winamp uses the direct sound system as default sound output. click "options-->preferences" from winamp menu, and change sound output to "wave out".
 6. Now press L to load your favorite mp3, and press the play button!
 7. Enjoy the music!
 
 [IMG]http://img204.imageshack.us/my.php?image=winampinlinux1bi.png[/IMG][IMG]http://img244.imageshack.us/img244/2530/winampinlinux9hw.jpg[/IMG]
 [IMG]http://img204.imageshack.us/my.php?image=winampinlinux1bi.png[/IMG]

---

### Post by earobinson on 2005-12-02
I assume you had wine installed all ready? Why not just use xmms also?

NOTE: this will not work, **you need wine or maybe cedaga or some other windows emulator to run windows programs before this would work**

---

### Post by welsh_spud on 2005-12-02
The WINE project never ceases to amaze me. A not for profit organisation managing to re-create the windows API that must have cost billions to make. Wow...

Hang on, you did use wine didn't you...?

---

### Post by Protostar on 2005-12-02
Can you mount an NTFS partition so that you can read AND write from it?

---

### Post by earobinson on 2005-12-02
NTFS read yes
NTFS write is still very unstable as I understand it

---

### Post by AndersAA on 2005-12-02
ntfs write using linux'es ntfs driver is unstable, using captive-ntfs you can mount ntfs using window'ses ntfs drivers (although someone should REALLY port that to fuse, because lufs it's built on is horrible).

---

### Post by anil_robo on 2005-12-02
Yes I  forgot to tell that I had wine installed. Try playing the same song with XMMS and winamp, and you'll know the difference... I feel winamp still plays better than XMMS - dont' know why! If someone can tell me how to make XMMS quality better, that'd be so good!

---

### Post by alpopel on 2005-12-02
in my opinion amarok is much better than winamp! i can't see the the reason changing my mp3-player...

alpopel

---

### Post by arpunk on 2005-12-02
[QUOTE=earobinson]NTFS read yes
NTFS write is still very unstable as I understand it[/QUOTE]
Yes, NTFS write support its been marked as *experimental* and as far as i know it can screw your windows partition (in 2.4 kernels). I havent used it yet, maybe anyone here can tell us how does it work? Theres a new driver in kernels 2.6 (2.6.14 and up) and they support a *save write* for NTFS partitions.

Quoting the linux-ntfs.org site:
> Still read-only, but with safe file overwrite support on all Windows versions without changes to the file size (uncompressed, unencrypted, nonsparse files only).
And
> One can setup a loopback device on an NTFS file. [TopologiLinux]("http://topologi-linux.sourceforge.net/index.php") and others use this feature to run Linux from a Windows NTFS partition with full read-write support.

---

### Post by MethodOne on 2005-12-02
anil_robo, what version of WINE did you use?

---

### Post by anil_robo on 2005-12-02
I don't know which version of wine did I use, but when I type wine in a terminal, it reads 

```
Wine 20050725
```

By the way, I've been playing some of my favorite songs on both winamp and amarok for the last one hour, and still I can feel winamp is giving me better sound quality. Amarok is definitely a good player, but winamp wins the race when it comes to pleasing my ears. However, I shall use amarok only, because winamp has some problems with display - the skin of winamp garbles occasionally when I move my mouse over it.

Doesn't amarok have some plugins etc. whereby I can enhance sound quality?

---

### Post by elreteipos on 2007-10-14
Just tried installing Winamp on Linux. Everything works fine, except when I try to play some music:

[img]http://img155.imageshack.us/img155/9458/errornn5.jpg[/img]

Note: that Dutch error message translates as> The specified format cannot be translated or supported. Use the Capabilities function to view supported formats.

What does this mean? How can I fix this?

---

### Post by RueHabergeon on 2008-03-21
I cant get winamp to play cds. The cd-rom folder shows up as empty. Whats up with that?

---

### Post by TenPlus1 on 2008-03-21
Try using Audacious on the Ubuntu side, this is a far newer re-make of Xmms with all new plugins, controls, codecs, filters etc and sounds pretty damn kewl...

---

### Post by BLTicklemonster on 2008-03-21
Cool! I can use the classiic and modern skins, but not the new bentoo or whatever it's called. I want to listen to the winamp Xradio streaming radio in winamp, can I do this from the modern skin? Actually, I want my wife to see that this can be done, as I use exaile normally, but if she saw winamp running in ubuntu, she'd get a wrinkle started in her frontal lobe, and start thinking perhaps Ubuntu wasn't just some freak software I play with, but an actuall honest to God Operating System.

---

### Post by dantakeoff on 2008-07-19
strange. im new to ubuntu, but all i did to get winamp to work was simply download winamp to my ubunto desktop and install it with wine, works perfectly, no tricks. im running the newest version of ubuntu...my problem was i couldnt get Audacios to work, it would load the files but wouldnt play them, besides, i like winamps no-nonsense aproach and simple layout. it takes about five seconds to load, but thats nothing new. also, i deselected alot of the install options like winamp agent and the other ******** optional install options. just try it, you got nothing to lose, and can always delete it if it doesnt work.
i cant get the plugins to work though, gforce and other visualization plugins cant operate without directx i guess... anybody tried it with Crossover?

---

### Post by BLTicklemonster on 2008-07-19
!!! The latest version of Winamp? Can you listen to online streaming audio music station thingies with it/

---

