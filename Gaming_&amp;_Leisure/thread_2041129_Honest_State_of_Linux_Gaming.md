---
title: "Honest State of Linux Gaming"
date: 2012-08-11
forum: Gaming &amp; Leisure
---

### Post by holastickboy on 2012-08-11
Hi all!

I have been using Linux for just over ten years now, and I have always had to have the whole dual-boot thing with Windows for my gaming addiction.  With a lots of old information about Linux gaming, I thought that it would be nice to do an article about the Honest State of Gaming in Linux currently.  

I have written a large article that discusses my experience with Linux gaming, including Wine and native games.  They are written by a user, for a user, so I certainly wouldn't call my article journalistic, but rather for entertainment. I am honest about my experience, and I do make calls when things don't work well, and I communicate about when they do.

Feel free to have a read of my article, and leave comments and share.

[http://revisitthis.blogspot.com.au/2012/08/linux-honest-state-of-gaming-preview.html](http://revisitthis.blogspot.com.au/2012/08/linux-honest-state-of-gaming-preview.html)

I check these forums regularly too, so am happy to discuss stuff here too.  Thanks for your time!

---

### Post by PaulInBHC on 2012-08-11
About what I expected.

My problem with native games is that most of them are FPS/RPG/RTS and I don't play those. Most of what I play only works in Windows at this time. I am not savvy enough to tweek with winetricks or I might be able to get some of them working. I want wine at the point where I can just install a game and it works.

I do applaud Desura for having 3 OS versions and wonder if this may have influenced Valve.

---

### Post by doorknob60 on 2012-08-11
> **PaulInBHC said:**
> 
My problem with **modern** games is that most of them are FPS/RPG/RTS .

Fixed that for you :P

---

### Post by ads52 on 2012-08-11
Thanks for the great article which I read with interest. I noticed that you did not deal with older games that have been successfully ported to Linux, perhaps because you are not an old fogy like myself :).  My own addiction is to a successful port of the old DOS game Descent 2 called d2x-rebirth but I am aware of descent work with the various iterations of Quake as well as games like Rise of the Triad.

Again, thanks for taking the effort to produce this article.

---

### Post by doorknob60 on 2012-08-11
And relating to your issues about Wine:

What I've noticed is the AMD Catalyst drivers work very well for everything EXCEPT Wine. I've had nothing but problems when trying Wine games on systems with Catalyst, but eveyrhting else always seems to work quite well. With Nvidia however, Wine runs just fine. That's just my experiences though. For example TF2, it won't run on my laptop in Wine with Catalyst (or the open ones for that matter, which don't run well with native stuff either), but on my desktop with the Nvidia blob, TF2 works just fine.

This is reflected by the results of his testing, the native games worked great, the Wine ones were hit and miss.

---

### Post by holastickboy on 2012-08-12
Thanks everyone for your comments, they are greatly appreciated.  Actually, I do play quite a lot of old games in Linux, particularly thanks to GoG.com installers (most of which work perfectly under WINE).  I was trying to get an idea about how current gaming was, with some real life examples.  I might do another article in the short future that looks at old gaming on Linux, as I do have an interest in that as well.  I am not much of a programmer, and find it hard to give back to OSS, so if I can do it via this, it would make me happy :D

---

### Post by ads52 on 2012-08-12
> **holastickboy said:**
>   I might do another article in the short future that looks at old gaming on Linux, as I do have an interest in that as well. 

I look forward to reading this one :).

---

### Post by mastablasta on 2012-08-12
> **PaulInBHC said:**
> 
My problem with native games is that most of them are FPS/RPG/RTS and I don't play those. Most of what I play only works in Windows at this time. I am not savvy enough to tweek with winetricks or I might be able to get some of them working. I want wine at the point where I can just install a game and it works.
.

i thought play on linux provides an easier way to setup wine.

---

### Post by Greggyboy on 2012-08-12
Good read. :)

