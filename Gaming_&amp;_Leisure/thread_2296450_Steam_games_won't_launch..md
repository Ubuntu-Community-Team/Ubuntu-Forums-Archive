---
title: "Steam games won't launch."
date: 2015-09-25
forum: Gaming &amp; Leisure
---

### Post by chance8 on 2015-09-25
I just got a new gaming PC and decided to try out the latest version of Ubuntu instead of purchasing a copy of Windows which is my preferred OS. 

So far, I'm finding Ubuntu extremely confusing. The problem I'm having is that I can't launch any games. I first tried playing Rocket League through Steam on PlayOnLinux, but it just wouldn't start. At first I thought the problem was that I wasn't doing something right with PlayOnLinux, but then I installed Terraria through normal Linux Steam and tried to run it, but it just won't launch. I don't get an error message or anything. When I try to launch it, it brings up a box that says "Preparing to launch Terraria..." but it quickly closes and nothing happens. 

I really like the look of Ubuntu and how it runs and everything, but the main reason I got this PC was to game. If someone could please help me out with what I'm doing wrong or what I'm not doing when it comes to PlayOnLinux and normal Steam, it would be greatly appreciated. 

Also, sorry if this isn't the right section to post this thread in, I apologize.

Thanks in advance.

---

### Post by Geoffrey_Arndt on 2015-09-25
It's always best to confirm what hardware specs you have (especially gpu & ram).   Also, assuming you've installed the proprietary drivers (via System Settings>Software & Updates>Additional Drivers tab.

Also, did you install the "restricted-extras" package from the ubuntu software center?     

As I'm not a gamer, the above is just a place to start - - but as I read lately, there are now over 1500 steam games available for Linux (and a few other native games and legacy ports.).   Others here at Ubu Forums will provide more info.

---

### Post by chance8 on 2015-09-25
Hardwarespecs:

MSIH81M-P33 Motherboard
intelPentium G3258 Processor
WesternDigital Caviar Blue 250GB 3.5" 7200 Hard Drive
G.SkillRipjaws X 1 x 4GB RAM
ASUSRadeon R7 260x 2 GB Video Card

Ihave installed the "restricted extras" package as well asthe proprietary drivers. 

But now I have more problems to deal with......

I restarted my PC and when everything loaded up, I see I'm stuck at 1024x768 resolution and can't seem to change it. Also, in the additional drivers, everything but "Continue using manually installed driver" is greyed out. ](*,)

*Edit*

On the bright side, for whatever reason, my game is now opening...

*Edit* 

The game is not showing my cursor and has weird....Textures I guess?? It just looks really weird haha. Im assuming that's probably due to the resolution and driver issue but I honestly have no idea what's going on...

---

### Post by Geoffrey_Arndt on 2015-09-26
a).   what version of ubuntu?
b).   did you install the graphics drivers from the ubuntu repo's or from the vendor's website? (re the source of the drivers). 

If using non-ubuntu source, you'll have to purge the original drivers before trying to re-install the proper ones.

---

### Post by howefield on 2015-09-26
Thread moved to the "*Gaming & Leisure*" forum.

---

### Post by chance8 on 2015-09-26
I ended up just completely reinstalling Ubuntu and everything seems to be working fine now. Not entirely sure what I did wrong in the first place to mess everything up, but I got it working now.

---

### Post by Geoffrey_Arndt on 2015-09-26
Just remember to install all apps from the Ubuntu Software Center, or the Synaptics Package Manager . . . with only the official servers (repos) checked.     After some experience, trusted PPA's (personal package archives) can also be used to either install an app that's not in the official repos, or to install a later version of any app.   (as only bug and security fixes are possible within a release cycle) . . . if that's not clear, let us know.

---

### Post by campanella-alex on 2015-09-27
if the main reason you got the PC is to game then you gotta go with Windows.  Sorry man there's no way around it.
If you're clever, you can play any/all windows games on Ubuntu, but never as fast as running Windows native.  Meaning if it's not available on Linux (most games) you'll have to use Wine or a virtual machine.  Virtual machines suck a lot of RAM and CPU and the graphics are normally glitchy.  Wine can sometimes be excellent however.  For older games, like Starcraft or Warcraft 3 I can play on Wine super smooth, actually even better than Windows.  But newer games I won't even bother to try.

However running Steam games on Linux should be easy.  Don't use PlayOnLinux!!! just download Steam on Linux!!!  I play TF2 every day natively on Linux with no problems.  It's a little choppy once in a while but not enough to stop me from playing.  My computer is also not very good, so even on Windows it would not be much different.

---

### Post by campanella-alex on 2015-09-27
Also people have been having a lot of trouble installing steam through the package managers (including myself)
with steam, you're best bet now is to download the .deb from the steam website.

Just double click on the .deb and it will install through the Ubuntu Software Center.  Please note, this is the NEWEST version and not actually available on the software center if you search for it.

---

