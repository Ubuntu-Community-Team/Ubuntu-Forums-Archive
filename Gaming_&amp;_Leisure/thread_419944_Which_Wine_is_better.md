---
title: "Which Wine is better?"
date: 2007-04-23
forum: Gaming &amp; Leisure
---

### Post by cogadh on 2007-04-23
I am looking to try running some of my Windows games in Linux again (never been successful before). Should I go with the 0.9.33 version of Wine in the "Cross Platform (Universe)" repository or the latest stable 0.9.35 from the WineHQ repository? Does either offer any significant advantage over the other?

---

### Post by lakersforce on 2007-04-23
I have been experiencing som problems in WoW with versions 0.9.32 - 0.9.34, so I would recommend getting the newest version from winehq. CrossOver and Cedega is essentially Wine with a nice user-interface and auto-help with installing certain applications. But paying just to get that extra (esentially non-useful) functionallity seems like a waste of money.

Unless of course, you are scared of typing simple commands in the terminal and learning in the process (hey, some people are :))

---

### Post by earobinson on 2007-04-23
I would try both, starting with the latest, since some times bugs get introduced

---

### Post by dreadlord_chris on 2007-04-23
> **lakersforce said:**
> I have been experiencing som problems in WoW with versions 0.9.32 - 0.9.34, so I would recommend getting the newest version from winehq. CrossOver and Cedega is essentially Wine with a nice user-interface and auto-help with installing certain applications. But paying just to get that extra (esentially non-useful) functionallity seems like a waste of money.

Unless of course, you are scared of typing simple commands in the terminal and learning in the process (hey, some people are :))

I'm running Crossover 6.0.0-1 and it's only using Wine version 0.9.17. So, they're a few wine vs' behind anyway.

---

### Post by buttons on 2007-04-23
> **cogadh said:**
> I am looking to try running some of my Windows games in Linux again (never been successful before). Should I go with the 0.9.33 version of Wine in the "Cross Platform (Universe)" repository or the latest stable 0.9.35 from the WineHQ repository? Does either offer any significant advantage over the other?