Gamming on linux isn't just about what games work and what don't though, peripherals like controllers, usb headsets, etc, can be a big issue too.

---

### Post by PaulInBHC on 2012-08-12
> **mastablasta said:**
> i thought play on linux provides an easier way to setup wine.

Yes it does and I use it. But if the game doesn't work, POL doesn't tell you what to do to try again.

---

### Post by holastickboy on 2012-08-12
> **Greggyboy said:**
> Good read. :)

Gamming on linux isn't just about what games work and what don't though, peripherals like controllers, usb headsets, etc, can be a big issue too.

Excellent point.  I actually recently plugged in my USB controller, and to my horror, it detected it as a keyboard and mouse, so now the joysticks move my mouse around the screen.  I downloaded and installed js-test-gtk and it allowed me to remap the buttons successfully.

As for headset, I use a standard 3.5MM connection headset (as I have a Soundblaster X-Fi card plugged into my pci-e slot, don't need another USB sound).  This has worked nicely for me, but I can definitely imagine the difficulties with the USB connections.  I find that Linux defaults to the HDMI sound on my ATI graphics card before it bothers to output to Sound Blaster too, which is easy to change, if you know where to look.

As for PlayonLinux, I have used it in the past, but some of the game profiles are dreadfully old (for example, last game profile for WoW is WOTLK, which is 2 years old, and there has been major changes to the engine since then).  I installed WINE and winetricks to make my life easier.  

I might add an update to my article, as I have done significantly more tweaking to my WoW installation and am now finding that the experience is rather smooth overall.  I have been playing WoW on Linux for the last 3 days exclusively, so it's been rather delightful to not have to reboot into Windows for just one task.

Again, thanks to everyone for reading the article and giving me your input. It's appreciated!

---

### Post by mastablasta on 2012-08-13
> **PaulInBHC said:**
> Yes it does and I use it. But if the game doesn't work, POL doesn't tell you what to do to try again.
 
ah i see (i haven't tried it yet). what about Crossover?

---

### Post by nyamina on 2012-08-13
I actually just installed WINE and then installed Half-Life 1 and 2 without having to adjust or tweak anything at all. It even worked with my XBox 360 controller, and, amazingly, worked with XPadder, the program for remapping game controllers to keyboard buttons and the mouse for older games.

In fairness, it would be good if there were just a whole ton of little programs where you just click, get a little GUI, tell it where the .exe is, and boom, it installs it, hiding away all the wine stuff, without all the "pretend c:/ drive" and windows 95 theme.

---

### Post by holastickboy on 2012-08-13
Do you have an Nvidia graphics card by any chance? Im using an AMD graphics card, and I have a suspicion that this might be the cause of the problems with Half Life 2 in my tests (had decent FPS, but severe graphical glitching)

---

### Post by PaulInBHC on 2012-08-13
Crossover is not free. They have a list what works as does POL and winehq. I have games that are not on those lists. I already paid for Windows and it works.

I have partitions for XP, 11.10 upgraded to 12.04, and 12.04. The second one lost the desktop and no one can tell me how to fix it. I started using the 3rd last night and my mouse was slow. MS does not have linux drivers and ubuntu has no way to adjust the scroll wheel or add button features.

So back to Windows for me.

---

### Post by mastablasta on 2012-08-13
> **PaulInBHC said:**
> Crossover is not free. They have a list what works as does POL and winehq. I have games that are not on those lists. I already paid for Windows and it works.
.
well ofcourse it works. they were made for windows OS weren't they?
 
MOder games mostly don't work in wine. Well, some do, but mostly they don't.
 
> 
and ubuntu has no way to adjust the scroll wheel or add button features.

 
it  does in a messy config file. for some mice (like logitech) you can use a GUI as well.

---

### Post by PaulInBHC on 2012-08-13
google and forum searches lead me to read that the config file was removed from ubuntu. You can however create one. Then you need the knowledge to type in what you need to make something work. I don't. There was a GUI for xorg.conf but the writer gave up on it a couple of years ago when the config was removed. Might still work though.

Anyway, the state of linux gaming to me is, if you like FPS/RPG/RTS there are some great games with good graphics, some free.

There are some good projects that suffer from not getting finished for whatever reason.

wine/POL/Crossover are not quite there yet.

---

### Post by holastickboy on 2012-08-14
> **PaulInBHC said:**
> google and forum searches lead me to read that the config file was removed from ubuntu. You can however create one. Then you need the knowledge to type in what you need to make something work. I don't. There was a GUI for xorg.conf but the writer gave up on it a couple of years ago when the config was removed. Might still work though.

Anyway, the state of linux gaming to me is, if you like FPS/RPG/RTS there are some great games with good graphics, some free.

There are some good projects that suffer from not getting finished for whatever reason.

wine/POL/Crossover are not quite there yet.

I agree, they are definitely better than they were a few years ago, and they seem to be making some decent progress too. With a project like WINE, they are always playing the catch up game

---

### Post by holastickboy on 2012-08-15
I've started fiddling with some older games and WINE, and I'm not having a great deal of luck at the moment.  My only access to these older games is via the Good Ol Games website downloads (mainly dosbox wrapped windows executables).  Anyone had any luck with them? (I have a few working, but majority are not working at all).

---

### Post by ads52 on 2012-08-15
> **holastickboy said:**
> I've started fiddling with some older games and WINE, and I'm not having a great deal of luck at the moment.

I am hoping that perhaps I have met another fan of the old DOS game Descent 2?

---

### Post by mastablasta on 2012-08-16
> **ads52 said:**
> I am hoping that perhaps I have met another fan of the old DOS game Descent 2?
 
I hated  part 2 becuase of those stealing bots. and when you destroyed them you didn't even get everything back. first one was quite nice though. ihtink graphcis are more or less the same. 
 
> **holastickboy said:**
> I've started fiddling with some older games and WINE, and I'm not having a great deal of luck at the moment. My only access to these older games is via the Good Ol Games website downloads (mainly dosbox wrapped windows executables). Anyone had any luck with them? (I have a few working, but majority are not working at all).
 
why not just use dosbox in linux? there are plenty of abandonware sites that offer zipped archives of original old games. you can then use dosbox in linux or instal for example DBGL (needs sun java) frontend : [http://members.quicknet.nl/blankendaalr/dbgl/](http://members.quicknet.nl/blankendaalr/dbgl/)

---

### Post by Erik1984 on 2012-08-16
That's a very nice write up! I like articles like this. Makes me want to give the olde StarCraft a try on Linux soon.

---

### Post by ads52 on 2012-08-16
> **mastablasta said:**
> I hated  part 2 becuase of those stealing bots. and when you destroyed them you didn't even get everything back. first one was quite nice though. ihtink graphcis are more or less the same.

Well you may be interested to look at d1x-rebirth and d2x-rebirth which for me have been an amazing nostalgia trip back to my DOS days. Both games have weathered to decades well :).

---

### Post by Eddie Wilson on 2012-08-16
> **Euroman said:**
> That's a very nice write up! I like articles like this. Makes me want to give the olde StarCraft a try on Linux soon.

The old Starcraft works just fine. :)

---

### Post by Eddie Wilson on 2012-08-16
> **ads52 said:**
> Well you may be interested to look at d1x-rebirth and d2x-rebirth which for me have been an amazing nostalgia trip back to my DOS days. Both games have weathered to decades well :).

