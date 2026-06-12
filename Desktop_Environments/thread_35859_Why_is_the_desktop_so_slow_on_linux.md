---
title: "Why is the desktop so slow on linux?"
date: 2005-05-20
forum: Desktop Environments
---

### Post by BorO on 2005-05-20
Hello!

I have tried some distros and I have never tried a distro that can compare to MSWindows in desktop. 
I have an AMD 2100XP, 512DDR, ATI9800PRO, bla bla... running in 1600x1200. 

If I just start moving an window I see shaddows. I hope you know what I mean. Minimazing and maximazing windows is very slow.

Why that? I a little bit tire of MS Windows and what to try something new. Everywhere I read it stand Linux is os fast... I can't work with so slow GUI...  ](*,) 

I don't know right terms, sorry..

Do you have it better?  :|

---

### Post by 23meg on 2005-05-20
the kind of slowness you describe is usually caused by inappropriate video drivers and configuration. you should first install official drivers for your graphics adapter if they're available, and then tweak your xorg / xfree86 for optimal performance (you can find lots of info on doing this in the ubuntu forums, just do a few searches).

---

### Post by BorO on 2005-05-20
I have already done that and I can run 3d stuff, OpenGL is working... But my 2d performance is very bad....

Or can I make it better?

---

### Post by 23meg on 2005-05-20
yes, probably. yours is a pretty recent card that shouldn't exhibit such behaviour normally. for starters, try adding the following in the "Device" section of your /etc/X11/xorg.conf file and see if it improves things:

```

        Option          "AGPMode" "4"
        Option          "AGPFastWrite" "True"
        Option          "EnablePageFlip" "True"

```

---

### Post by BorO on 2005-05-20
Thank you!

I have now restarted X with those settings and in beginning it felt faster... But... I don't know..... 

Is there some more options that I can use? :)

This is my conf
```
Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon 9800 Pro (R350 NH)"
#	Driver		"ati"
	Driver     	"fglrx"
#	BusID		"PCI:2:0:0"
#	VideoRam	131072
#	Option		"UseFBDev"		"true"
#	Option 		"NoDDC"
	Option		"VideoOverlay"	"on"
	Option		"OpenGLOverlay" "off"
	Option		"UseInternalAGPGART"	"no"
	Option		"AGPMode"	"4"
	Option 		"AGPFastWrite"	"True"
	Option		"EnablePageFlip"	"True"
	
EndSection
``` 

Thanks!

Best regards, Boris

---

### Post by 23meg on 2005-05-20
the following rough description isn't directly related to graphics performance, but tries to explain the reason behind the general "slowness" of linux that people who come from the windows world initially complain about, and might provide a partial answer to the question that is the title of this thread:

windows and linux have very different ways of dealing with software that runs on them. in windows, pretty much everything you install and execute is pre-compiled binary executables that have been statically compiled, meaning that everything an application needs is packed into the application and usually not shared with other applications. this method speeds up application launch time, but generally speaking decreases performance, reliability, expandibility and requires more disk space per application. in linux, pretty much everything is dynamically compiled, meaning they're "modular" and shared; if an application needs a certain function in a library, it just states to the os that it needs that library, and the os installs it via the package manager and points its location to the program. this way, many programs can share a single installed library, and thus they can have very little sizes, much more expandibility and better performance in general  but in exchange they will launch slower, because they need to fetch and bring together various things from many libraries before starting to initiate their own functions. 

in short, linux applications may feel a bit slower to launch and get going at first, but once they launch they usually outperform their windows counterparts largely thanks to linux's vastly superior memory management.

---

### Post by 23meg on 2005-05-20
[QUOTE=BorO]Thank you!

I have now restarted X with those settings and in beginning it felt faster... But... I don't know..... 

Is there some more options that I can use? :)
[/QUOTE]
 hmm, i have a much older ATI card that doesn't use fglrx so i don't know about the rest of the parameters on your xorg.conf, but i'm sure someone else will be able to help with this.

---

