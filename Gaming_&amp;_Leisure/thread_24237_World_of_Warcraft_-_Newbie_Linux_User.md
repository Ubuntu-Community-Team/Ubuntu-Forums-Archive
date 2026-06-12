---
title: "World of Warcraft - Newbie Linux User"
date: 2005-04-06
forum: Gaming &amp; Leisure
---

### Post by Giawa on 2005-04-06
Hi everyone. I'd been thinking of switching to Linux for a while, but was not sure how I'd do in the new system. Microsoft's recent action against pirated versions of Windows made me switch (yes, I couldn't cough up the couple hundred for the Pro, so I downloaded one). So, here I am with Ubuntu, and I actually like it!

But... one major thing was that I wanted to be able to play World of Warcraft at least. I had looked up before that the free version of Winex supported World of Warcraft, so I thought I wouldn't have a problem. Well, I am, haha. I'm not sure if it's because I have the new version of Ubuntu, but I can't get wine to work, Cedega has just totally confused me because it's a bunch of bin files. I just want to get WoW to open up, if only for a minute so I know that I'll be able to get it running eventually. Does anyone have a link they can point me to, or some hints? I've tried a couple ways of installing Wine (reccommended on these forums and on googe) and I'm stuck.

I am a new Linux user, so, I might not be able to skip steps or understand exactly what you're talking about. A good online tutorial or good commenting on what code you are showing me would be very helpful. Thanks :razz:

---

### Post by Giawa on 2005-04-06
I think my main problem is this... On the tutorial it says after running

apt-get build-dep wine

