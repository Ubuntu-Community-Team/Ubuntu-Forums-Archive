---
title: "World of Warcraft (WoW)? which instructions to use"
date: 2006-10-26
forum: Gaming &amp; Leisure
---

### Post by MemoryDump on 2006-10-26
hi all,

I'm really really trying to hard to switch to Ububutu full time however I still can't seem to get WoW running. I've tried numorous tutorials and read several threads on "HOW TO" get WoW running however I still haven't been successfull.

With all the threads posted on this forums it's very hard to tell which one is the best one to follow.

I have sucessfully installed Ubuntu on my worstation along with the latest updates. I believe I did manage to get the Nvidia drivers running as I get the logo when I login and doing glgear tests the FPS are really high.

I have a NVIDIA GeForce 7800 GS (AGP) on a P4 3.02 system with 2gigs of RAM. So my system is pretty good and shouldn't have any issues. Everything works perfectly under Windows however with Vista coming out soon.. I'd like to support the linux ppl more :P
(yes I know I could multi-boot.. but that's a pain in the butt too)

thanks

---

### Post by MemoryDump on 2006-10-27
nobody can share with me which instructions worked best for them? 
recommendations? workarounds?

there are so many threads that I don't which one stick with.. and I've tried a few.. but I've yet to get WoW working.

:-k

---

### Post by hikaricore on 2006-10-27
Things I (or anyone else) would need to know before we could provide advise:

[COLOR="Red"]*[/COLOR] What color depth is X running in.
[COLOR="Red"]*[/COLOR] Does the output of "glxinfo | grep rendering" return Yes?
[COLOR="Red"]*[/COLOR] Which version (build) of wine are you using?
[COLOR="Red"]*[/COLOR] Are you using a modified config.wtf file or a default.
[COLOR="Red"]*[/COLOR] Are you starting WoW with -opengl flag or -d3d flag.
[COLOR="Red"]*[/COLOR] What happens (if anything) when you attempt to run:
[INDENT]    [/INDENT]"wine /location/of/wow.exe -opengl" or "wine /location/of/wow.exe -d3d"
[COLOR="Red"]*[/COLOR] What do you see (if anything) if/when the game loads.
[COLOR="Red"]*[/COLOR] Do you have all of your mods disabled (this can help if the game won't load at all).
[COLOR="Red"]*[/COLOR] Are you running a fresh install of WoW on a linux based file system or are you accessing it via a read only NTFS drive (this can impact performance and even cause the game to crash with weird errors).
[COLOR="Red"]*[/COLOR] Are you running _ANY_ desktop extentions that make use of direct rendering (beryl or compiz for example).
**[COLOR="Red"]*[/COLOR] Any other information you think might be useful, and I'll do my best to help.**

---

### Post by Ferrat on 2006-10-27
IMO the best help you can get is at 

[http://appdb.winehq.org/appview.php?iVersionId=5606](http://appdb.winehq.org/appview.php?iVersionId=5606)

Use the how to there to get wow running, worked like a charm for me atleast, hope it helps

---

### Post by glave on 2006-10-28
I am in the same boat here, although I admit I haven't even BEGAN to look. I decided yesterday to make the switchover, so today I got everything installed, been tweaking all morning (all mouse buttons on my mx1000, firefox32 w/ flash, etc) and I've now begun to dig a little on getting WoW going.

---

### Post by DraeLee on 2006-10-28
> 
IMO the best help you can get is at

[http://appdb.winehq.org/appview.php?iVersionId=5606](http://appdb.winehq.org/appview.php?iVersionId=5606)

Use the how to there to get wow running, worked like a charm for me atleast, hope it helps

I agree with Ferrat these are the compiling instructions i used.  I installed Wow on windows first and then copied it over to my fat32 partition i uninstalled all versions of wine and then compiled with patch per instructions from site above and then ran wine WoW.exe -opengl and it works fine I still got crappy fps but it is playable.  Until I can figure that out and get my sound correct its ok.  

Hope that helps

---

### Post by Tulwinn on 2006-10-31
PLease ignore this, solved it myself

---

### Post by StomUK on 2006-10-31
Have you managed to get it working with no problems on Ubuntu 6.10? I have tried the newer 0.9.24 wine and I get a crash as soon as I try and get WoW to run. 0.9.23 of wine used to give graphical problems.

spec wise i am running pretty much the same spec as you as far as graphics cards go 7800GS agp card)

---

### Post by Ferrat on 2006-10-31
> **StomUK said:**
> Have you managed to get it working with no problems on Ubuntu 6.10? I have tried the newer 0.9.24 wine and I get a crash as soon as I try and get WoW to run. 0.9.23 of wine used to give graphical problems.

spec wise i am running pretty much the same spec as you as far as graphics cards go 7800GS agp card)

Ubuntu 6.10 doesn't work well with wine and the new 0.9.24 has a regression on the openGL drivers so for easiest go with Dapper and Wine 0.9.23

---

### Post by reiki on 2006-10-31
I've been working on this in the appdb with some maintainers. 
I have tried simply swapping a the winex11.drv.so from a compiled 9.23 and 9.24 that was compiled WITH the "flicker patch" for nVidia cards. No go.

One of the things that has come up is that if we compile 9.24 using gcc version 4.1 (the default for Edgy), World of Warcraft does not run. However it (so far) looks like it will compile successfully using gcc version 3.4 and run. ( ./configure CC=gcc-3.4 ).

This will be a whole lot easier once someone does a pre-patched-for-nvidia-WoW version of wine. Not sure I'm smart enough to do that and not sure how long it would take me to learn how to make a proper .deb. Have to finish testing first to make sure we can patch, compile, and then run WoW. Once I know the correct combination I may be of more help.

---

### Post by Ferrat on 2006-11-01
> **reiki said:**
> I've been working on this in the appdb with some maintainers. 
I have tried simply swapping a the winex11.drv.so from a compiled 9.23 and 9.24 that was compiled WITH the "flicker patch" for nVidia cards. No go.

One of the things that has come up is that if we compile 9.24 using gcc version 4.1 (the default for Edgy), World of Warcraft does not run. However it (so far) looks like it will compile successfully using gcc version 3.4 and run. ( ./configure CC=gcc-3.4 ).

This will be a whole lot easier once someone does a pre-patched-for-nvidia-WoW version of wine. Not sure I'm smart enough to do that and not sure how long it would take me to learn how to make a proper .deb. Have to finish testing first to make sure we can patch, compile, and then run WoW. Once I know the correct combination I may be of more help.

The OpenGL in 0.9.24 is still broken I guess since I compiled 0.9.24 in Dapper and OpenGL crashes everytime wine 0.9.24 tries to run WoW, the memory mapping is wrong, or atleast that's what WoW feels is the problem =(

---

### Post by StomUK on 2006-11-01
Hopefully we will get a working version for Edgy at some point then. I have tried numerous compiling options myself now (even though I am beginner) and still dont get very far with it all. Even the flicker patch doesnt work half the time for me :)

Latest one off the budjetdedicated just crashes out WoW as soon as I try and start it up. The ones i have made myself so far start up WoW and everything, its just unplayable after that :/

Give it a few more days i guess and a solution will be found I hope :)

---

