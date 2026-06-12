---
title: "[SOLVED] Just migrated from Windows"
date: 2005-11-27
forum: Desktop Environments
---

### Post by crazyness003 on 2005-11-27
Hi everyone. I just moved from Windows(tm) and decided to take refuge under the Ubuntu roof. I have U 5.10 "Breezy Badger" (whatever that means) installed. Just so you know, i have NO idea how to operate ubuntu. Its like I'm on an alien planet free of Microsoft(r) corruption and greed. I'm very new to this, so i have a whole bunch of questions.
1) Can I install most of the software that i had on Windows? and if so, how?
2) My mp3's wont play, and I dont even know where to play them. Can I install iTunes on there, or WMP(tm)?
3) Everytime i try to run a .exe, it says > Couldn't display "*whatever*.exe"
4) How can i get to the weird "sudo *bla bla*" thing I see ppl talking about?
5) Can I use the same drivers I had on my "Windows(tm) Version" computer? I have a laptop, so i need specific drivers for all of the components. Its an eMachines M2350, and it was Designed for Windows(tm) XP. Its got ATI Radeon IGP graphix, AMD Atholon XP-M mobile processor, On-Board Wi-Card, Cup holder(well, not really), etc.

Sorry if I posted on the wrong forum. If there's a "Newbies start here with Ubuntu" site i can go to, I'd like to know about it. ANd im kinda low on time, the only time i have time to do time-consuming things is about 12am (Eastern), so quick, fast, and in-a-hurry tactics are appreciated.

Thanks everyone.

---

### Post by Perfect Storm on 2005-11-27
[QUOTE=crazyness003]Hi everyone. I just moved from Windows(tm) and decided to take refuge under the Ubuntu roof. I have U 5.10 "Breezy Badger" (whatever that means) installed. Just so you know, i have NO idea how to operate ubuntu. Its like I'm on an alien planet free of Microsoft(r) corruption and greed. I'm very new to this, so i have a whole bunch of questions.
1) Can I install most of the software that i had on Windows? and if so, how?
2) My mp3's wont play, and I dont even know where to play them. Can I install iTunes on there, or WMP(tm)?
3) Everytime i try to run a .exe, it says 
4) How can i get to the weird "sudo *bla bla*" thing I see ppl talking about?
5) Can I use the same drivers I had on my "Windows(tm) Version" computer? I have a laptop, so i need specific drivers for all of the components. Its an eMachines M2350, and it was Designed for Windows(tm) XP. Its got ATI Radeon IGP graphix, AMD Atholon XP-M mobile processor, On-Board Wi-Card, Cup holder(well, not really), etc.

Sorry if I posted on the wrong forum. If there's a "Newbies start here with Ubuntu" site i can go to, I'd like to know about it. ANd im kinda low on time, the only time i have time to do time-consuming things is about 12am (Eastern), so quick, fast, and in-a-hurry tactics are appreciated.

Thanks everyone.[/QUOTE]


1. No, I'm afraid not. Though Linux have alternative to the windows programs check here: [http://ubuntuforums.org/showthread.php?t=33183](http://ubuntuforums.org/showthread.php?t=33183)

2. To play your mp3 files - **Application** --> **Sound and Video** --> **XMMS**

3. Linux can't run .exe files. .exe files are window a window format.

4. When people are talking sudo etc. etc. they are talking about commands in the terminal. To use it: **Applications** --> **Accessories** ---> **Terminal**

5. Most of the drivers are included in Linux, you may seek howto install 3D acc. for your ATI card in the HOWTO section.

Beginner forum: [http://ubuntuforums.org/forumdisplay.php?f=73](http://ubuntuforums.org/forumdisplay.php?f=73)

---

### Post by potrick on 2005-11-27
Hello, and welcome to Ubuntu!

  As Ubuntu is not windows, Ubuntu cannot run Windows programs natively, so you cannot open just any .exe file. If you want to run windows programs, I suggest you use windows. You could technically get some of the programs you are talking about running in Wine (a translation program that allows Linux to run Windows apps) but you really are better off using the Linux equivilents, especailly if you don't have a lot of time. 
  Check out this forum if you want to know which applications do which things:  

[http://www.ubuntuforums.org/showthread.php?t=33183](http://www.ubuntuforums.org/showthread.php?t=33183)

  And, if you want to escape the "Microsoft corruption and greed" why would you want to install its capital, WMP?

---

### Post by etc on 2005-11-27
1) You should use the Linux alternitives to your Windows software, but you can use Wine to run those windows programs that have no linux option, just open Synaptic Package Manager under System -> Administration, and search for wine, mark it for installation, click apply.

2) Look at [Automatix]("http://ubuntuforums.org/showthread.php?t=66563"), which will install your MP3 codecs.  They aren't included by default due to patents.  Try out Rhythmbox or XMMS for something like iTunes.

