---
title: "Full Screen games are garbled"
date: 2008-10-25
forum: Gaming &amp; Leisure
---

### Post by judasg0at on 2008-10-25
Hello all,

I am a long time reader, but a first time poster. Anyways, I just got a brand spanking new machine. The specs are:
Gateway LX6200
Phenom 4x 9500
8Gb Ram
ATI HD3200 on board graphics
Gateway HD2201 Widescreen Monitor

Anyways, I have several games installed and although they start, the screen is all mangled up. Most of the time it looks like a refresh rate issue, but I am not sure. All of the games have sound, and seem to actually be working, they are just not displaying correctly.

The games I have tried are:
Scorched3d
Alien Arena
Prey (Demo)

All three of these start up, and (thankfully) the gui for Alien Arena is predictable, the exit button seems to be at the bottom of the screen. I can see a yellow bar that is all mangled when I start Alien Arena, so i press the down arrow to select the lower most box, and then press enter. Presto Bango, I get sent back to the desktop, and everything is ok again.

I had compiz fusion up and running. It worked Well, got the rotating cubes and the Fire etc... Anyways, I synaptic removed compiz, thought It might be a compatibility Issue. I am using x64 Ubuntu Intrepid (8.10) and everything seems to be working well. I have checked the /var/log/Xorg.0.log, and there is noooo mention of anything related to a graphics error. I have also run fgl_glxgears, and it runs very well in windowed mode. I can play movies well enough in full screen, so I am not sure what else to say. 

I have the specs for my monitor somewhere. I have tried to manually set up a custom refresh rate setting for Xorg.conf because I thought that would be the problem, but I am not sure I set that up correctly.

Any help would be greatly appreciated.

Monitor specs:
UltraResponse disabled: 5 ms (typical)
Frequency Rates 48 - 76 Khz (horizontal)
24 - 83 Hz (vertical)
Colors 16.7 million 


Here is my Xorg.conf File:
Section "Monitor"
	Identifier   "aticonfig-Monitor[0]-0"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]-0"
	Device     "aticonfig-Device[0]-0"
	Monitor    "aticonfig-Monitor[0]-0"
	DefaultDepth	24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "Module"
	Load  "glx"
EndSection

Section "ServerLayout"
	Identifier     "Default Layout"
	Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]-0"
	Option	    "UseFastTLS" "1"
	BusID       "PCI:1:5:0"
	Driver	"fglrx"
EndSection

---

### Post by Ripfox on 2008-10-25
I am having this exact problem with ATI Radeon X1200. Windowed mode only on all 3d games including Nexuiz, Regnum.

---

### Post by judasg0at on 2008-10-26
Bump

Anyways, I went to the screen resolution center and changed it to all of the options available (There are many) and all of them work. From what I have read I am starting to expect that this is an ATI driver issue.

I will try to get some screen shots up of the issue, maybe someone else will have an idea of what is going on. Maybe this would be better posted on the Phoronix Forums?

I dont see how all of the resolutions would work and yet I would end up with a refresh rate issue when a game goes full screen. Additionally I am having a heck of a time getting games to run in windowed mode. I found the area to set it in Alien Arena, changed it, but the results were the same. So it sounds like a driver issue, but then again.... Why does compiz fusion run flawlessly?

Utterly confused.

---

### Post by schnauzer93 on 2008-10-28
I also have this issue. I have a X1200 series also; however, I manually updated my driver to 8.54.3 using ATI's script. 

dmesg | grep fglrx output:
```
[   32.900565] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[   32.918173] [fglrx] Maximum main memory to use for locked dma buffers: 1776 MBytes.
[   32.918186] [fglrx]   vendor: 1002 device: 791e count: 1
[   32.918229] [fglrx] ioport: bar 4, base 0xee00, size: 0x100
[   32.918480] [fglrx] PAT is enabled successfully!
[   32.918497] [fglrx] module loaded - fglrx 8.54.3 [Oct  3 2008] with 1 minors
[   41.271503] [fglrx] GART Table is not in FRAME_BUFFER range 
[   41.274393] [fglrx] Reserved FB block: Shared offset:0, size:1000000 
[   41.274400] [fglrx] Reserved FB block: Unshared offset:7ffb000, size:5000 
```

---

### Post by Ripfox on 2008-10-30
Bump on this important issue. I can no longer play WoW because of this!

---

### Post by tbobo05 on 2008-10-31
I seem to be having the same problem with my ATI Radeon X1250 card BUT I am runnign XFCE. This happens with ANY game requires hardware 3d acceleration.  I have tried both WINE and Crossover to run the games.   (Thanks to the Lame Duck Challenge)

