---
title: "About Grim Fandango"
date: 2005-12-25
forum: Gaming &amp; Leisure
---

### Post by Zalbor on 2005-12-25
WinXP will not run it correctly, and 98 won't install on my PC, so if I'm going to play this again Wine is my only hope.
Now I know the official site lists it as playable, but I have a problem with graphical glitches, like for example, a texture not appearing correctly or worse, shapes being distorted etc (please don't tell me off about this, I'm very serious. These freak me out).

So I would like to know if anyone here has ran it, and how well it worked. I have the newest version of Wine from the winehq repositories.

Thank you.

---

### Post by madjinx on 2005-12-25
just wondering, have you tried the xp patch for it?

---

### Post by Zalbor on 2005-12-25
There is one? The only patch for it I see on support.lucasarts.com is the one that fixed the first bugs and added text to the cutscenes, but that has been out for years.

---

### Post by madjinx on 2005-12-25
[http://www.fetishfollies.com/Patch%20for%20Win%20XP.zip](http://www.fetishfollies.com/Patch%20for%20Win%20XP.zip)

its suppose to fix XP trouble.

theres also:

to make Grim Fandango installation not crash on windows xp, you just need to make a blank text document and copy 

@echo off
lh %SYSTEMROOT%\system32\mscdexnt.exe
lh %SYSTEMROOT%\system32\redir
lh %SYSTEMROOT%\system32\dosx
SET BLASTER=A220 I5 D1 P330 T3

and save it as autoexec.nt in c:\windows\system32\

if nothing works, theres always Winodws compatability mode.

---

### Post by Sudokan on 2005-12-25
Heh...I almost forgot about that game...a true classic...thanks for reminding me...Anyway, I got it out and installed it in Ubuntu Breezy. I have an ATI Radeon ( on this particular laptop, it is a Radeon 9600), and I had to start it with wine GRIMFANDANGO instead of wine grim, since grim.exe complained about a lack of directx. I got ingame, hit F1 and turned off the hardware acceleration, and it ran fine...I had a slight sound problem, but I changed to emulation and it worked fine. I also noticed if you run "wine GRIMFANDANGO" with the -? switch, it gives a short menu to modify the way Grim Fandango starts. Maybe someting there might help too. I couldn't find any patches, except the last official one, which I got off of [www.grimfandango.net](www.grimfandango.net). It doesn't specifically list XP support, but I can run it in XP with the patch, so maybe it helps. Anyway, good luck getting it to run.

Sudokan


Everything of importance has been said before by somebody who did not discover
it.
      -- Alfred North Whitehead

---

### Post by Zalbor on 2005-12-26
Thanks people! I'll try these things. :)
Just for the record, my problem wasn't with installing, and I did use compatibility mode. It's just that the graphics were sort of flickering at certain parts, like trembling.

---

### Post by stoffe on 2005-12-29
For those who installed it under Wine, how did you do? I can't do it - I pop in the first CD, run the installer and everything looks right... but I think it doesn't copy everything it should, it does seem to finish a bit fast. And when running the game - or the installer again, instead of "Play" it still says "Install".

It was a short while ago I tried it so this is what I remember, just wondered how you managed to get it installed, if there's anything I missed. It was as recently as wine 0.9.3 or at least 0.9.2 anyways. 

Best game ever, really want to run it again! :)

Thanks!

---

### Post by Zalbor on 2005-12-29
I still have problems in XP... And about running it under wine (party an answer to the above poster) I try to wine the executable of the game itself instead of the launcher. But then an error message appears that the cd isn't in the drive, which it is.

---

### Post by Franko30 on 2006-01-08
[QUOTE=Sudokan]I had to start it with wine GRIMFANDANGO instead of wine grim, since grim.exe complained about a lack of directx. I got ingame, hit F1 and turned off the hardware acceleration, and it ran fine...[/QUOTE]

Hi,

I'm running wine 0.9.5 on Breezy with an ATI card using the xserver-xorg-driver-ati driver.

If I install and run Grim Fandango as stated above with a freshly configured wine (winecfg), it complains about no CD being in the drive - although the drives have been configured...

If I use a fresh, winetools configured wine it doesn't doesn't complain about the CD-ROM, but about making sure that other DirectX processes seem to acces the  hardware. Problem is: The message is only displayed half and the message window can't be resized...

Ideas anyone?

Thanks in advance.

---

### Post by Sudokan on 2006-01-08
I haven't played this game in about few days; been busy with other things. I had to reload Ubuntu yesterday, and when I saw this thread today, I reinstalled Grim Fandango and tried to play it. I think something changed in the last version of Wine ( or I did something to my system that I forgot about when I reinstalled). At any rate, I also get a notice about the CD missing. I also now have 2 major problems I never had before; one with the sound locking up randomly ingame and the other being that I am unable to see the menu text when hitting F1. Other than that, it plays fine until it locks up. I have found a way to make the game play without the CD, but first a word of caution. It involves messing with the wine registry, and you could destroy your wine installation if you do something wrong. I would only do it if you are familiar with the windows registry. OK, my CYA statement is complete...so...One possible solution to the NO CD problem is to copy all the .lab files from the both CD's to the Grim Fandango install directory, then go to the wine windows directory, open a terminal, run regedit, go to HKLM/software/lucasarts/, and change the path for the CD and the data directorys to the Grim Fandango directory ( in my case c:\program files\lucasarts\grim\ ), and add a String  entry called "good_times" ( without the quotes ) and set its value to "true" (again without the quotes). This will enable the game to play without the CD. I am still trying to figure out the problems I am having with the graphics and sound. If anyone has any better success, or a better way to do this, please post it here. I also found a third party launcher at [www.grimfandango.net](www.grimfandango.net) that automates the above process, but it is iffy in wine, and causes crashes if you use it to run the game. Let me say that this game really is worth all the effort to get it to run, I played it in windows long ago and it is a very good adventure game. If you can get it to run in Linux, or you dual boot windows, by all means find a copy on Ebay or in the bargain bin. You will be glad you did.

---

### Post by leech on 2006-01-09
By the way, there is a project working on getting this to work natively, [http://www.scummvm.org/subprojects.php](http://www.scummvm.org/subprojects.php)

Leech

---

### Post by ricesteam on 2006-08-07
Hi, Wondering if anyone got this working??

---

### Post by dango on 2006-08-13
ummm, I have one big problem with Grim Fandango. I get to run it on Xp just fine, but in the wine cellar puzzle, the elevator seems to go up A LOT faster than previous times I've played the game! In fact, by the time Manny has gotten his a** up on that forklift, the elevator is already stopped...

Any ideas?

---

### Post by Sammi on 2006-08-14
I've heard about this problem before. Think there is a solution for it, but you'll have to Google for it yourself as I'm too lazy :p

---

### Post by Zalbor on 2006-08-14
That's because you've not installed the patch. It adds some features and is really necessary for any computer with a processor faster than 400MHz. Search for it in [http://support.lucasarts.com/](http://support.lucasarts.com/) .

---

### Post by dango on 2006-08-14
Yeah, I found out about the patch, but I can't download it! I always get the could not connect error message, and all other sites I've found the patch on seems to link back to Lucasarts... Anybody got the patch?

---

### Post by Zalbor on 2006-08-17
I do...

---

### Post by dango on 2006-08-19
Could you mail it to me?

edit: no stress, suddenly I could download it... :)  probably something wrong with my computer.

---

### Post by Eversmann on 2006-08-19
For the known, i played recently grim fandango on windows xp with the patch ans was able to play it and finish it. On the same laptop i have ubuntu, ati xpress 200M, celeron 1.6, etc....

---