I loved Decent more than Decent 2. I do miss them. I guess I need to take a look at d1x-rebirth and d2x-rebirth.

Thanks.

---

### Post by ads52 on 2012-08-16
> **Eddie Wilson said:**
> I loved Decent more than Decent 2. I do miss them. I guess I need to take a look at d1x-rebirth and d2x-rebirth.

The developers have done a beautiful job and there are a couple of extra / reworked soundtracks that fit in very neatly with both games.

---

### Post by Erik1984 on 2012-08-16
> **Eddie Wilson said:**
> The old Starcraft works just fine. :)

Actually I have tried but just on a too crappy PC for 'emulation' of Windows games and without legacy proprietary nvidia drivers in place. Even on that PC it did work, just not smooth enough. I'm convinced it will run fine on my current *buntu setup. I just forgot about it and this article sparked my interest in Starcraft again :P

---

### Post by mad gamer on 2012-08-17
> **holastickboy said:**
> so now the joysticks move my mouse around the screen

:eek:

> **holastickboy said:**
> As for headset, I use a standard 3.5MM connection headset (as I have a  Soundblaster X-Fi card plugged into my pci-e slot, don't need another  USB sound).  This has worked nicely for me, but I can definitely imagine  the difficulties with the USB connections.  I 

I have a Plantronics GameCom 780 (usb) on the way so it will be interesting to see how ubuntu handles it.

Btw, good article holastickboy! Look forward to seeing more. :)