The game(s) seem to be running fine from listening to the audio but the screen has a bunch of horizontal lines in it.  Maybe its a vertical refresh setting error?  I have tried proprietary ATI drivers and the free drivers as well.  All Fglx Gear tests run great with 200-250 FPS.  

Was having the same problem on GNOME with Ubuntu 8.04 but disabling Compiz seemed to remedy the problem.  Disabling Compositor in XFCE does not help.  

I will be putting more time in to trying to solve the problem this weekend hopefully.  If I can come up with a solution that helps me I will post.


Bobo

---

### Post by pakenzo on 2008-10-31
I have the same problem when updating kde , before this, any problem, Urban Terror , Nexuiz and other games were running correctly, so the problem might be the drivers? 
I have an 1200x too, but until now i played games,,,

---

### Post by Huitogi59 on 2008-10-31
I'm going to bump the tread up.cheap wow power leveling (World of warcraft Power Leveling):**buy [WoW Power Leveling](http://www.igsstar.com),  cheap [world of warcraft power leveling](http://www.igsstar.com/wow-powerleveling-us/) , 1-80 level [wow Power Leveling](http://www.wowgoldweb.com),[maple story mesos](http://www.buymsmesos.com),       [wedding invitations](http://www.vponsale.com/invitations/)**

---

### Post by Ripfox on 2008-11-01
Anybody else? This is really harsh! :(

---

### Post by VicViper on 2008-11-01
> **pakenzo said:**
> I have the same problem when updating kde , before this, any problem, Urban Terror , Nexuiz and other games were running correctly, so the problem might be the drivers? 
I have an 1200x too, but until now i played games,,,
Same here.

---

### Post by gnulogic on 2008-11-01
same problem here ati radeon 3200, intrepid x64.  I did a little research on the net and I think it might be related to the new x.org

---

### Post by judasg0at on 2008-11-04
Hello again!

Ok, so I have been doing some looking around and it looks like I get the same result whether or not Compiz fusion is running, so I have it enabled again for now, but if anyone comes across a fix for this let me know. 

I tried to get some screen shots, by going to Applications -> Accessories -> Take Screen shot. And while there is a medium sized black box on the screen there is nothing resembling the view that I am acutally getting on my screen. From my perspective it almost looks like the screen has changed resolutions, but I'm pretty sure it isnt actually changing resolution because by monitor usually flashes a note saying that the resolution changed, and that isnt happening.

Just being curious I noticed that there are a few notices that pop up when I start Compiz Fusion, and I will share them now, to see if anyone can piece together the information.

Compiz Startup

Checking for Xgl: not present. 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1680x1050) to maximum 3D texture size (8192): Passed.
Checking for Software Rasterizer: Not present. 
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format.

---

### Post by Ripfox on 2008-11-07
Bump.

This even happens when I start Elisa in full screen mode. There sems to be no explanation except that it has to do with the ATI cards.

---

### Post by westomopresto on 2008-11-07
> **Ripfox said:**
> Bump.

This even happens when I start Elisa in full screen mode. There sems to be no explanation except that it has to do with the ATI cards.

i had the same problem with my game 
Blockland
but i fixed it with the drivers...
im not sure if my comment helped. but i hope it springs a idea 
good luck mate ;P

---

### Post by Karilex on 2008-11-07
I used to have the same problem with another computer but it got solved by disabling desktop effects but I don't think this is the case here try it anyway hope it helps at least one person

---

### Post by judasg0at on 2008-11-07
I found another thread dealing with simular issues on the HD3200, there is a screen shot of the problem that is "Creepy" similar to the things that I am seeing. These issues are undoubtedly related or the same. Maybe someone could take a look at this and tell me what they think?

-With any luck the new drivers will be coming out in a few weeks, but who knows.

-judas