I'm supposed "to install your newly created package (which should be in whatever directory you were in when you ran apt-get --build source), run 'dpkg -i wine*.deb' as root."
When I type in that command it says
dpkg: eroor processing wine*.deb (--install_:
cannot access archive: No such file or directory.

---

### Post by chronusdark on 2005-04-06
i play world of warcraft on ubuntu...goto [www.transgaming.com](www.transgaming.com) and read all the cedega documentation....well atleast the basics.....you arent in windows country any more linux isint as cut and dry as windows and if you ever plan to do anything in it you better be prepared to read...

the transgaming site has forums with almost every newbie question already asked....just look through there cedega is definately worth the 5 dollars a month to get to play warcraft 3, world of warcraft, halflife 2 and gobs of other windows games.....please contribute to the project so cedega can become perfect

also in linux .bin files are like exe's in windows just a lil fyi 

good luck

---

### Post by Giawa on 2005-04-06
The reason I went to Linux was because I couldn't afford anything... I don't want to sound selfish, but ya. the only reason I can afford the WoW subscription fee is because my Dad sometimes plays on my account, so he picks up the tab. Anyways, I've gotten further. I can run

winesetup

But as soon as it asks if I want to overwrite the registry files that are already there it kicks me out. I can then try to run the WoW installer with Wine and it opens a dialogue letting me know that Wine is trying to open the file, but the Installer quits telling me the Installer could not be opened because there was not enough harddrive space. I think the winesetup is quitting prematurely, before it can make the fake Windows folders and such. Any ideas? (Because I have over 40gb free on this drive, so there's not a problem with HD space)

---

### Post by Giawa on 2005-04-06
Okay, new question!  :smile: I think I know what I have to do, just not how to do it. How can I delete the file LibGL.a in the /usr/lib folder? It says I do not have permission to alter that file or its parent directory. I want permission, how?

---

### Post by hvar on 2005-04-06
Hi.
If you run terminal commands with the sudo, you'll get access.
You have to type a password after doing this, this is the same as the password of the user you created during Ubuntu install.
su=super user
do=do

example:
sudo apt-get update
password: pwd

I'm currently running WoW with Cedega, and it works great. I have heard that many others use wine successfully on WoW as well, so don't dispear :)
I don't have links to any of the wine resources now, but i guess google will do the job just as good as anything. 
Good luck!

---

### Post by Giawa on 2005-04-06
Okay... well. thanks  :-o for the help. I figured it out a big before hand, but not as easily as I think your method is.

Anyways, I downloaded the new wine over csv or cvs (i forget, but you probably know what I'm talking about). Then cleaned it up, checked for updated.
./configure
make depend
make

and it worked perfect. So, now I try Warcraft III and it's installing perfect right now, we'll see gameplay in a bit I guess, but WoW gives me the message that the installer can't start, perhaps there is not enough hard drive space. Could this be because WineX only makes a 3gb or something HD when WoW needs around 5? Is there a workaround to get by this? or am I doing something wrong still? It puzzles me though, because it does run the Warcraft III installer and everything fine. Oh well

Thanks in advance

EDIT-Looks like WineX can't read do Windows App Protection, so I need a cd crack for WC3. I'll do that when I wake up in 5 hours, haha. Night

---

### Post by Giawa on 2005-04-06
Okay... soo. I don't know how to get World of Warcraft to install. I think Winex is alright now because Warcraft III install worked fine (except I need a CD crack). So, is there a reason why WoW Installer would be saying that I might not have enough hard drive space? Is there a way to increase the amount of harddrive space available for windows applications.

and lastly... where is the fake hard drive? I can't find it anywhere  :-? I'm trying to find it to drop the cd crack for Warcraft III into that directory. I'll also need it to put the patch files for WoW in there, so I don't have to wait for them to download. Anyone?

---

### Post by dewey on 2005-04-06
You have to have enough space allocated to your /home or / partition, do a "$sudo fdisk -l" and paste the output.

I don't know about winex, but cedega (WineX has become cedega) stores everything underneath /home/USERNAME/TransGaming_Drive

---

### Post by Giawa on 2005-04-06
Disk /dev/hdb: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        7014    56339923+  83  Linux
/dev/hdb2            7015        7297     2273197+   5  Extended
/dev/hdb5            7015        7297     2273166   82  Linux swap / Solaris

---

### Post by Giawa on 2005-04-07
Well, I've tried tons of things, but I can't get anything to work with WineX. I can't even get cvscedega to work (if anyone wants to help me out by walking me thru this reply here, it would be awesome for any help!). The WoW Installer still says the installer could not start, you may be out of hard drive space. Anyways, I'm going to retire again for the night. If anyone has got WoW working without purchasing a subscription to Cedega can you please point me in the right direction? Thanks

 :razz: 

Also, I've heard rumours WineX has no been working properly since an update in Hoary. Is this true? If so, that may explain some of my problems :-P Maybe all will be well come Stable Release time (tomorrow yay!)

---

### Post by Giawa on 2005-04-07
Well, if anyone is still out there reading this. I installed CVSWine. CVSCedega doesn't work, it says
Installing Registry...
Registry Install Failed
Remove /home/user/.cvscedega .reg files to try again.

I tried removing the reg file in that directory and it just gives the same thing. So in CVSWine I tried
cvswine wow.exe -opengl

and i get this

fixme:opengl:query_function_pbuffer gl_version is: "1.5.3 NVIDIA 71.74"
fixme:opengl:query_function_pbuffer glx_exts is: "GLX_EXT_visual_info GLX_EXT_visual_rating GLX_SGIX_fbconfig GLX_SGIX_pbuffer GLX_SGI_video_sync GLX_SGI_swap_control GLX_ARB_multisample GLX_NV_float_buffer GLX_ARB_get_proc_address "
fixme:opengl:query_function_pbuffer gl_version is: "1.5.3 NVIDIA 71.74"
fixme:opengl:query_function_pbuffer glx_exts is: "GLX_EXT_visual_info GLX_EXT_visual_rating GLX_SGIX_fbconfig GLX_SGIX_pbuffer GLX_SGI_video_sync GLX_SGI_swap_control GLX_ARB_multisample GLX_NV_float_buffer GLX_ARB_get_proc_address "
fixme:advapi:SetSecurityInfo stub
fixme:user:EnumDisplayDevicesA ((nil),0,0x7798f6bc,0x00000000), stub!
fixme:user:EnumDisplayDevicesA ((nil),0,0x7798f4d8,0x00000000), stub!
fixme:user:EnumDisplayDevicesA ((nil),0,0x7798fa78,0x00000000), stub!
fixme:user:EnumDisplayDevicesA ((nil),0,0x7798fa78,0x00000000), stub!
fixme:user:EnumDisplayDevicesA ((nil),0,0x7798fa18,0x00000000), stub!
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
fixme:user:EnumDisplayDevicesA ((nil),0,0x7798fa04,0x00000000), stub!
fixme:user:EnumDisplayDevicesA ((nil),0,0x7798fa18,0x00000000), stub!
fixme:msvcrt:_XcptFilter (-1073741819,0x7798ed5c)semi-stub
fixme:thread:GetThreadTimes Cannot get kerneltime or usertime of other threads
fixme:thread:GetThreadTimes Cannot get kerneltime or usertime of other threads
fixme:thread:GetThreadTimes Cannot get kerneltime or usertime of other threads
fixme:thread:GetThreadTimes Cannot get kerneltime or usertime of other threads

And WoW quits and brings up the Blizzard bug submitter. Does anyone have any ideas?

---

### Post by Moeru on 2005-04-08
Just to give you guys hope, I'm a newbie. Got Cedega on, WoW installed and it DID run. Ran bad but that was cause I didn't install my 3d drivers for my card  \\:D/  BTW, for those of you who are doing fresh installs, grab the latest patch off Fileplanet. You can use Cedega to get it installed so you won't have to wait for that install either.

---

### Post by meinbobo on 2005-04-12
hey
i have been getting the same error message and after hours of resaerch this is what i have found

the wine messages are not the key
the key is the blizzard bug reporter window that pops up

[COLOR=Red][SIZE=2]>=========================
>World of WarCraft: Assertions Enabled Build (build 4297)
>
>Exe:      G:\games\World of Warcraft\WoW.exe
>Time:     Apr 12, 2005 11:54:02.774 PM
>User:     bobo
>Computer: roxie
>------------------------------------------------------------------------------
>
>This application has encountered a critical error:
>
>ERROR #0 (0x85100000)
>Program:	G:\games\World of Warcraft\WoW.exe
>File:	C:\build\buildWoW\Storm\Source\SFile.cpp
>Line:	5513
>Expr:	block < archiveptr->header.blockcount
>[/SIZE][/COLOR]

This is what I get - I found a blizzard form where windows users were getting similar things.  A blizzard rep said this was due to wow not being able to contact the blizzard servers.

blizzard support pages say:

[COLOR=Blue][SIZE=2]>The firewall or router will need to allow unrestricted communication on TCP Port number: 3724, 8086, 8087, 9081, 9090, 9091, 9100[/SIZE][/COLOR]

I have tried to reconfig my firewall to no avail.

I am running SuSE 9.2
I have allowed these ports in my yast firewall config and it is still giving me the exact same error.

Hope this helps someone.

I will post further if i make more headway.

-meinbobo

Athlon 3000+
Asus A7N8X-Delux
1GB DDR RAM
GeForce FX 5200
------------------------
SuSE 9.2
Wine v 20050310

---

### Post by rcbaxter on 2005-04-16
How I got it working:

First, some hardware specs for background purposes.  I'm running Ubuntu Hoary 5.04 on a P4 2.8, Abit DuraMAX AA8 motherboard, 512 DDR2 RAM, with an Nvidia GeForce 6600 PCI Express video card.  I had previously installed nvidia-glx using Synaptic.

1.  Installed Cedega 4.3

2.  Copied the first WoW installation CD to Desktop\cd1

3.  $cedega WoW.exe from within cd1 to start the WoW installer.

4.  Installed WoW just as if in Windows.  *(Swapping CDs worked fine for me)

5.  Downloaded the WoW updates from     [http://www.blizzhackers.com/viewtopic.php?t=261409](http://www.blizzhackers.com/viewtopic.php?t=261409) and manually installed them.

6.  $cedega WoW.exe from within the Wine WoW installation directory.

7.  WoW updated itself to the latest 1.31 build.

From this point, everything has been working great.  I hope this helps some of you.  If you need help, let me know.

---