3) .exe's are for Windows platforms, but you can use Wine to run them.  Please try to use Linux native programs though.

4) "sudo" stands for superuser do.  It's an alternative for using the root account, which is a bad idea.  To use it, open a terminal and type in "sudo <app that needs admin rights>".

5) No, you can't use Windows drivers, but for the other hardware maybe someone else could help.

Also, keep in mind that Ubuntu isn't 'Windows without the spyware and viruses'.  Linux is a completely different system that does things differently than Windows, so don't get frustrated when it doesn't do things the 'windows way', because you'll get used to it.

---

### Post by 23meg on 2005-11-27
Welcome.

1) Depends on what software you used, but chances are not most, but some. Instead of trying to get your Windows software working, look for Linux alternatives to your Windows software first. If you don't find any, look for instructions on setting up Wine and getting the Windows ones working.

2) To get mp3s working, do this: [http://help.ubuntu.com/starterguide/C/faqguide-all.html#codecs](http://help.ubuntu.com/starterguide/C/faqguide-all.html#codecs)

You may be able to get itunes working, but not WMP. When you see the choices you have in Ubuntu, chances are you won't want to get back to either anyway.

3) You need [Wine]("http://www.winehq.com/") to use Windows software, and it only works with some Windows software. Not even most.

4) You mean the terminal? Applications / System Tools / Terminal or hit alt-f2 and type "gnome-terminal". Or hit ctrl+alt+f1.

5) No. Most drivers should already be set up. If any of your devices aren't working as supposed, do a search to find out if you need a driver for them, and if you can't find any, post a problem thread.
__

---

### Post by Perfect Storm on 2005-11-27
ATI: [http://doc.gwos.org/index.php/3D_Graphic_Cards](http://doc.gwos.org/index.php/3D_Graphic_Cards)

You may also check for further howto: [http://doc.gwos.org/index.php/BreezyCust](http://doc.gwos.org/index.php/BreezyCust)

---

### Post by Emerzen on 2005-11-27
1.)  No, you can't install most of the software.  There are Linux equivalent apps for most of what you have in Windows though, and it's free.

2.)  Check out this site [www.ubuntuguide.org](www.ubuntuguide.org) for media playback instructions (and a general quick guide for newbs).

3.)  Linux can't run .exe files directly.  There is an app called WINE in the repositories that can run some of these.

4.)  Under the main menu look in Accessories and there is a "terminal" icon, open it and type sudo blah blah blah stuff there.

5.)  If you already have Ubuntu installed & working, then you have the drivers already preconfigured.  There are specific drivers written for different pieces of hardware in Linux, e.g. graphics cards, search the forums w/ the name of your hardware.  If you're a newb I'd stick w/ the preinstalled driver's until you're more comfortable w/ Linux.
-------------------------------------------------------------------------
By the way, I just recently moved to Windows and could you answer these questions for me?

1.)  I use alot of software under Linux, how can I go about running them in Windows?

2.)  My OGG files won't play, how do I get it working?

3.)  How do I get a .bin file to run?

4.)  Can I use the drivers I use in Ubuntu in Windows?

5.)  How come I have to reboot every time I install a new piece of software?

6.)  Should I be concerned about all these viruses, spyware, trojans, etc...  I was fine w/ no security in Ubuntu.  Should I spend hundreds of dollars buying software to guard my computer or can I just leave it open?

7.)  How do I get it not to lock up so much?  How do I figure out what are the right settings?

---

### Post by crazyness003 on 2005-11-27
WOW. That was fast.
Okay, i think I got a few things down. Windows and its programs will be just that. So alternatives are the way to go...hmm, cool. And you say that my drivers n such should already be hooked up. Alright.
Now here's the clincher:
-I converted all of my mp3's to wma's for size's sake (I noticed wma's of the same song were a bit smaller). Now, i have a converter that takes them from one to the other and vice-versa, but I bet i cannot play them in wma format. Right?
Meh, a small price to pay.
Well thanx anyway. I like Ubuntu, its smooth and shiney :D 

Keep the peace!

---