### Post by BorO on 2005-05-20
I have not noticed slow launc time. My only problem is that GUI is little to slow and to demanding.

---

### Post by BorO on 2005-05-20
I don't know if my system can be faster or not running linux.

If I for example open following page [http://ubuntuguide.org/](http://ubuntuguide.org/) and scrolling fast my CPU goes upp to 100% and the page can't catch up with me.

Is it so for you too?  :-| 

Best regards, Boris

---

### Post by 23meg on 2005-05-20
now way, that's very strange. does this happen with firefox? which version? and does it happen only while scrolling with the mouse wheel?

---

### Post by BorO on 2005-05-20
> now way, that's very strange. does this happen with firefox? which version? and does it happen only while scrolling with the mouse wheel? 

Japp, this is happeing with firefix. Version 1.02. But it's just an example. 

For example when I push tha "LogOut" button an dthe screen starts to fade. It does'nt fade smothly. And I can hardly move my mouse the CPU is woring 100%

Is it normal?

Please help me...
I can't have it like this.

Best regards, Boris

---

### Post by 23meg on 2005-05-20
of course it's not normal. don't worry, it will get fixed somehow :) it sounds like some video driver problem really. perhaps you should try enabling/disabling the rest of the Option parameters on your xorg.conf file.

---

### Post by BorO on 2005-05-20
> of course it's not normal. don't worry, it will get fixed somehow it sounds like some video driver problem really. perhaps you should try enabling/disabling the rest of the Option parameters on your xorg.conf file. 

I hope you are right because I really like Ubuntu....

I'm going to try to enable some settings now...

Wish me luck :)

---

### Post by BorO on 2005-05-20
I have enabled some options with no luck...But then I changed my resolution and this logout fading is much smothlier now but thats all....