Given the changelog, it would seem (I haven't tested) that DX games would run better under later versions.  The only game I play on wine is CS 1.6, and that seems to have reduced performance on my machine on anything after 0.9.32.  So that's what I've got.

My suggestion is to test.

---

### Post by hyperair on 2007-04-23
I'm using Cedega. and I'm not sure what version of wine it uses, but one thing I do know is that Cedega is meant for gaming and it is a highly modified version of wine, to enhance compatibility and performance with games.

---

### Post by cogadh on 2007-04-23
Thanks for all the suggestions, I've already got KOTOR 2 installed and it did launch briefly (and then crashed and locked my desktop at 800X600), which is already far better than any previous game I have tried with Wine. 

I've looked through the Wine AppDB for any games that are already tested with Wine and there are several that are reported as working, but there is very little info on how they got them working. Can anyone suggest any other sources/sites that may have more detailed info on gaming with Wine?

---

### Post by buttons on 2007-04-23
> **cogadh said:**
> Thanks for all the suggestions, I've already got KOTOR 2 installed and it did launch briefly (and then crashed and locked my desktop at 800X600), which is already far better than any previous game I have tried with Wine. 

I've looked through the Wine AppDB for any games that are already tested with Wine and there are several that are reported as working, but there is very little info on how they got them working. Can anyone suggest any other sources/sites that may have more detailed info on gaming with Wine?

Getting a tad off topic here, but I happen to know that KOTOR2 is one of those games that "just works" with caveats enumerated in cedega's release notes:

Star Wars Knights of the Old Republic II Sith Lords

General Notes

    * The mouse will not be usable unless you disable Hardware Mouse from the launcher configure screen.

Installation Notes

    * At the end of the installer users may be told they need to configure the game when it has already been configured. Exit the installer and re-launch the game to play.

Should be the same for both wine and cedega.

---

### Post by cogadh on 2007-04-23
Unfortunately, KOTOR2 "just doesn't work" for me, which is pretty much the same experience that I have had with everything I have tried to use Wine on, except maybe MSPaint. The KOTOR2 launcher and configuration utilities work fine (except for blank buttons on the launcher), but when I try to launch the game, the LucasArts logo comes up briefly, then minimizes, leaving my desktop locked at a lower resolution. Right now, there is a KOTOR window minimized on my desktop that I can't maximize or or even close.

I found the same information that you list about how it should "just work" and there are apparently a lot of games that "just work", but none of them have ever worked for me. That's why I am wondering if there is more detailed info somewhere that explains how some people can get these games to "just work" when I can't.

For example, the same information on KOTOR2 also says that the installation "just works". Well sure it works... until you need to switch CDs. Since you can't unmount the CD while the install routine is trying to access it, the install can't progress past the first 30% or so. There is no info explaining how to work around this and AFAIK there is no Loki installer for KOTOR2 (can't access the Loki site right now for some reason). I ended up copying my Windows installation of the game into my Wine directory instead of installing it, which is probably why it doesn't work.

I don't mean to rant, but there has been nothing in my Linux experience more frustrating than Wine. Getting Beryl to work was easier than this. The Wine documentation is spotty at best and, more often than not, the documentation you do find is *way* out of date.

Gaming is the only thing that keeps me tied to Windows today. I do all my work, e-mail, surfing and general PC use in Linux, but if I want to play a game, I need to reboot into Windows. I know I'll probably never get every PC game I have to work with Wine, but even if only a few would work, it would be progress.

---

### Post by Jarn on 2007-04-23
While this is for a different game, the same should apply since it's not game-specific. I only had the drive not open when I had cded into the cdrom directory (/media/cdrom) and ran the setup file from there. When I ran it from ~, with ```
wine /media/cdrom/setup.exe
``` it opened fine. Or, alternatively, you could copy all the files from all the disks into a directory somewhere and run it from the directory. That way is probably the easiest, though it may take awhile depending on how many disks there are.

---

### Post by cogadh on 2007-04-23
That method doesn't always work, unfortunately. Since Windows doesn't require you to unmount a drive before ejecting a CD, the InstallShield programmers got lazy and didn't bother programming for an unmount. Depending on the game, it doesn't matter if you Wine from within the CD directory or if you tell Wine to look in the CD directory, it still won't let you swap CDs. For example, KOTOR 1 installs perfectly and allows you to swap CDs as if you were running from within Windows (just finished installing it), while KOTOR 2 does not.

The copying files to the local drive has never been successful for me, since most current copy protection routines already account for that. I'm always willing to try, so I'll give it another shot.

---

### Post by Jarn on 2007-04-23
Good luck.

---

### Post by hyperair on 2007-04-23
Oh I had that problem with Kotor2, yes xD. Try forcing an unmount, or even using the lazy unmount command ^^. That worked for me. 

Use either command: 
sudo umount -f /dev/cdrom0 (preferable)
sudo umount -l /dev/cdrom0 (may not mount next cd correctly)

Anyhow I managed to finally install KOTOR2 on Wine, but never got round to playing it. And it was taking up so much disk space I just scrapped it.

---

### Post by barmazal on 2007-04-23
Cedega ans Crossover find solutions in which regular wine will put an error, it's not just user friendly interface behind those apps but hundreds lines of code to rewrite Windows files to make each application they claim as working under their app actually working.

Ive seen quite a few real wine's user interfaces but i prefer to do stuff which programmed for Windows on Windows. I'm sorry but even open source Linux native games look much better on Windows systems, seems like whole graphics issue is much more powerful for widely used OS. You simply cannot expect to see person to do his paid job as open source one. Which brings us back to Cedega and Crossover.

---

### Post by cogadh on 2007-04-23
At this point I have tried four different games that are all reported as working in Wine's AppDB:
Star Wars Knight of the Old Republic - rated gold - installed, won't run
Star Wars Knights of the Old Republic II: The Sith Lords - rated gold - installed, won't run   
Vampire: The Masquerade - Redemption - rated silver - crashed during install
Call of Duty - rated gold - installed via Loki script, crashes after launch

Once again, I spent most of the day Googling the cryptic messages that are left in the terminal after a Wine app crashes and once again I have found a whole lot of nothin' to help me. It seems plenty of people have the same problems as me with these games, but there is no single source for definitive answers. Most of the Wine Wiki is just incomplete cut and paste from forum posts and that "User Guide" is a joke. Sure it tells you what to do, but it never tells you *how to do it*!

I know Cedega is reportedly a lot more user friendly, but is it still a pain in the butt to compile from source?

---

### Post by buttons on 2007-04-23
I don't mean to insult you, but if nothing works, do you have direct rendering working for your card?  Do you have an ATi card?  Are you running ESD or aRTs?  Do native games work?

---

### Post by hyperair on 2007-04-24
@cogadh: I think there are Cedega debs available for Ubuntu, so I never tried the experience of compiling it myself ^^

---

### Post by Sammi on 2007-04-24
The official proprietary drivers for ATI cards are a pain in the ***.

---

### Post by cogadh on 2007-04-24
> **buttons said:**
> I don't mean to insult you, but if nothing works, do you have direct rendering working for your card?  Do you have an ATi card?  Are you running ESD or aRTs?  Do native games work?

I have an nVidia GeForce FX 5200 card with the 9755 drivers, rendering works great, I'm running ALSA and native games work great. 

> **hyperair said:**
> @cogadh: I think there are Cedega debs available for Ubuntu, so I never tried the experience of compiling it myself ^^

Do you know what repository has the Cedega debs? It's not part of the default or the usual Universe/Multivers reps. I refuse to pay Transgaming for this product until I have a chance to try it, so I can't get it from them. If it works, then maybe it will be worth the subscription fee. Last time I wanted to try it, my only option was to compile it from the CVSCedega source, and that did not go well at all.

How's this for irony; Last night I decided to give KOTOR 1 another try and it actually launched. The sound didn't work, but I was able to get into gameplay finally. The ironic part is I didn't make any changes. All I did was try launching it one more time and for some reason it decided to work. Of course today it's back to the same old launch, show the LucasArts logo then crash...

---

### Post by hyperair on 2007-04-24
There are *koff* torrents *koff koff koff*. I"m not sure if I'm allowed to post links, but for my own safety I shan't. If you want the torrent, PM me, or go search in any torrent site.

---

### Post by cogadh on 2007-04-24
In case anyone was wondering, CVSCedega is still a pain in the butt to install. The install script from Linux Gamers.net doesn't work, so you need to do it the old fashioned way, which generally requires a computer science degree to get it right.

EDIT - As a matter of fact, it appears that CVS Cedega is no longer maintained and hasn't been since 2004 (probably the last time I tried it). Looks like I'll be sticking with Wine for now.

hyperair, thanks for the offer, but I'd rather not resort to *koff* questionable *koff koff koff* torrents right now.

---

### Post by hyperair on 2007-04-24
Questionable indeed. Afraid of malware popping in through the torrent? I'd be really happy if I could even find a single malware in Linux. It would be the chance of a lifetime to see one, most definitely.

---

### Post by bluehue on 2007-04-24
I'd go with the latest version, 0.9.35, as it allows you to play S.T.A.L.K.E.R.

---

### Post by cogadh on 2007-04-24
Thanks for all the help people, it looks like I will be focusing on getting Wine 0.9.35 to work. Since this post got kind of off-topic a bit, I started a new post for my ongoing problems with Wine:
[http://ubuntuforums.org/showthread.php?t=421652](http://ubuntuforums.org/showthread.php?t=421652)

---

