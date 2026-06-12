---
title: "LOW FPS on 3D games..."
date: 2011-12-04
forum: Gaming &amp; Leisure
---

### Post by ahil925 on 2011-12-04
Well, switched from XP to Ubuntu 10.04 Lucid lynx.  A few issues with the wifi, not really much else, till I decided to reinstall a few games.

So far the only one I've reinstalled is Tremulous GPP, and I'm having the damnedest problems with low FPS ingame.  No matter the graphics settings I just cant get above 10-18fps.  Gameplay is choppy and annoying.  When I ran this game under Windows I was doing fine, 50-60fps.

I installed Red Eclipse to try it out, and sure enough, same issue with low FPS.

What gives?

I'm running an IBM T40 laptop with 512mb ram and an integrated 32mb ATI Mobility Radeon 7500 graphics card.

Thoughts?

---

### Post by doorknob60 on 2011-12-04
> **ahil925 said:**
> 
I'm running an IBM T40 laptop with 512mb ram and an integrated 32mb ATI Mobility Radeon 7500 graphics card.

That's like a 10 year old graphics card, it's going to be slow no matter what (not sure how you managed to get such good results from XP though). The only thing I would suggest is to install a lighter Desktop Environment like Xfce and use that instead of Gnome. Also, if you have desktop effects running (Compiz), turn them off.

---

### Post by ahil925 on 2011-12-04
All I did under XP was lower the graphics setting some and Halo CE, Tremulous, and CoD1 all ran fine. I really don't get why switching to Lucid has trashed my performance as much as it has :confused:.  Anyone know if the Ubuntu drivers for the Radeon 7500 don't support 3D options?

---

### Post by WienerWuerstel on 2011-12-05
> **ahil925 said:**
> All I did under XP was lower the graphics setting some and Halo CE, Tremulous, and CoD1 all ran fine. I really don't get why switching to Lucid has trashed my performance as much as it has :confused:.  Anyone know if the Ubuntu drivers for the Radeon 7500 don't support 3D options?


Well the main Reason for it is that Ubuntu and in Linux in general use Open Source Drivers for the older ATI Chips because ATI/AMD dropped the support for your Graphics Chip a while ago. Those Open Source work great but they don't have some of the Features that the proprietary Driver has because of Licenses and Patents. That said you can still have decent 3D Performance with the OS Driver if you set your Desktop to 16 bit and change some Settings in the driconf Tool (Which ma be illegal in some Countries because of Patents).
But don't expect to run any modern 3D Game as the ATI Mobility Radeon 7500 is still a 8 Year old Graphics Chip. 
Games like World of Goo and Defcon should work just fine tough as I have tested them on my own T40 ;)

---

### Post by mastablasta on 2011-12-06
you could try to update the opensource drivers. I know there are some options.
 
easiest way to use latest Xubuntu instead of 10.04. Another way is to add a PPA package to oyur current install. 
Read more here: 
[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)
 
>  
**Getting better 3D support**
 
For r300-r500 (Radeon 9500 - X2300) cards, the r300g driver is a newer 3D driver based on Gallium3D. It is the default 3D driver in Ubuntu Natty/11.04 and newer releases. If you're still running an older Ubuntu release you can add the very experimental [xorg-edgers PPA]("https://launchpad.net/~xorg-edgers/+archive/ppa") Likewise, for r600-r700 cards, the r600g Gallium3D-based driver is available from the xorg-edgers PPA. It is also enabled by default from Ubuntu Natty/11.04 on. 


---

### Post by ahil925 on 2011-12-08
Well, changing to 16bit color depth and using those new xorg packages seems to have impoved FPS a bit, but now I'm running into a different issue.  In both Red Eclipse and Tremulous if I attempt to move AND look around, the camera doesn't pan smoothly.  Instead of seeing the environment pan nicely as my character looks around the image jumps from one angle to another.  If I hold still and look OR just move without shifting my POV then the image is smooth.  Other characters in the games move smoothly, so I'm not sure its a graphics card related issue.

Thoughts?

---

