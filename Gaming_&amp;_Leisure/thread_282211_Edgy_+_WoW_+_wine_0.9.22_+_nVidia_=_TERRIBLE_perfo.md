---
title: "Edgy + WoW + wine 0.9.22 + nVidia = TERRIBLE performance!"
date: 2006-10-22
forum: Gaming &amp; Leisure
---

### Post by jdmpike on 2006-10-22
All,

I haven't logged into WoW in several months, but thought I would try to play with my brother for a bit this weekend.

After the Edgy upgrade I received a new wine package and I have read on other posts that this package delivered amazing performance improvements. This however isn't the case for me. 

I don't think it is using OpenGl or my graphics card at all - I can't even get past the login screen which renders at 0.1-0.25 fps as WoW.exe soars to 100% of the system resources.

I don't understand what is going on or how to start troubleshooting. If anyone has ideas, let me know!

Thanks,

jdmpike

---

### Post by skenliv on 2006-10-22
Please make shure that you have the latest Nvidia drivers installed.
And start wow with: /pathtowine/Program Files/World Of Warcraft/WoW.exe --opengl

You should get an error about OpenGL if they are not properly installed.

---

### Post by jdmpike on 2006-10-22
The drivers are properly installed. 

```
jordan@luckyone:~$ glxinfo | grep render
direct rendering: Yes
OpenGL renderer string: GeForce2 MX/AGP/SSE2

```

Direct rendering is enabled, it just doesn't seem to work for World of Warcraft unfortunately...

I am guessing this may have something to do with it?

```

fixme:wgl:X11DRV_wglQueryPbufferARB unsupported WGL_PBUFFER_LOST_ARB (need glXSelectEvent/GLX_DAMAGED work)

```

I canceled my account today anyway... so it won't matter much after the end of my 3 month period.

Thanks for the ideas though,

jdmpike

---

### Post by Perfect Storm on 2006-10-22
Well that isn't the strongest card you have there, anyway. Have you tried on a clean Edgy install? There's a chance that an dist upgrade will mess up things.

---

### Post by reiki on 2006-10-29
Wine 0.9.22 does not work with WoW due to some gl issue that causes flashing... TERRIBLE flashing of the screen. Like unplayable flashing. I tried compiling my own wine 0.9.23 last night and broke everything really badly so now wine segfaults :)  Fortunately I'm playing on a second physical drive so no harm done to my main system. I won't upgrade to Edgy until I know I can play WoW in Wine :)

---

### Post by Ferrat on 2006-10-29
> **reiki said:**
> Wine 0.9.22 does not work with WoW due to some gl issue that causes flashing... TERRIBLE flashing of the screen. Like unplayable flashing. I tried compiling my own wine 0.9.23 last night and broke everything really badly so now wine segfaults :)  Fortunately I'm playing on a second physical drive so no harm done to my main system. I won't upgrade to Edgy until I know I can play WoW in Wine :)

nvidia has a fix for the flashing check appdb.winehq.org/appview.php?iVersionId=5606

---

### Post by reiki on 2006-10-29
yeah but it involves recompiling wine which I DID, by the way, try, but ended up buggering up wine on Edgy so badly that subsequent attempts to get a working wine installation have failed and I MAY reinstall completely just to clear things up and start again from square one. Apparently there's a problem compiling Wine on Edgy due to some gcc flag default. It segfaults after installation.

So... download wine 9.23, patch, compile, install, and it blows up.
Very nice.

No thanks, I'll wait until someone smarter than me fixes this. Meanwhile I'll keep my working Dapper install thank you. :)

---

### Post by Ferrat on 2006-10-29
> **reiki said:**
> yeah but it involves recompiling wine which I DID, by the way, try, but ended up buggering up wine on Edgy so badly that subsequent attempts to get a working wine installation have failed and I MAY reinstall completely just to clear things up and start again from square one. Apparently there's a problem compiling Wine on Edgy due to some gcc flag default. It segfaults after installation.

So... download wine 9.23, patch, compile, install, and it blows up.
Very nice.

No thanks, I'll wait until someone smarter than me fixes this. Meanwhile I'll keep my working Dapper install thank you. :)

Yeah know the Edgy problem, tried the edgy beta and had the same problems, running Dapper now, there is suppost to be a fix for the building problem with wine and edgy but haven't looked it up, since Dapper works fine but from what I've heard edgy should give better preformance (if you get it to work ^^)

---

