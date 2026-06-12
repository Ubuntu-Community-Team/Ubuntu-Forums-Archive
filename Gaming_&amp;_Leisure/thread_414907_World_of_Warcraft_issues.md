---
title: "World of Warcraft issues"
date: 2007-04-20
forum: Gaming &amp; Leisure
---

### Post by Stormweaver on 2007-04-20
Hey gang, new to linux here but trying to setup a machine for me to use.

I just got through dealing with issues of getting my nvidia stuff set up and it seems to be doing what it should.  I followed the tutorial about installing WoW, and the recommended add on to the config.wtf file.  When I tried to start WoW it said it could not engage the 3D enviroment.  I also noticed when running things from Terminal that it said there was no OpenGL and to expect problems... I don't know if I have a bad install of wine or WoW, but I am guessing I should dump both programs and start again, only problem is, I don't know how to.   Could someone help me?? I'm going offline for the moment to cool off but should be back on in a couple of hours.  Feel free to watch for me log onto MSN or Yahoo both are listed in my profile, but I could really use the help fixing this... I have the 386 sever version running due to other things this machine does, and I am running a teamspeak server in the background if that might affect things.


Thank you!

Stormweaver

---

### Post by NeonNazgul on 2007-04-20
I'm still a newbie at all this, so not sure I can contribute much, but a second brain is sometimes helpful ;)  Can you get 3D acceleration in anything else?  What version of Ubuntu (Dapper, Edgy, Feisty, etc) are you running?

I usually install the basic 3D desktop app from the Synaptic manager to test that my OpenGL is working properly.  If not, I know the issue stems from the driver.

---

### Post by miley6112 on 2007-04-20
Do you go on neopets.com?

---

### Post by Stormweaver on 2007-04-20
I'll try the 3D desktop now.

Nope, never been to Neopets.

Just waking up so mind the short response.


Stormweaver

---

### Post by Stormweaver on 2007-04-20
So not so much luck here:

```
stormweaver@Eye-of-the-Storm:~$ 3ddesk
Attempting to start 3ddesktop server.
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Daemon started.  Run 3ddesk to activate.
Server not found after waiting 5 seconds.
Could not find server.
Try starting manually (3ddeskd)

stormweaver@Eye-of-the-Storm:~$ 3ddeskd
Daemon started.  Run 3ddesk to activate.
stormweaver@Eye-of-the-Storm:~$ Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".


```

I can't have the Nvidia GLX according to their site and to the people helping me with the driver -

Here is the thread I was working with::