hmhmh :(

---

### Post by krusbjorn on 2005-05-20
Perhaps you'd like to take a look at this thread.

[http://www.ubuntuforums.org/showthread.php?t=18197](http://www.ubuntuforums.org/showthread.php?t=18197)

---

### Post by BorO on 2005-05-20
I'm reading it and it seems that I have he same problem. Hopes there some solution in the thread comming soon :)

---

### Post by 23meg on 2005-05-20
it's recommended on that thread to blacklist the agpgart module, so i'd play with that agpgart option on your xorg.conf and see what happens.

---

### Post by vassalle on 2005-05-20
[QUOTE=23meg]it's recommended on that thread to blacklist the agpgart module, so i'd play with that agpgart option on your xorg.conf and see what happens.[/QUOTE]
 to be totally honest, 2d performance in gnome is a bit slow, compared to MS. im using a p4 3.0 with nvidia 6800 and ive tried most of the settings in the xorg, regarding nvidia, but really doesnt change much.. the agpgart thing is best left at the default value which is 3, using agpgart over nvagp. the gui 'lag' in gnome can be clearly seen if u open two firefox windows, and minimising one of them.. ull see the frames slowly moving into the taskbar (hopefully u know what i mean....)  ](*,) 

however, i dont think this is a problem in linux or xorg, its a gnome thing i guess.. i tried playing around with xfce 4.2 and realise the 2d performance increased, perhaps to be even faster than MS.. but probably thats just me.. :D

---

### Post by dresnu on 2005-05-20
Here are the steps I took that made my linuxbox run faster than windows(which I have tweaked pretty well too):
1) Fixed my xorg.config, it's really important
2) Disabled all the useless services running in the background (try webmin)
3) Recompiled the kernel (maybe not that usefull)
4) Prelinking (now that's something that makes the difference(!), check here: [http://www.ubuntuforums.org/showthread.php?t=1971&page=1&highlight=prelink](http://www.ubuntuforums.org/showthread.php?t=1971&page=1&highlight=prelink))

(if you use kaffeine be sure to install this fix [http://www.ubuntuforums.org/showthread.php?t=27670&page=1&highlight=kaffeine](http://www.ubuntuforums.org/showthread.php?t=27670&page=1&highlight=kaffeine))

---

### Post by Grue on 2005-05-20
[QUOTE=vassalle]to be totally honest, 2d performance in gnome is a bit slow, compared to MS. im using a p4 3.0 with nvidia 6800 and ive tried most of the settings in the xorg, regarding nvidia, but really doesnt change much.. the agpgart thing is best left at the default value which is 3, using agpgart over nvagp. the gui 'lag' in gnome can be clearly seen if u open two firefox windows, and minimising one of them.. ull see the frames slowly moving into the taskbar (hopefully u know what i mean....)  ](*,) 

however, i dont think this is a problem in linux or xorg, its a gnome thing i guess.. i tried playing around with xfce 4.2 and realise the 2d performance increased, perhaps to be even faster than MS.. but probably thats just me.. :D[/QUOTE]
 I think this is generally a problem in a lot of new Linux programs. Firefox is a real memory hog, and has a tendency to max out CPU usage on my laptop for some reason. I've never seen the log-out fading in GNOME happen smoothly, so why it's there I don't know (this is on fairly decent hardware (AMD64 +3000, RADEON 9800 pro, with drivers and all working smoth)). Why not leave it out, till it's been optimized a bit. It's not really a crucial part of the DE, but gives a bad impression for the user.
Also the click-drag on the desktop begins to suck up CPU usage when it's covering about 70% of the screen.

I think we as Linux users and developers should focus more on performance and optimizations for a while. I know Ubuntu is fairly bleeding-edge, and GNOME has seen some great improvements in the last couple of months, but it's just not enough yet :). 

I guess it's pretty redundant to write this here, but I really think this is important. I hope we'll see a new trend forming, but I'm still looking for the omens.

[/rant]

---

### Post by BorO on 2005-05-21
> 
I think we as Linux users and developers should focus more on performance and optimizations for a while. I know Ubuntu is fairly bleeding-edge, and GNOME has seen some great improvements in the last couple of months, but it's just not enough yet .

I guess it's pretty redundant to write this here, but I really think this is important. I hope we'll see a new trend forming, but I'm still looking for the omens. 
Something has to happend. I'm a webbdesigner and programmer and I always have many apps started. It works well in MS Windows but in Gnome i can't do anything. Like when you play a game with to high resolution. Everything is lagging. If users are going to run some linux distro that OS has to be as fast as windows. Maybe is linux much better but I just can't see it with lagging GUI. However the 3D performance is good...

For some reason I like Gnome more than KDE. But my only solutions for now is maybe to switch to KDE because KDE seems to run much better.

Best regards, Boris

---

### Post by matthias_k on 2005-05-21
Hm, I'm not yet using Ubuntu, and I'm neither using GNOME nor X.org, so I know this sounds like rather useless information, but I just want to make my point, that it's NOT a Linux problem in general, as some poeple here seem to believe. I'm doing just fine in terms of performance (apart from 3D, which I haven't managed to set up properly yet).

My setup:
P4 3.0, 1GB RAM, Radeon 9800 Pro
Debian Sarge (testing), XFree86 4.3, Xfce 4.2.1.1
Kernel 2.6.11.10 (custom)

Driver settings:
> 
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz"
        ### [arg]: arg optional
        #Option     "NoAccel"                   # [<bool>]
        #Option     "SWcursor"                  # [<bool>]
        #Option     "Dac6Bit"                   # [<bool>]
        #Option     "Dac8Bit"                   # [<bool>]
        #Option     "ForcePCIMode"              # [<bool>]
        #Option     "BusType"                   # [<str>]
        #Option     "CPPIOMode"                 # [<bool>]
        #Option     "CPusecTimeout"             # <i>
        #Option     "AGPMode"                   # <i>
        #Option     "AGPFastWrite"              # [<bool>]
        #Option     "AGPSize"                   # <i>
        #Option     "GARTSize"                  # <i>
        #Option     "RingSize"                  # <i>
        #Option     "BufferSize"                # <i>
        #Option     "EnableDepthMoves"          # [<bool>]
        #Option     "EnablePageFlip"            # [<bool>]
        #Option     "NoBackBuffer"              # [<bool>]
        #Option     "PanelOff"                  # [<bool>]
        #Option     "DDCMode"                   # [<bool>]
        #Option     "MonitorLayout"             # [<str>]
        #Option     "IgnoreEDID"                # [<bool>]
        #Option     "OverlayOnCRTC2"            # [<bool>]
        #Option     "CloneMode"                 # [<str>]
        #Option     "CloneHSync"                # [<str>]
        #Option     "CloneVRefresh"             # [<str>]
        #Option     "UseFBDev"                  # [<bool>]
        #Option     "VideoKey"                  # <i>
        #Option     "DisplayPriority"           # [<str>]
        #Option     "PanelSize"                 # [<str>]
        #Option     "ForceMinDotClock"          # <freq>
        Identifier  "Card0"
        Driver      "ati"
        VendorName  "ATI Technologies Inc"
        BoardName   "Radeon R350 [Radeon 9800]"
        BusID       "PCI:1:0:0"

Everything is set to default, and it performs quite nicely. I'm not using the proprietary fglrx driver though, that's also why I don't have hardware 3D.

So it's either GNOME's or X.org's fault that your system performs bad. Or maybe a Kernel problem? Try rolling your own.

---

### Post by matthias_k on 2005-05-21
[QUOTE=BorO]Something has to happend. I'm a webbdesigner and programmer and I always have many apps started. It works well in MS Windows but in Gnome i can't do anything. Like when you play a game with to high resolution. Everything is lagging. If users are going to run some linux distro that OS has to be as fast as windows. Maybe is linux much better but I just can't see it with lagging GUI. However the 3D performance is good...

For some reason I like Gnome more than KDE. But my only solutions for now is maybe to switch to KDE because KDE seems to run much better.

Best regards, Boris[/QUOTE]
You should really try to figure out what is causing this. Divide and Conquer.
First, install Xfce or something similar lightweight like Blackbox WM. If the lags are gone, dump GNOME and consider using something more lean and slim.
If you should come to this conclusion, I can really really suggest using Xfce. It is way more flexible in terms of customization and looks just as good (have a look at  [this snapshot of my Xfce desktop](http://digitalraid.com/tmp/screen_11.png)). It performs extremely well, even on low end machines. I have seen Xfce running on a Pentium II 300MHz and it performed extremely well. It's also getting more and more attention, just give it a try. 

If the lags aren't gone, try replacing the stock kernel with a customized one. Rolling a kernel is quite some work and somewhat hairy, but it's worth the time. Stock kernels ought to be generic, so they run on as much configurations as possible. That however doesn't mean that they perform well. They come with loads of drivers and settings for partly ancient hardware which you have most probably never even heard about.

If that still doesn't fix the problem, you may want to consider downgrading to XFree86. If you can live without real transparency and shadows and all this other useless stuff, XFree86 is just as good (though its future is questionable because X.org is taking over the X11 land).

---

### Post by Grue on 2005-05-21
[QUOTE=matthias_k]
My setup:
P4 3.0, 1GB RAM, Radeon 9800 Pro
Debian Sarge (testing), XFree86 4.3, Xfce 4.2.1.1
Kernel 2.6.11.10 (custom)
[/QUOTE]

With 1 GB RAM and a Pentium 4  3 GHz that's not really that surprising now is it? A lot of users aren't hardware geeks, with ricer rigs, and there's still a lot of laptops around which run great, but need an up to date OS. 

This is not Linux bashing in any way, but rather some constructive criticism. Ubuntu with GNOME runs fairly smooth on my AMD64 +3000 with 512 MB RAM, but still lacks a bit in responsiveness imo (we are talking a second or two mostly). But on my Acer Travelmate laptop with Pentium 3 700 Mhz and 256 MB RAM, GNOME starts to be a bother. The worst though is Firefox. Thats the 800 lb gorilla we all are hoping for memory makeover :).

---