[http://forum.boxee.tv/showthread.php?t=1383&page=2]("http://forum.boxee.tv/showthread.php?t=1383&page=2")

---

### Post by Ripfox on 2008-11-07
> **judasg0at said:**
> I found another thread dealing with simular issues on the HD3200, there is a screen shot of the problem that is "Creepy" similar to the things that I am seeing. These issues are undoubtedly related or the same. Maybe someone could take a look at this and tell me what they think?

-With any luck the new drivers will be coming out in a few weeks, but who knows.

-judas


[http://forum.boxee.tv/showthread.php?t=1383&page=2]("http://forum.boxee.tv/showthread.php?t=1383&page=2")

Yes...this is exactly the same problem I get on-screen. It has nothing to do with Compiz. I have tried that (although I never use them b/c they are kind of useless) It only happens in full screen mode.

---

### Post by judasg0at on 2008-11-08
Ok so BIG news, I have made some major headway on this issue. I was browsing a forum:

[http://xbmc.org/forum/showthread.php?t=39717&page=3]("http://xbmc.org/forum/showthread.php?t=39717&page=3")

And I came across a person that ran the graphics program with "sudo" and it worked. Well guess what, I tried it and it also WORKED!!! so I tried sudo ./crx to play Alien Arena and presto blamo I got my first honest to goodness linux gaming experience. WHOOO HOOOO

Maybe someone smarter than me can figure out what sort of permissions issue is allowing this?

---

### Post by murlosad on 2008-11-08
> **judasg0at said:**
> Ok so BIG news, I have made some major headway on this issue. I was browsing a forum:

[http://xbmc.org/forum/showthread.php?t=39717&page=3]("http://xbmc.org/forum/showthread.php?t=39717&page=3")

And I came across a person that ran the graphics program with "sudo" and it worked. Well guess what, I tried it and it also WORKED!!! so I tried sudo ./crx to play Alien Arena and presto blamo I got my first honest to goodness linux gaming experience. WHOOO HOOOO

Maybe someone smarter than me can figure out what sort of permissions issue is allowing this?

that seems to do the trick for me too. this warrants some more investigation as to why the permissions are all messed up for openGL applications.

but I was able to run Unreal Tournament (finally) with this card albeit not very well, but that's not a driver problem I don't think.

---

### Post by mpie on 2008-11-09
try this replace username with your user

sudo gpasswd -a username video

seems the dri nodes are owned by videogroup....

---

### Post by judasg0at on 2008-11-10
Adding my username to the video group didn't do the trick. I have an added partition that I am going to try a fresh install on and see if it makes a difference, so well see. Though, to tell the truth I am on a basically fresh install already, and have had this problem even before I upgraded to Intrepid.

I might need to try more games. I have a question though, as I said before "Compiz Fusion" has always run well, does it have some other permission set on default? Running games as root (Bad Idea) makes them work, maybe compiz never had problems because of the same thing? If this is a simple matter of chmodding a few graphics driver files then we may be getting close to a fix.

-judas

---

### Post by thatsPipe on 2008-11-11
I'm also getting this problem. I have a Toshiba Satellite laptop with a Radeon X1250 (although lspci -vv reports : 01:05.0 VGA compatible controller: ATI Technologies Inc RS690M [Radeon X1200 Series]) Fullscreen OpenGL apps were running fine before I updated to Intrepid. Has anyone filed a bug report?

---

### Post by MikeyUbun2 on 2008-11-11
it seems 8.10 is screwing a lot of people over. when i switched this started happening to me aswell i still havent found a fix for it though.
I might switch to a different distro if this doesnt work (if i get desperate enough)

---

### Post by Ripfox on 2008-11-12
Yes running them as root circumvents the problem...but what the hay is going on here?

---

### Post by judasg0at on 2008-11-13
An interesting thing happened last night. I had a spare partition available, so I reinstalled Ubuntu 8.04 (Hardy)x64 on it, got the video drivers automatically from the restricted repository and my games started working. I even got to the main screen for the Prey demo up and running, though the game itself crashed when I tried to start it up.

It seems that between our suspicions over a permissions issue with the ATI divers and my new results with a fresh install this may be SOLVED. I think what happened was that I tried to manually install the restricted drivers from the AMD website, and then ended up later going back to the default restricted drivers in the repositories.

I will mark this as solved once I get someone elses opinion.

-Edit: We may want to find a way of fixing this issue without doing a complete wipe/reinstall. Other things to note are that I had upgraded to the Intrepid Beta, and went around adding my main user to different groups randomly trying to get past the permissions issue. So, It may actually be an Intrepid issue, more likely it is a consequence of having installed multiple copies of the ATI drivers though.

---

### Post by gnulogic on 2008-11-16
running urban terror as root from the terminal fixed the problem for me.  thanks.  just cd in to the games directory.  Then sudo ./entergamesnamehere  this will run the game as root not a secure thing to do but it works.  MY frame rates are like 12 per second do I have to revert back to hardy.  I dont think 3d acceleration was working somthing is still wrong.

---

### Post by Ripfox on 2008-11-19
This is definitely not "solved" if we have to run games as root. This is just not an acceptable answer, although it is progress in finding out the real problem. Anybody else?

---

### Post by Rhemat on 2008-11-20
I have a similar problem when I try to play Quake 3, Doom 3, Quake 4, and the demo for Quake Wars:  Enemy Territory in full screen in a widescreen resolution.
My computer specs are an MSI RX2400Pro, Acer AL1917W widescreen monitor (1440x900 resolution).
I can play the games fine in a 4:3 resolution, and the game gives me the proper field of view, so it does play widescreen.  The problem is that if I want to take a screen shot, then it either saves a crunched picture (Quake 3) or cuts off a bit of each side (Doom 3 and Quake 4).
If there is any more information you need from me, let me know.
Thanks in advance.

---

### Post by xnevermore on 2008-11-20
I'm experiencing the same issue. Here is the related Launchpad bug report: [https://bugs.launchpad.net/bugs/292858](https://bugs.launchpad.net/bugs/292858). Please add developments there.

---

### Post by Ripfox on 2008-11-20
Read the reports on Launchpad and all they have is the same answer i.e. run as root. No can do with Wine apps, too dangerous!!

---

### Post by dsfdfewrgf on 2008-11-21
> **judasg0at said:**
> Bump

Anyways, I went to the screen resolution center and changed it to all of the options available (There are many) and all of them work. From what I have read I am starting to expect that this is an ATI driver issue.

I will try to get some screen shots up of the issue, maybe someone else will have an idea of what is going on. Maybe this would be better posted on the Phoronix Forums?

I dont see how all of the resolutions would work and yet I would end up with a refresh rate issue when a game goes full screen. Additionally I am having a heck of a time getting games to run in windowed mode. I found the area to set it in Alien Arena, changed it, but the results were the same. So it sounds like a driver issue, but then again.... Why does compiz fusion run flawlessly?

Utterly confused.

i agree with you , and i have the same problem as you , and i am also confused

---

### Post by freevryheid on 2008-11-22
Same problem here. I have the ATI X1200 on a Toshiba Satellite laptop. AMD64. Running Ubuntu 8.10. No compiz - and no visual effects. ATI restricted driver activated.

Not able to get my opengl, glut or glfw developed apps to go fullscreen - been like this from the get go.

Tried two of the "solutions" reported above. Neither worked.

1. There was no video group. I created one and added user to this but it didn't help.
2. Running as sudo doesn't help.

Solution:
Deactivate the FGLRX Hardware Driver.

---

### Post by Ripfox on 2008-11-24
> **freevryheid said:**
> Same problem here. I have the ATI X1200 on a Toshiba Satellite laptop. AMD64. Running Ubuntu 8.10. No compiz - and no visual effects. ATI restricted driver activated.

Not able to get my opengl, glut or glfw developed apps to go fullscreen - been like this from the get go.

Tried two of the "solutions" reported above. Neither worked.

1. There was no video group. I created one and added user to this but it didn't help.
2. Running as sudo doesn't help.

Solution:
Deactivate the FGLRX Hardware Driver.

That would be fine and dandy if I didn't need it for the games I wish to be full screen there fella. Catch 22.

---

### Post by Ripfox on 2008-11-24
bump

---

### Post by jamesrfla on 2008-11-24
Not sure if this was mentioned but has anyone tried turning off compiz if they have it turned on?

---

### Post by Ripfox on 2008-11-25
Doesn't work.

---

### Post by judasg0at on 2008-11-25
I just wanted to double check to see if anyone has tried my suggestion of reinstalling x64 Hardy. It worked for me. I still haven't stepped up to intrepid yet, but everything else now works. I still have that flickering problem with compiz on when I am in full screen though, but that is a separate issue.

---

### Post by monraaf on 2008-12-03
Same problem here with a Radeon HD 3200 IGP on Intrepid. It doesn't look like a permission problem to me.

user:
```

geteuid32()  = 1000
getuid32()   = 1000
open("/usr/lib/dri/fglrx_dri.so", O_RDONLY) = 9

```

root:
```

geteuid32()  = 0
getuid32()   = 0
open("/usr/X11R6/lib/modules/dri/fglrx_dri.so", O_RDONLY) = -1 ENOENT (No such file or directory)

```

So the dri module doesn't even get loaded when you run an OpenGL application as root.

Also there is a new fglrx driver in Intrepid proposed, anyone tried it yet?

---

### Post by monraaf on 2008-12-03
I just installed the new fglrx driver from intrepid-proposed and the problem is gone!

---

### Post by MikeyUbun2 on 2008-12-04
is may be no help at all but when i start toribash it is fine for approxomately 0.6 seconds THEN it gets scrambled. and it is windowed.
it gets scrambled for many other games too either fullscreen or not.
I can play just fine on 8.04 LTS in fullscreen or not but i hate it because every 10 mins the screen changes funny colours and freezes then i have to restart. 8.10 is screwing me over!!! :(

---

### Post by freevryheid on 2008-12-14
Install the new intrepid driver  - steps available here:

[http://wiki.cchtml.com/index.php/Ubuntu_Intrepid_Installation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Intrepid_Installation_Guide")

Fixed my ATI Radeon X1200. Q4 and ET work now.

---

### Post by TwoEyesOnly on 2008-12-15
I was having the same problem with a Radeon 3200 (builtin video on the Asus M3A-H/HDMI motherboard.)   First time it showed up is with stellarium.. tried to switch to full screen and it gave me that garbled screen... then I tried running alien arena.. same deal.

Updated to the latest fglrx in the proposed repository as the previous commenter suggested and it's working fine now!

---

### Post by PatchMonster on 2009-03-12
The FGLRX driver wouldn't let me do full screen on Guild Wars, but after installing the proprietary driver from AMD it works just like on Windows, with Wine of course.
[URL="http://support.amd.com/us/gpudownload/Pages/index.aspx"]
Link to ATI's drivers[/URL]

The 1200 series isn't listed under Linux, so just use 1300 if you're using that card.  It worked fine for me.

---

### Post by judasg0at on 2009-03-18
It WORKS!!

Hey everyone, I wanted to run down the steps that worked for me (not all of them may be necessary) First I went to: 
[http://wiki.cchtml.com/index.php/Ubuntu_Intrepid_Installation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Intrepid_Installation_Guide")

I followed the instructions there. The important thing (I think) is the first step, because I have x64 architecture I ran this command instead:

sudo apt-get install build-essential fakeroot dh-make debhelper debconf libstdc++5 dkms ia32-libs

The only difference is that it includes ia32-libs install. Then I went here:
[http://wiki.cchtml.com/index.php/9.2]("http://wiki.cchtml.com/index.php/9.2")
And downloaded the Catalyst 9.2 drivers. Next I went to the terminal and ran this command (Also from the instructions listed in the first link.) 

sudo sh ati-driver-installer-8-3-x86.x86_64.run --buildpkg Ubuntu/intrepid

Finally, and very importantly, I used TAB completion to make my final command:

sudo dpkg -i xorg-driver-fglrx_8.582-0ubuntu1_amd64.deb fglrx-kernel-source_8.582-0ubuntu1_amd64.deb fglrx-amdcccle_8.582-0ubuntu1_amd64.deb 

*Previously I had tried this method and tutorial and It didnt work. What made it work better this time is using the tab completion to keep from fat fingering the command. 

The new drivers for 9.2 are kicking butt! I can play games that I couldnt even play when I had Hardy only. If this works for anyone else please let me know.

-Judas

---

### Post by The-IRS on 2009-03-18
> **judasg0at said:**
> Bump

Anyways, I went to the screen resolution center and changed it to all of the options available (There are many) and all of them work. From what I have read I am starting to expect that this is an ATI driver issue.

I will try to get some screen shots up of the issue, maybe someone else will have an idea of what is going on. Maybe this would be better posted on the Phoronix Forums?

I dont see how all of the resolutions would work and yet I would end up with a refresh rate issue when a game goes full screen. Additionally I am having a heck of a time getting games to run in windowed mode. I found the area to set it in Alien Arena, changed it, but the results were the same. So it sounds like a driver issue, but then again.... Why does compiz fusion run flawlessly?

Utterly confused.

I have Read and experienced the fact the  Nvidia Drivers work much better for linux. In my opinion nvidia is much more freindly towards linux. UNLIKE SAMSUNG >:(

---

### Post by Art3mis on 2009-03-21
ATI CARDS HAVE SOME ISSUE WHEN RUNNING 3d GAME AND COMPIZ AT THE SAME TIME>

SIMPLY DISABLE COMPIZ THEN START GAME

---

### Post by hikaricore on 2009-03-21
> **Art3mis said:**
> ATI CARDS HAVE SOME ISSUE WHEN RUNNING 3d GAME AND COMPIZ AT THE SAME TIME>

SIMPLY DISABLE COMPIZ THEN START GAME

Don't yell.

---