### Post by cyberswat on 2006-10-29
I performed a completely clean installation of Ubuntu 6.10 today and did not touch anything before installing wine and the WoW.  Followed the instructions at [http://www.winehq.com/site/download-deb](http://www.winehq.com/site/download-deb) to add the repository and install Wine.

Installed windows fonts into wines font folder so I could read the WoW installer's directions.

The WTF/Config.wtf had to contain the following lines because anything less created an evil flickering of horizontalish lines:
   SET gxResolution "1280x1024"
   SET gxRefresh "75"
   SET gxColorBits "24"
   SET gxApi "opengl"
   SET SoundOutputSystem "1"
   SET SoundBufferSize "150"
   SET hwDetect "0"

I've tried this a bunch in the past and have always had to compile from source with the nvidia patch ... I did not have to do that this time.  This is the first time everything worked completely and totally like it should.

A complete detail of the steps I took are at [http://www.kevinbridges.org/linuxWoW](http://www.kevinbridges.org/linuxWoW)

---

### Post by reiki on 2006-10-29
Ok wait... that's a DAPPER repo. You added it to edgy? What version of Wine did it install? And are you saying that installing Wine from that repo you had no issues with the flickering screen in WoW? 

Are you using an nVidia graphics card and starting wow in openGL mode?

If simply installing wine from a different repository makes WoW work... I'll do it! :)

---

### Post by reiki on 2006-10-29
OK call me skeptical, but I'm not convinced that this was done with 9.24. If you add teh repositories as it says on winehq, you get a dapper repository with 0.9.23 version of wine. And going to Kevin Bridges' site there is no mention of him installing 9.24 so I assume from his intructions and how he got wine, that he got 9.23. 

He seems to be indicating that he's installing the 8776 nvidia drivers, even though a few lines down it appears he's installing the 8756 nvidia drivers. I can chalk that up to a simple oversight when updating teh instructions.

I CAN tell you that with my 7300GT with 512MB on it, his Config.wtf settings do NOT eliminate the flickering.

Can somebody please patch 9.23 or 9.24? :)

---

### Post by Ferrat on 2006-10-29
Any preformance gain vs Dapper then?? or just no flickering ect.?

---

### Post by reiki on 2006-10-29
I'm not seeing any reason yet to switch from Dapper. Edgy is still just a little too edgy and even if I get this wine thing straightened out, there's still the matter of getting VMWare workstation running in Edgy. *sigh*

I think I'm a Dapper kind of guy for a while to come yet.

---

### Post by cyberswat on 2006-10-29
I installed Ubuntu 6.10 from scratch, plugged into the wine repository, installed WoW, created teh Config.wtf I mention above, installed the latest nvidia drivers and set it up for dual sli  .... I've been running WoW at 8x Antialiasing and 8x Anisotropic all day.

The Config.wtf is a big deal ... to much or two little and it will look like the nvidia graphics aren't working right ... I outlined everything I did on the site I linked to.

---

### Post by cyberswat on 2006-10-29
> **reiki said:**
> OK call me skeptical, but I'm not convinced that this was done with 9.24. If you add teh repositories as it says on winehq, you get a dapper repository with 0.9.23 version of wine. And going to Kevin Bridges' site there is no mention of him installing 9.24 so I assume from his intructions and how he got wine, that he got 9.23. 

You are correct wine --version shows **Wine 0.9.23**

> **reiki said:**
> He seems to be indicating that he's installing the 8776 nvidia drivers, even though a few lines down it appears he's installing the 8756 nvidia drivers. I can chalk that up to a simple oversight when updating teh instructions.

I installed the package located at [http://download.nvidia.com/XFree86/Linux-x86/1.0-8776/NVIDIA-Linux-x86-1.0-8776-pkg1.run](http://download.nvidia.com/XFree86/Linux-x86/1.0-8776/NVIDIA-Linux-x86-1.0-8776-pkg1.run) and abbreviated the remainder of the code I found at [http://doc.gwos.org/index.php/Latest_Nvidia_Breezy#METHOD_2](http://doc.gwos.org/index.php/Latest_Nvidia_Breezy#METHOD_2)

You can be skeptical, but I've been playing WoW all day and I did nothing else to the computer than what i described.

---

### Post by cyberswat on 2006-10-29
> **Ferrat said:**
> Any preformance gain vs Dapper then?? or just no flickering ect.?

When I was running 6.06 and wine patched for nvidia I could not get nvidia to override WoW's antialiasing like I was telling it to in the control panel.  The sli overlay would say that it was working at 8x but you could see that it wasn't.  The edges are noticeably smoother now.  That's the entire reason I tried approach to begin with ... I shouldn't see jagged edges with those graphics cards.

I don't know if I got lucky or what, but I'm glad it's working.

---

### Post by graigsmith on 2006-10-30
Hmm, i been playing it like every day with little problems, on my ati 9200 (using open source drivers).

you just need to set up the config file in the WTF folder correctly.  then it will use open gl, and use less geometry and you can get it playable.

---

### Post by Somniis on 2006-10-30
I'm having similar problems, just not pertaining to WoW.  It's with wine in general.  Before I upgraded to Edgy, Starcraft and Fallout (the two games I mostly play with wine) ran near perfectly.  Now, however, both of them are terribly slow.  I did nothing to wine after I upgraded to Edgy.

I have downloaded and am using the Nvidia beta drivers.  That may be it, as I can't see any other reason why they run so horribly.  :(

Edit: Also, the option to emulate a virtual desktop is grayed out in winecfg.  Anyone know why?  wine 0.9.24

---

### Post by reiki on 2006-10-30
> **cyberswat said:**
> You are correct wine --version shows **Wine 0.9.23**



I installed the package located at [http://download.nvidia.com/XFree86/Linux-x86/1.0-8776/NVIDIA-Linux-x86-1.0-8776-pkg1.run](http://download.nvidia.com/XFree86/Linux-x86/1.0-8776/NVIDIA-Linux-x86-1.0-8776-pkg1.run) and abbreviated the remainder of the code I found at [http://doc.gwos.org/index.php/Latest_Nvidia_Breezy#METHOD_2](http://doc.gwos.org/index.php/Latest_Nvidia_Breezy#METHOD_2)

You can be skeptical, but I've been playing WoW all day and I did nothing else to the computer than what i described.

When I said "skeptical" I hope you understand that I was referring to whether or not this would work for me.... and not whether or not you were reporting facts which I have no doubt you are reporting accurately. However I have to wonder if this has something to do with the SLI setup you have. I know it's just nVidia drivers on the other end, but...

I have a 7300GT with 512MB and using the 8762 nvidia drivers (I haven't got teh 8776 drivers yet.... ran out of time to play with this) I can tell you that even with the Config.wtf file edited exactly as you stated, it still does not work and the screen flashes (flickers) so terribly you can't use it.  I guess my next experiment would be to get the 8776 drivers and see if something in those drivers allows this to work correctly with an unpatched wine version. THAT would be wonderful!

---

### Post by chadk on 2006-10-30
nVidia drivers:
envy (thanks tseliot!) 
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

Dapper, Wine (already patched .21) and WoW:
[https://wiki.ubuntu.com/WorldofWarcraftHowto](https://wiki.ubuntu.com/WorldofWarcraftHowto)

Works perfectly, I have a nvidia 7600gs 512 and I'm running wow with full graphics details with zero problems on an amd64 running what, something like 1800mghz
anyway, I hope this helps.

Install Dapper.
Install vVidia drivers using Envy.
Install wine and WoW using the howto.
Run and play WoW, enjoy.

---

### Post by KRavEN on 2006-10-30
Fixing the compile problem for edgy is easy enough.

Follow the buildwinefromsource instructions in the ubuntu wiki

before doing the buildpackage step:

cd "wine-source-directory"/debian
gedit rules

change:
CFLAGS = -Wall -g
to:
CFLAGS = -Wall -g -fno-stack-protector

Also if you have a multicore processor and want it to compile a lot faster using multiple threads (works for all builds)
change:
	# Add here commands to compile the package.
	$(MAKE)
to:
	# Add here commands to compile the package.
	$(MAKE) -j3

I had a problem with applying the flicker patch so I did it by hand.  Very easy, just 1 line changed.

I also had a problem with all wine builds running winecfg and clicking the audio tab kicked it out saying:
can't create mcop directory

I fixed this by doing:
mkdir /tmp/ksocket-kraven ##substitute kraven with your login name

I prefer using the budgetdedicated sources but the changes will work for either wine source

---

### Post by reiki on 2006-11-01
Kraven-

When I went into my sources directory for 9.24 I did not appear to have a /debian directory. Did you simply untar the wine.......bz2 file from winehq or did you add the repostories and get the sources using apt?

---