---

### Post by holastickboy on 2012-08-28
> **holastickboy said:**
> Hi all!

I have been using Linux for just over ten years now, and I have always had to have the whole dual-boot thing with Windows for my gaming addiction.  With a lots of old information about Linux gaming, I thought that it would be nice to do an article about the Honest State of Gaming in Linux currently.  

I have written a large article that discusses my experience with Linux gaming, including Wine and native games.  They are written by a user, for a user, so I certainly wouldn't call my article journalistic, but rather for entertainment. I am honest about my experience, and I do make calls when things don't work well, and I communicate about when they do.

Feel free to have a read of my article, and leave comments and share.

[http://revisitthis.blogspot.com.au/2012/08/linux-honest-state-of-gaming-preview.html](http://revisitthis.blogspot.com.au/2012/08/linux-honest-state-of-gaming-preview.html)

I check these forums regularly too, so am happy to discuss stuff here too.  Thanks for your time!

Please note, I have migrated my Blogger blog with this article to my Ubuntu webserver at [http://popularpariah.com](http://popularpariah.com)

---

### Post by Nanur on 2012-08-30
That was an interesting read.

---

### Post by walker195 on 2012-08-31
> **doorknob60 said:**
> Fixed that for you :P

no i believe he meant native as it you dont need wine

---

### Post by ZoiaGuyver on 2012-09-01
Good read, nicely done!

I did notice a while ago telling WoW and "Source" based games to run in opengl mode (manually editing the configs) normally really kicks up performance (prob as it's one less thing to mess about with on Wine) running the games in DX mode though can lead to issues, after all it is a MS API.

---

### Post by Roque Lmnz on 2012-09-01
Great text. Most of this games i won't be able to test myself because of my notebook config (and i don't have a desktop). Anyway i'm really glad to see gaming on Linux has been improving that much in the past 4~5 years. Hope VALVE rocks the house when it comes to Linux and so we can stop hearing "I don't use Linux because gaming on Linux sucks." in a promising future.

---

### Post by shazeal on 2012-09-02
Im currently using VMWare workstation 9 to game on linux, playing through Skyrim again. The performance is amazing, its stupidly better than workstation 8 which was not really an alternative for gaming.

Im playing skyrim with a load of mods, 1680x1050, Medium settings, minor frame rate jitter in some dungeons otherwise its comparable performance to windows native, admittedly I could run High settings on native windows, but this means no dual boot :)

Computer is i5 2500, with nvidia 560 gtx. I have also disabled pulse audio and am just using ALSA since pulse was causing performance problems.

---

### Post by contributor on 2012-09-13
Is that article is removed or what? When I clicked on that link, I found think. I guess, the site has been moved to somewhere else.

---

### Post by synaptix on 2012-09-13
> **contributor said:**
> Is that article is removed or what? When I clicked on that link, I found think. I guess, the site has been moved to somewhere else.

Seems to have been removed.

---