[http://ubuntuforums.org/showthread.php?t=414229&highlight=Stormweaver](http://ubuntuforums.org/showthread.php?t=414229&highlight=Stormweaver)


The above code was the attempt to run the 3d Desktop after installing it.

So I don't know what to do next?

Stormweaver

---

### Post by Stormweaver on 2007-04-20
This may help as well information wise:

I'm running Ubuntu Server 386 w/ Ubuntu Edgy Desktop - I assume 6.10


I have GeForce 6600GT, 64Bit AMD Proc on a BioStar T-Force board.  I have a 1 Gig of RAM.

Maybe these things will help.  I I will be AFK for a bit while I handle breakfast and taking a friend home from the hospital.  

Feel free to watch for my messengers to pop up - They should be listed on my profile.


Stormweaver

---

### Post by Stormweaver on 2007-04-20
Having taken time to read the rant over not starting new WoW threads, I feel really stupid for having started this one... 

I went ahead and took time to look through the others, in hopes of finding an answer, and found only only a means of forcing it to use open gl.  So I tried that, and here was the return:

```
stormweaver@Eye-of-the-Storm:~/.wine/drive_c/Program Files/World of Warcraft$ wine WoW.exe -opengl
Xlib:  extension "GLX" missing on display ":0.0".
err:wgl:X11DRV_WineGL_InitOpenglInfo  couldn't initialize OpenGL, expect problems
Xlib:  extension "GLX" missing on display ":0.0".
err:wgl:X11DRV_WineGL_InitOpenglInfo  couldn't initialize OpenGL, expect problems
err:wgl:X11DRV_wglGetProcAddress No libGL on this box - disabling OpenGL support !
err:wgl:X11DRV_wglGetProcAddress No libGL on this box - disabling OpenGL support !
err:wgl:X11DRV_wglGetProcAddress No libGL on this box - disabling OpenGL support !
err:wgl:X11DRV_wglGetProcAddress No libGL on this box - disabling OpenGL support !
err:wgl:X11DRV_wglGetProcAddress No libGL on this box - disabling OpenGL support !
err:wgl:X11DRV_wglGetProcAddress No libGL on this box - disabling OpenGL support !
fixme:advapi:SetSecurityInfo stub
fixme:powrprof:DllMain (0x7d780000, 1, (nil)) not fully implemented
fixme:ntdll:NtPowerInformation Unimplemented NtPowerInformation action: 11
fixme:powrprof:DllMain (0x7d780000, 0, (nil)) not fully implemented
fixme:win:EnumDisplayDevicesW ((null),0,0x33eedc,0x00000000), stub!
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
err:d3d:IWineD3DImpl_FillGLCaps    GL_Extensions returns NULL
Xlib:  extension "GLX" missing on display ":0.0".
err:d3d:IWineD3DImpl_FillGLCaps    GLX_Extensions returns NULL
fixme:win:EnumDisplayDevicesW ((null),0,0x33f14c,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f6e8,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f6e8,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f650,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f63c,0x00000000), stub!
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
err:wgl:X11DRV_DescribePixelFormat No libGL on this box - disabling OpenGL support !
err:wgl:X11DRV_ChoosePixelFormat No libGL on this box - disabling OpenGL support !
fixme:win:EnumDisplayDevicesW ((null),0,0x33f650,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f63c,0x00000000), stub!
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
err:wgl:X11DRV_ChoosePixelFormat No libGL on this box - disabling OpenGL support !
fixme:win:EnumDisplayDevicesW ((null),0,0x33f650,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f63c,0x00000000), stub!
fixme:xvidmode:X11DRV_XF86VM_SetCurrentMode Cannot change screen BPP from 32 to 16
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
err:wgl:X11DRV_ChoosePixelFormat No libGL on this box - disabling OpenGL support !
fixme:win:EnumDisplayDevicesW ((null),0,0x33f650,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f63c,0x00000000), stub!
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
err:wgl:X11DRV_ChoosePixelFormat No libGL on this box - disabling OpenGL support !
fixme:win:EnumDisplayDevicesW ((null),0,0x33f650,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f63c,0x00000000), stub!
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
err:wgl:X11DRV_ChoosePixelFormat No libGL on this box - disabling OpenGL support !
fixme:win:EnumDisplayDevicesW ((null),0,0x33f650,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f63c,0x00000000), stub!
fixme:xvidmode:X11DRV_XF86VM_SetCurrentMode Cannot change screen BPP from 32 to 16
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
err:wgl:X11DRV_ChoosePixelFormat No libGL on this box - disabling OpenGL support !
stormweaver@Eye-of-the-Storm:~/.wine/drive_c/Program Files/World of Warcraft$ 

```

Also another window opened up - Said that World of Warcraft could not engage the 3D drive or server or something to that effect, it crashed out before I could see it all.


If I need to stop posting here about WoW, merely tell me a site I can go to about it, and I will leave the ubuntuforums alone.  I didn't realize it was such as issue.


Stormweaver

---

### Post by rudeboyskunk on 2007-04-20
I'll give the same advice I always give -- it's not worth the trouble installing wine.  Pay the $5/month and go with cedega.  There are, on ocassion, a few minor tweaks one must make, but overall it's SO MUCH EASIER.  [http://www.transgaming.com](http://www.transgaming.com)

(Of course plenty of other people will disagree, and for good reason.  Wine is free, as all software should be, and it really does work.  I'm just lazy, and cedega is so EASY.)

---

### Post by hikaricore on 2007-04-20
> **rudeboyskunk said:**
> I'll give the same advice I always give -- it's not worth the trouble installing wine.  Pay the $5/month and go with cedega.  There are, on ocassion, a few minor tweaks one must make, but overall it's SO MUCH EASIER.  [http://www.transgaming.com](http://www.transgaming.com)

(Of course plenty of other people will disagree, and for good reason.  Wine is free, as all software should be, and it really does work.  I'm just lazy, and cedega is so EASY.)

...........

---

### Post by AndrewRiedi on 2007-04-20
> **rudeboyskunk said:**
> I'll give the same advice I always give -- it's not worth the trouble installing wine.  Pay the $5/month and go with cedega.  There are, on ocassion, a few minor tweaks one must make, but overall it's SO MUCH EASIER.  [http://www.transgaming.com](http://www.transgaming.com)

(Of course plenty of other people will disagree, and for good reason.  Wine is free, as all software should be, and it really does work.  I'm just lazy, and cedega is so EASY.)

Look at wine's debug info from the previous post!!!!  He has no libGL.so!  Getting Cedega would do nothing for him but make his wallet $15 lighter.  Wine is not really that hard to use, especially for WoW with howtos and whatnot everywhere.  Seriously.

To the original poster:
Anyhow, you need to make sure you have OpenGL installed.  Look up DRI.  I don't have an Intel card, so maybe other folks and/or Google can help you there.  Once that is up, I will be happy to help you get WoW working with Wine.

---

### Post by hikaricore on 2007-04-20
Thank you, I said something similar in another thread he posted the exact same info in.

I didn't have the sanity left to say it again.

---

### Post by AndrewRiedi on 2007-04-20
Yeah, and the other thing is if you want an "easy to use Wine," go get Crossover Linux from Codeweavers.  It is a 1-time charge of $40, and they actually give back to the Wine project, not to mention having good support, especially when compared to Transgaming.

---

### Post by Stormweaver on 2007-04-22
Well I had to give up and reinstall OS... I don't know if I have my Open GL up and running... 

But if I do, I'm ready to get WoW installed!


Thanks!

---

### Post by AndrewRiedi on 2007-04-22
These should tell you if you have OpenGL.

```
glxinfo | grep -i opengl
```
```
glxinfo | grep direct
```

---

### Post by Stormweaver on 2007-04-22
We are Green for Load!  -- I haven't loaded Wine yet, waiting for any tips you might have.... Here is a read out of the code from those two tests, looks good to me!


```
stormweaver@Eye-of-the-Storm:~$ glxinfo | grep -i opengl
OpenGL vendor string: NVIDIA Corporation
OpenGL renderer string: GeForce 6600 GT/PCI/SSE2/3DNOW!
OpenGL version string: 2.0.2 NVIDIA 87.76
OpenGL extensions:

stormweaver@Eye-of-the-Storm:~$ glxinfo | grep direct
direct rendering: Yes
stormweaver@Eye-of-the-Storm:~$ 

```

Already copied the CDs over, but have not moved or touched them, just got the files on there.

Here's hoping your online!

---

### Post by AndrewRiedi on 2007-04-23
You can install WoW now.  :)

Here are some additional urls that may or may not help during and after install:

[http://www.wowwiki.com/Linux/Wine]("http://www.wowwiki.com/Linux/Wine")
[http://appdb.winehq.org/appview.php?iVersionId=6482]("http://appdb.winehq.org/appview.php?iVersionId=6482")
[http://wiki.winehq.org/UsefulRegistryKeys]("http://wiki.winehq.org/UsefulRegistryKeys")

---

