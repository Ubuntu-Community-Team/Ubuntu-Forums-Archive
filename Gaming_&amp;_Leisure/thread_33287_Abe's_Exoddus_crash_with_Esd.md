---
title: "Abe's Exoddus crash with Esd"
date: 2005-05-10
forum: Gaming &amp; Leisure
---

### Post by globalspace on 2005-05-10
hi all!
i've installed Abe and all works ok if i not use Sound ( snif ...)
if i use Sound (Esd) when i start the game it crash with this error :


> massi@Pc-Massi:~/Abe$ wine Exoddus.exe
Invoking /usr/lib/wine/wine.bin Exoddus.exe ...
Please use the registry key HKEY_CURRENT_CONFIG\Software\Fonts\LogPixels
to set the screen resolution and remove the "Resolution" entry in the config file
fixme:ddraw:Main_DirectDraw_SetCooperativeLevel (0x77c6da88)->(00010022,00000053)
fixme:x11drv:X11DRV_desktop_SetCurrentMode Cannot change screen BPP from 32 to 16
fixme:x11drv:X11DRV_desktop_SetCurrentMode Cannot change screen BPP from 32 to 16
fixme:ddraw:DIB_DirectDrawSurface_Blt dwFlags DDBLT_WAIT and/or DDBLT_ASYNC: can't handle right now.
fixme:mmtime:timeBeginPeriod Stub; we set our timer resolution at minimum
err:dsound:DSOUND_MixInBuffer length not a multiple of block size, len = 812, block size = 4
err:dsound:DSOUND_MixInBuffer length not a multiple of block size, len = 812, block size = 4 

i've try to search with google but i didn't found something :(

thanks ! :)

---

### Post by McQuaid on 2005-05-10
Well, there are a couple things you can try.  

First set esd to use alsa.  You should install libesd-alsa and change esd.conf to use alsa, and you'll need a alsa config file for your soundcard.

See this thread: 
[http://www.ubuntuforums.org/showthread.php?t=32063](http://www.ubuntuforums.org/showthread.php?t=32063) 

Look at the first post on initial setup and then look at my post within that thread.

Then install libwine-alsa.  That should do it.  

Otherwise I found this thread on esd and wine
[http://www.winehq.com/hypermail/wine-devel/2005/02/0675.html](http://www.winehq.com/hypermail/wine-devel/2005/02/0675.html) 

MIght be more effort than it's worth, hopefully buddy submits a patch to get it into mainline wine.

If esd still gets in the way either kill it, or maybe install a small window manager like icewm where esd won't start up and you should be fine.

Please let me know as I love this game and the first one.  Still haven't forgiven them for going xbox only

---

### Post by globalspace on 2005-05-10
[QUOTE=McQuaid]Well, there are a couple things you can try.  

First set esd to use alsa.  You should install libesd-alsa and change esd.conf to use alsa, and you'll need a alsa config file for your soundcard.

See this thread: 
[http://www.ubuntuforums.org/showthread.php?t=32063](http://www.ubuntuforums.org/showthread.php?t=32063) 

Look at the first post on initial setup and then look at my post within that thread.

Then install libwine-alsa.  That should do it.  

Otherwise I found this thread on esd and wine
[http://www.winehq.com/hypermail/wine-devel/2005/02/0675.html](http://www.winehq.com/hypermail/wine-devel/2005/02/0675.html) 

MIght be more effort than it's worth, hopefully buddy submits a patch to get it into mainline wine.

If esd still gets in the way either kill it, or maybe install a small window manager like icewm where esd won't start up and you should be fine.

Please let me know as I love this game and the first one.  Still haven't forgiven them for going xbox only[/QUOTE]

thanks but i really don't want to try the first option because i've done a lot of audio problem when i've tryed to set alsa  :-| 
for the second option i don't know the PATH that i should put me to patch wine ... it says 

> cd wine-20050111 

but i've installed wine from synaptics and i can't find the right path .. :(

thanks again :)

---

### Post by McQuaid on 2005-05-10
I hear ya but I still strongly recommend the first option rather than trying to compile/patch wine from source, which will probably be harder or have mroe issues.

This first thing is install libesd-alsa.  Ubuntu should come with this with a fresh install as your using alsa anyways unless you went out of your way to install oss drivers which I doubt.  And this is totally reversable.  So is changing esd.conf, just back it up and modify it according to the other how to.

But if you don't want to do any of this even though it will probably make your sound experience much better in general in gnome just install a lite window manager like icewm and run it from there, as icewm by default doesn't use esd.  Or kill esd to test it out and make sure it works.

---