### Post by etc on 2005-11-27
After I installed the non-free codecs using Automatix, I could play WMAs.  You should use a different format though.

---

### Post by crazyness003 on 2005-11-27
> By the way, I just recently moved to Windows and could you answer these questions for me?

1.) I use alot of software under Linux, how can I go about running them in Windows?

2.) My OGG files won't play, how do I get it working?

3.) How do I get a .bin file to run?

4.) Can I use the drivers I use in Ubuntu in Windows?

5.) How come I have to reboot every time I install a new piece of software?

6.) Should I be concerned about all these viruses, spyware, trojans, etc... I was fine w/ no security in Ubuntu. Should I spend hundreds of dollars buying software to guard my computer or can I just leave it open?

7.) How do I get it not to lock up so much? How do I figure out what are the right settings?

LOLOLOL! Thats funny. Thats one of the reasons I moved.

Now, here's some more questions (sorry):
  "Repositories"
Whats are they, whats in them, and where can i get them (er..whats inside of them, whatever). Do i have to be connected to the intenet (oh, did i mention i still use dial-up? One of the many obstacles I face in modern society).

AND

Does Macromedia Flash 8 (the authorware stuff, for making Flash content) work in Linux? if not, is there a Linux verson as kick-ars as it?

Well, thanks again. You guys rock!

---

### Post by Perfect Storm on 2005-11-27
> Repositories"
Whats are they, whats in them, and where can i get them (er..whats inside of them, whatever). Do i have to be connected to the intenet (oh, did i mention i still use dial-up? One of the many obstacles I face in modern society).

Yes, you have to connect to the internet. 
To change your repo:
```

sudo gedit /etc/apt/sources.list

```

[http://doc.gwos.org/index.php/Sources.list](http://doc.gwos.org/index.php/Sources.list)

---

### Post by crazyness003 on 2005-11-27
Oh, and I also forgot to ask:
I got a disc from a friend who told me there were a bunch-o Ununtu Add-ons on it. But, being the n00b I am, how do I install/add er whatever to Ubuntu? I tried just popping in the CD, but i didnt know waht to do after that.

You guys have helped a whole lot

---

### Post by Emerzen on 2005-11-27
That was my attempt at a Jedi Mind Trick...trying to highlight that you're in a new operating environment.  It sounds like you jumped right into the deep end though...great.

Go to System Tools and look for Synaptic, open it.  This is your link to the repositories (where the software resides)...and yes, you do need an internet connection.  By the way, what kind of modem do you have?  How'd you get it set up?

Flash is installable and I believe it's in the repositories.  Again, search the forums specifically for "flash" and you should find plenty of posts w/ details or check out [www.ubuntuguide.org](www.ubuntuguide.org) .  It's the place to start as well as the Wiki.

---

### Post by Brent Dax on 2005-11-27
> **crazyness003]I have U 5.10 "Breezy Badger" (whatever that means) installed.[/quote]
"Breezy Badger" is the codename for this release said:**
> 1) Can I install most of the software that i had on Windows? and if so, how?
You can run some Windows program using Wine, but it's a bit hit-and-miss.  A better solution is to find Linux programs to replace the ones you used on Windows.  Many programs which are add-ons in Windows have equivalents installed with Ubuntu--OpenOffice replaces Office, Gaim replaces most of the popular IM programs, The Gimp replaces Photoshop, etc.  There's a table on [the Ubuntu Wiki](https://wiki.ubuntu.com/WhatWindowsUsersWant#head-86f47411cd5a7a7022fe8cd24399781a22d1a891) which details some common Windows programs and their Linux equivalents.

[QUOTE=crazyness003]2) My mp3's wont play, and I dont even know where to play them. Can I install iTunes on there, or WMP(tm)?[/quote]
iTunes (regretfully) and Windows Media Player (not-so-regretfully) aren't available on Linux.  However, there are several nice Linux players--XMMS is similar to Winamp, while Rhythmbox and Banshee are similar to iTunes.  amaroK isn't quite like anything on Windows, but it's probably the most powerful Linux music player.

MP3 support isn't installed by default because the MP3 format is patented.  However, you can install it from the "universe" repository.  Support is also available for other formats, such as unprotected Apple AAC files.

[QUOTE=crazyness003]3) Everytime i try to run a .exe, it says [/quote]
EXE files are designed for Windows, so they won't run under Linux without help.  Many EXEs will run if Wine is installed.

