---
title: "Unreal Tournament 2004 question"
date: 2006-12-25
forum: Gaming &amp; Leisure
---

### Post by Zeikcied on 2006-12-25
I just got Unreal Tournament 2004 Editors Choice Edition for Christmas.  Imagine my shock when I find there is no Linux installer.  I primarily wanted this game because it gives me a game to play on Linux, instead of having to boot to WinXP every time I want to play something.

Now, I looked at TuxGames.com, and they want $40 for the game.  I want to look a bit lower (seeing as how the ECE edition was $10).  So, if I were to look at Amazon.com, or a similar website, which versions have a Linux installer?

I thought all the Windows discs had the Linux installer on them.  But I guess I got the one version that doesn't :(

---

### Post by MetalMusicAddict on 2006-12-25
I know my regular version had a linux installer on the last disk. Ive heard the ECE doesnt have this though.

---

### Post by Spent Casing on 2006-12-26
Go [HERE](http://liflg.org/?catid=6&gameid=17) to download the UT2004 linux installer plus updates and some mods.

But just downloading [ut2004.megapack-english-2.run ](http://liflg.org/?what=dl&catid=6&gameid=17&filename=ut2004.megapack-english-2.run) is all you need to get the base game installed.

---

### Post by Zeikcied on 2006-12-26
> **Spent Casing said:**
> Go [HERE](http://liflg.org/?catid=6&gameid=17) to download the UT2004 linux installer plus updates and some mods.

But just downloading [ut2004.megapack-english-2.run ](http://liflg.org/?what=dl&catid=6&gameid=17&filename=ut2004.megapack-english-2.run) is all you need to get the base game installed.
I downloaded that file, and I tried executing it, and it says that I need Unreal Tournament 2004 installed first, which doesn't make sense to me.  I tried again with the DVD in the drive, and that didn't work either.  I did the "export" thing described in the FAQ, and that didn't help.

Please tell me what I'm supposed to do here.  I'm lost, and a relative newbie, too.  I've been able to find out some things, but this isn't making sense to me.

---

### Post by Spent Casing on 2006-12-26
I just used that installer to reinstall ut2004 last week.  I have the original CD version, but that shouldn't make a difference.  I installed it by:

```
sudo sh ut2004.megapack-english-2.run
```

It unpacks, then asks you to insert the first CD.  If there are any remains of a previous install, it will try to update to the lastest version.

---

### Post by Zeikcied on 2006-12-26
> **Spent Casing said:**
> I just used that installer to reinstall ut2004 last week.  I have the original CD version, but that shouldn't make a difference.  I installed it by:

```
sudo sh ut2004.megapack-english-2.run
```

It unpacks, then asks you to insert the first CD.  If there are any remains of a previous install, it will try to update to the lastest version.
My problem is that it doesn't ask for a CD.  It just tells me that I need to have UT2K4 installed before I run that installer.  So...I'm just lost.

---

### Post by Spent Casing on 2006-12-26
Ok, lets try this.  I just uploaded the linux installer off my CD to my web site.  You can download it [HERE](http://www.clan-noquarter.net/files/utinstaller.zip).

Now that I think about it, this is what I may have used...my bad..](*,) Its for the CD version, but lets hope it works for you.

---

### Post by Zeikcied on 2006-12-26
> **Spent Casing said:**
> Ok, lets try this.  I just uploaded the linux installer off my CD to my web site.  You can download it [HERE](http://www.clan-noquarter.net/files/utinstaller.zip).

Now that I think about it, this is what I may have used...my bad..](*,) Its for the CD version, but lets hope it works for you.
Ok, I'm going to try it.  But, are you sure it will work when it isn't in the root directory of the CD/DVD?

Edit:  Ok, I tried it.  But it asks me to mount disc two.  I don't have a disc two.  I believe the data on the CD version of disc two is in a directory on the DVD, and it isn't in an ISO form, so I can't insert or mount it.

---

### Post by Spent Casing on 2006-12-26
I did some searching and this is all I could find [HOW-TO: Install UT2k4 Editor's Choice Ed DVD with no linux-installer.sh on Linux](http://utforums.epicgames.com/showthread.php?t=554966).  I don't really consider this a solution since it involves windows, plus it isn't very indepth.  If we can just find the installer for the normal DVD version, your DVD can be installed and the megapack could be used to update to the Editors Choice edition.  Seems pretty idiotic to not include the install on only that version.


EDIT, ok I found this translated from german. [How To](http://translate.google.com/translate?hl=en&sl=de&u=http://www.ubuntu-gaming.de/thread.php%3Fgoto%3Dlastpost%26threadid%3D687%26sid%3D8f9e9b7da11b9680f04fc85e5c46f283&sa=X&oi=translate&resnum=4&ct=result&prev=/search%3Fq%3Dut2004%2Bdvd%2Blinux-installer.sh%2Bdownload%26start%3D10%26hl%3Den%26lr%3D%26client%3Dfirefox-a%26rls%3Dcom.ubuntu:en-US:official%26hs%3D3vK%26sa%3DN). It explains how to install the ECE version without using windows.

---

### Post by Patrick-Ruff on 2006-12-26
you can always download a new UT2k4 CD and burn it.

---

### Post by Zeikcied on 2006-12-26
> **Spent Casing said:**
> I did some searching and this is all I could find [HOW-TO: Install UT2k4 Editor's Choice Ed DVD with no linux-installer.sh on Linux](http://utforums.epicgames.com/showthread.php?t=554966).  I don't really consider this a solution since it involves windows, plus it isn't very indepth.  If we can just find the installer for the normal DVD version, your DVD can be installed and the megapack could be used to update to the Editors Choice edition.  Seems pretty idiotic to not include the install on only that version.


EDIT, ok I found this translated from german. [How To](http://translate.google.com/translate?hl=en&sl=de&u=http://www.ubuntu-gaming.de/thread.php%3Fgoto%3Dlastpost%26threadid%3D687%26sid%3D8f9e9b7da11b9680f04fc85e5c46f283&sa=X&oi=translate&resnum=4&ct=result&prev=/search%3Fq%3Dut2004%2Bdvd%2Blinux-installer.sh%2Bdownload%26start%3D10%26hl%3Den%26lr%3D%26client%3Dfirefox-a%26rls%3Dcom.ubuntu:en-US:official%26hs%3D3vK%26sa%3DN). It explains how to install the ECE version without using windows.
The Google translation is quite confusing in certain parts.

But I thank you for searching for me.  Maybe I can find a guide in English.

---

### Post by terryroe on 2006-12-31
I got the ECE DVD about a year ago.  It has a linux-installer.sh file in the root of the DVD and it worked for me.  I forget how I had to run it as I'm back on Windows right now.

I went back to Windows because, among other reasons, I couldn't get UT to perform as well.  I'm doing research for ideas on how to make UT perform properly under Linux/Ubuntu in the hopes that I can return to using Ubuntu in the near future.

TR

---

### Post by Zeikcied on 2006-12-31
Well, I've finally gotten around to attempting the translated How-To.

Things work well enough, but there are some big issues.

First, it only said it extracted around 1666 files, when the How-To says it should extract 1805.  I thought that might just have been due to different languages being included in different versions.

But, the folder names are all wrong.  I have folder names like *All_Benchmark*, *All_Feedback*, and *All_UT2004.EXE*.  I also do not have any System folder.

Some other folders have an underscore as the first character, and while that may be intentional, it looks a bit odd.

For some reason, I think I'm missing something major, and the unshield program doesn't seem to be creating folders with the right names.  Does anyone have any clue as to what I'm doing wrong?

I have data1.cab, data1.hdr, data2.cab, data3.cab, data4.cab, data5.cab, and data6.cab in the ut2k4_cabs folder, unshield improperly names the folders, and I'm missing a large chunk of files.

---

### Post by diepruis on 2007-01-01
Sounds to me like you got the Unreal Anthology and not the UT2004 ECE.

---

### Post by Zeikcied on 2007-01-01
> **diepruis said:**
> Sounds to me like you got the Unreal Anthology and not the UT2004 ECE.
No...It's UT2004 ECE.  It's from Gamestop, and it is just the UT2K4 box, and no other Unreal games.  It's also the version published by Midway (since Atari lost the Unreal publishing deal).  But, it says on the cover "Includes Editor's Choice and Mega Bonus Pack!"  So...I'm assuming it's the ECE.  It doesn't have any Linux installer, anyway.

I have a dual-boot system, so should I just install it on Windows and then copy the files over to Linux, then apply whatever Linux patches?  I think that'd be easier than the networked computer method mentioned earlier.  And faster.

---

### Post by diepruis on 2007-01-02
You could do what I did and borrow a friends copy of UT2004 that has the installer on and install from that. Just use your CDKEY.

---

### Post by handy on 2007-01-02
With the CD version at least, the word is to copy the **linux_installer.sh** onto your desktop & run it from there, for the best install experience?!

That is how I have allways installed the UT2k4 CD version.

---

### Post by Lord Illidan on 2007-01-02
> **Zeikcied said:**
> No...It's UT2004 ECE.  It's from Gamestop, and it is just the UT2K4 box, and no other Unreal games.  It's also the version published by Midway (since Atari lost the Unreal publishing deal).  But, it says on the cover "Includes Editor's Choice and Mega Bonus Pack!"  So...I'm assuming it's the ECE.  It doesn't have any Linux installer, anyway.

I have a dual-boot system, so should I just install it on Windows and then copy the files over to Linux, then apply whatever Linux patches?  I think that'd be easier than the networked computer method mentioned earlier.  And faster.

I had this happen to me too.

What I did was I just installed it on Windows.

Then I copied everything to Linux.

Then I downloaded the linux patches off UT's website, and unzipped them to the SYSTEM folder.

Then I tried running it. Didn't work, because of missing versions of SDL.

So I just got the linux ut2004 demo, got the sdl and openal libs 

libSDL-1.2.so.0
and openal.so

and tried it again. Worked like a charm.

---

### Post by Zeikcied on 2007-01-02
> **Lord Illidan said:**
> I had this happen to me too.

What I did was I just installed it on Windows.

Then I copied everything to Linux.

Then I downloaded the linux patches off UT's website, and unzipped them to the SYSTEM folder.

Then I tried running it. Didn't work, because of missing versions of SDL.

So I just got the linux ut2004 demo, got the sdl and openal libs 

libSDL-1.2.so.0
and openal.so

and tried it again. Worked like a charm.
I did something similar to that.

I followed the How-To that explained copying the game from Windows to Linux.  I ran the installer, and copied the binaries that it extracted before asking for a disc, and put them in a temporary location.  I downloaded the 3369 patch (from Gamespot), and copied those files on top of the binaries from the installer.  Then I copied the game files from Windows to Linux, and then copied the binary/patch files on top of all that.

I try to open it, and I get to the splash screen before it errors out with:

> Can't find 'ini:Engine.Engine.GameEngine' in configuration file

History:

Exiting due to error

So, I have no clue what to do now.  I did what the guide suggested, and it won't run :(

---

### Post by Lord Illidan on 2007-01-02
> **Zeikcied said:**
> I did something similar to that.

I followed the How-To that explained copying the game from Windows to Linux.  I ran the installer, and copied the binaries that it extracted before asking for a disc, and put them in a temporary location.  I downloaded the 3369 patch (from Gamespot), and copied those files on top of the binaries from the installer.  Then I copied the game files from Windows to Linux, and then copied the binary/patch files on top of all that.

I try to open it, and I get to the splash screen before it errors out with:



So, I have no clue what to do now.  I did what the guide suggested, and it won't run :(
Do you have a folder .ut2004 in your home directory? Delete it.

---

### Post by Zeikcied on 2007-01-02
> **Lord Illidan said:**
> Do you have a folder .ut2004 in your home directory? Delete it.

I only have a .ut2004demo folder, which is locked.  Would that have anything to do with it?

Oh, I just got Unreal Anthology, after noticing the Tux logo on the box.  And wouldn't you know it, no Linux installer.  Why have Tux if there is no installer?

So...I'm trying to make it install via Wine.  At the very least, I hope I can play the games via Wine.  If the installer works...it seems to be giving me a bit of trouble.  It keeps hanging at various points.  Almost randomly.

What the hell is up with the lack of Linux installers?

---

### Post by Lord Illidan on 2007-01-03
> **Zeikcied said:**
> I only have a .ut2004demo folder, which is locked.  Would that have anything to do with it?

Oh, I just got Unreal Anthology, after noticing the Tux logo on the box.  And wouldn't you know it, no Linux installer.  Why have Tux if there is no installer?

So...I'm trying to make it install via Wine.  At the very least, I hope I can play the games via Wine.  If the installer works...it seems to be giving me a bit of trouble.  It keeps hanging at various points.  Almost randomly.

What the hell is up with the lack of Linux installers?

Use google. I managed to get mine installed by looking at various sites, and editing or deleting various .ini files in the directory. It takes some time.

I don't know about UT 2004 and Wine.

---

### Post by diepruis on 2007-01-03
> **Lord Illidan said:**
> I don't know about UT 2004 and Wine.

Doesn't work, I tried.

---

### Post by Rhubarb on 2007-01-03
If you can wait for 6 hours (I'm at work now), I'll upload my linux installer to my website.
It's from the original Unreal Tournament 2004 DVD.

I'll check this thread before uploading to see if you've fixed the problem first, and I'll obviously post a link to the download right after I've finished uploading the file.

Hope you get it all working, my experience with UT2004 is that it runs at the same frame-rate as it does in windows, except that in Linux loading up maps and especially quitting UT2004 is much much faster.  This is especially true when comparing with Vista RC1 and Ubuntu Dapper (haven't tried it with Edgy yet ... I might try it tonight).

---

### Post by diepruis on 2007-01-03
> **Rhubarb said:**
> If you can wait for 6 hours (I'm at work now), I'll upload my linux installer to my website.
It's from the original Unreal Tournament 2004 DVD.

Can't you just get the one from liflg.org?

---

### Post by Zeikcied on 2007-01-03
I've decided to just install Unreal Anthology using Cedega.  UT2004 ran fine in Wine, but for some reason, Wine wouldn't let me move the mouse as I should.  So I'm hoping Cedega will correct that issue.

It may not be native Linux, but it's better than nothing.

---

### Post by Zeikcied on 2007-01-03
Ok, UT2004 looks like crap in Cedega.  Could be my settings, but on the Absolute Zero map, it doesn't draw the textures and stuff correctly.  Or at all.

In the Wikipedia entry for Unreal Anthology, it says that a Linux installer was released due to community complaints, but I've searched on Google, and I can't find any such installer.  And the Wikipedia article doesn't supply a link.

Is this a case of incorrect information, or is there really a native Unreal Anthology installer out there?

---

### Post by diepruis on 2007-01-03
[QUOTE=Wikipedia]A minority of players were turned off by the lack of Linux support by the anthology. The executables to run on Linux is offered as a free download.[/QUOTE]

Odd. I didn't find anything when I did my search. Could be that the author of the article is not a linux user and, as such, didn't test his theory. There's nothing on liflg.org at any rate.

---

### Post by Rhubarb on 2007-01-03
Ok, for those of you that want to download the linux UT2004 DVD installer, here it is (28MB):
```
wget http://web.aanet.com.au/camdaw/media/linux-installer.sh
```

And for those that want to see UT2004 running in Dapper (could be edgy - I can't remember), being operated (poorly) via a remote control (7MB):
```
wget http://web.aanet.com.au/camdaw/media/ut2004_remote.mp4
```

* This will only be online from anywhere from a week to a year depending on how lazy I am / how much traffic I get.

---

### Post by Zeikcied on 2007-01-03
> **Rhubarb said:**
> Ok, for those of you that want to download the linux UT2004 DVD installer, here it is (28MB):
```
wget http://web.aanet.com.au/camdaw/linux-installer.sh
```
I get a 404 when I try that.

Or is it not up yet?

---

### Post by Zeikcied on 2007-01-03
Well, I got UT2004 to run.  Yay!

I did the whole "install to Windows and copy files to Linux" thing.  The reason why it wasn't working was apparently because, when I was doing "sh ut2004" it was calling a link in /usr/local/bin that pointed to the UT2004 Demo executable that I had installed.  The demo uninstaller wouldn't run, so I just deleted the demo and the link.  So while I have no idea how to recreate the link so it will point to the full UT2004 game, I can at least get it to run now.

I'm happy :)

Now my only concern is if the .run files for the mods over at that one site will recognize that I have UT2004 installed...

---

### Post by Rhubarb on 2007-01-03
Oops, thanks for letting me know of the broken link.
This time I've tested it to make sure it works:-
```
wget http://web.aanet.com.au/camdaw/media/linux-installer.sh
```
It might be a good idea to download this, so you don't have to do all the windows messing around to get it to work.

---

### Post by macabro22 on 2007-12-13
I am trying to update the game with the megapack file from here
[URL="http://www.liflg.org/?catid=6&gameid=17"]  but it says I need to have ut2004 installed which I *do*.

Anyone suceeded upgrading the game?

---