[QUOTE=crazyness003]4) How can i get to the weird "sudo *bla bla*" thing I see ppl talking about?[/quote]
When someone tells you to type "sudo blah blah", they're telling you to pull down the Applications menu, point to Accessories, click Terminal, and type the command given.

[QUOTE=crazyness003]5) Can I use the same drivers I had on my "Windows(tm) Version" computer? I have a laptop, so i need specific drivers for all of the components. Its an eMachines M2350...[/quote]
It looks like that should've been auto-configured for the most part.  [This page on the Ubuntu Wiki]("https://wiki.ubuntu.com/HardwareSupportMachinesLaptopsOthers?highlight=%28M2350%29") contains some information on configuring Ubuntu for that model.  (By the way, "Designed for Windows XP" is basically just a Microsoft marketing ploy.)

A lot of your questions on installing things can be answered in the Ubuntu Starter Guide.  This is included with Ubuntu--just go to System, select Help, and then select "Ubuntu 5.10 Starter Guide" on the screen that appears.

---

### Post by Perfect Storm on 2005-11-27
Just a note to Emerzen comment. That ubuntuguide.org is for v5.04 and there may be things in there that doesn't work.

---

### Post by crazyness003 on 2005-11-27
Oh, im using a different compy to acomplish my "roaming of the net". With dialup, i need to install My ISP's software and connect and...pfft, not worth the hassel. I'll wait till i go to school, we got a wireless network hooked up there, so i'll do stuff there in more detail. But no, im using XP and IE to read up on all-o-this awesome info. Thanx again guys.

By-the-way: How much do you gotta know how to modify and make your own version of linux? Not that i'm ready for that, but just a thought.

---

### Post by Emerzen on 2005-11-27
Yep, good point AI.  For the original poster, when I refer you to [www.ubuntuguide.org](www.ubuntuguide.org) ,it was written for the previous version of Ubuntu.  I've used it for a reference for the Breezy Badger, but some things may not work.  The built in guide under the help/lifeboat is a better start.

---

### Post by angkor on 2005-11-27
@crazyness003.

A lot of helpful info can be found under **System -> Help -> Ubuntu 5.10 Starter Guide**

Welcome to Ubuntu and its wonderful community :)

---

### Post by crazyness003 on 2005-11-28
Alright. Thanks again guys. Your wisdome will be greatly appreciated. With all-o-this help, i might be able to help out some friends of mine who i shared my Ubuntu CD with. They just look at me and wonder "why?"

So i tell them "You wont regret it"

Thnx and Peace!

---

### Post by towsonu2003 on 2005-11-28
[QUOTE=crazyness003]Oh, im using a different compy to acomplish my "roaming of the net". With dialup, i need to install My ISP's software and connect and...[/QUOTE]

hmmm, your isp won't have software for linux -I guarantee that-... you'll need your username, password, and the phone number to dial in order to connect to isp from linux... 

usually,the problem will not be configuring connection, but the modem itself. go to System>Administration>Networking (will ask for password, give your own ubuntu password u set during install)... Do you see "Modem connection"? If you see it, you're so lucky and I'm so jealous: click on "modem connection", click on "properties", check "enable connection", put in your isp information, click 'ok', click on 'modem connection', click on 'activate', and wait+pray:) if 'activate' doesn't work, check the forum then post and we'll help :)

If you don't see the modem, it usually means you have a winmodem. hard to configure (because the modem manufacturer do not provide drivers and hardware specifications), sometimes never work in linux... first place to go is linmodems.org, read the page, download scanModem tool, read the readme file VERY closely and follow instructions, again, VERY closely. I wish you good luck: it took me 5 months to make the winmodem work, and it ONLY works with ubuntu (which is not that nice as I miss most of the linux 'democracy' of multiple distributions*...). u can post your winmodem issues here as well as emailng the linmodems.org mailing list. do NOT email linmodems.org mailing list if you did not read and follow the readme instructions came with scanModem tool, they hate when that happens... other than that, they are great+very helpful ppl.

*distribution=(distro) linux kernel + a bunch of software bundled in it. distrowatch.com will give you an idea about how many there are.

---

### Post by crazyness003 on 2005-11-28
[QUOTE=towsonu2003]hmmm, your isp won't have software for linux -I guarantee that-... you'll need your username, password...[/QUOTE]

Dont sweat it, i dont intend to connect my lappy to a dial-up isp anyway. It would slow me down to dis-proportional measures. Thanks for the info though, im sure someone will find it valuable.

Rroft Shiperia!

---

