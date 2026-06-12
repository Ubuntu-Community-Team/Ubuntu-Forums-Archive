---
title: "OpenGL vs Direct3D"
date: 2006-02-26
forum: Gaming &amp; Leisure
---

### Post by Eazy© on 2006-02-26
Ok, I have just one game to compare this with, and that is UT2004. I have the same fps in both Linux (OpenGL) and WinXP (Direct3D), but in Linux graphics lags even if the fps is ok (80 fps and above, mostly above 100 fps). 
I have gone through every tweak guide there is to tweak my grafic card (Nvidia 6600GT) and my ini-files for UT2004. I have tried to compile a Vanilla kernel with ck-patch, but nothing of this have helped.

When I play in WinXP it makes no difference if the fps is as low as 80 fps, it dont lag, and everything is smoth. In Linux the fps has to be over 130 to make it as smoth as in WinXP.

So my questions is: 
Should I stop searching for a solution? 
Is this what can be expected of OpenGL and playing in Linux, or is there any chance to get the same smoth gaming as in Direct3D?

I'm really tired to have to boot to WinXP every time I like to play, and I play alot.

/Eazy

---

### Post by Zeroedout on 2006-02-27
When you play on linux, do you boot into gnome and launch the game? Personally, i use FLWM, very light and uses like 5 megs of memory. The next thing, and i'm sure this is what is causing the lag, did you disable gam_server? If you've never heared of this, look up in the forums on how to disable it. You basically go to the directry where it is located and change it's name. If you just kill the process, it's just going to spawn again, I'm almost 100% sure this is the problem. If disabling it doesn't work (check your processes to make sure it is disabled), then post back and we'll see what else we can do.

---

### Post by newuser111 on 2006-02-27
it would be a more fair comparison if you compared opengl in windows to opengl in linux, and it depends on your video card drivers the most, the vendors optimize their drivers more for windows than linux, especially if you have an ati card you can expect slower 3d in linux compared to windows and compared to an equivalent nvidia card

directX is a microsoft only technology, whereas opengl runs on many platforms and OS

---

### Post by Eazy© on 2006-02-27
@ Zeroedout
Thanx for your suggestions! 
I have disabled gam_server and installed Blackbox, but it makes no differnce. I'm guessing the problem lies in OpenGL. Something that has to be enabled or disabled (just guessing). Maybe when I write "stat fps" in console it gives me false result, fps it's lower than it shows.

@newuser111
I know I could have compared with OpenGL in Windows but that was not my question. As I have exactly the same fps in Linux with OpenGL as I have in Windows with Direct3D I was thinking UT2004 would run equival smoth in both Linux and Windows. But I guesse that its not only the results of fps that matters. Thats why I ask.
/Eazy

---

### Post by Eazy© on 2006-02-28
Ok, maybe I have found what is responsible for the lag. If I circle around a box  (on DM-Deck17) using my mouse and keyboard it is very unsmooth (word?:p), but if I circle around the same box using only the keyboard its really smooth and nice. Is this whats called "mouse lag"? I have never had mouse lag before, so I dont know how it feels like.

I have a Logitech MX500 mouse pluged in to USB, and I have installed logitech_applet so I have 800cpi. I have tried without logitech_applet installed but the result is the same.
Any help would be appreciated.
/Eazy

---

### Post by Brynster on 2006-02-28
Is th emouse cabled or is it wireless.

Mouse lag *usually* occurs in wireless kit only. If you have the option plug in a standard cable mouse and circle the box again see it the "lag" is still present.

---

### Post by Eazy© on 2006-02-28
MX500 is not a wireless mouse. I have tried with an adapter and pluged it into PS/2, but it didnt help.

---

### Post by Eazy© on 2006-02-28
Sorry to answer my own post.
I have tested things all day now, and unless someone has some tips, this is the end of it :P

If I put Vsync on (both in Graphic drivers and in ut2004.ini) it smoothes up in large areas of a map, but if I am close to a wall or some other texture (eg. a box on Deck17) it lags really bad. 'Mouse smoothing' dose not makes a difference if its off or on, neither does 'Reduce mouse lag' if I put that on ingame.

If I put Vsync off and put 'Mouse smoothing' on ingame, it lags badly on large areas, but it is really smooth if I circle around a box or other textures.

---

### Post by Zodiac on 2006-02-28
I have had that happen to me in ET before... I think it is an issue with XORG or something because I have that exact same mouse.

I looked online for a configuration that would make the lag disappear, all to no avail. Sadly, I would recommend the duel boot... I have to. :cry:

---

### Post by leech on 2006-02-28
Could be the mix between X and OpenGL and the game just doesn't understand using 800dpi.  I have a MX1000, but have never had any of those issues, but then I haven't tried to change the dpi of the mouse either.

Leech

---

### Post by Zeroedout on 2006-03-03
outta curiousity, how much RAM do you have? In UT2004 If you have more than 512, are you loading all the textures to RAM? I belive it was under one of the options tabs, and it really makes things smoother on my machine if everything is preloaded (though ofcourse, loading is a bit longer). Also, what filesystem are you using? I'm guessing ext3, however, I personally use ReiserFS, though I don't think either should make a difference for gameplay, if you got time to kill, it could be something to test out. The other thing, try compiling your kernel from scratch with the nitro patchset, that should definatly help performance. It might take a few tries if you've never compiled a kernel before, but once you do it, it can help quite a bit. [http://www.ubuntuforums.org/showthread.php?t=43065](http://www.ubuntuforums.org/showthread.php?t=43065) this is my favorite guide to use, and the instructions for using the nitro patchset work with this guide, and you should be able to logically fit the instructions together. If you can't figure it out, i'll be glad to help. I believe [http://forums.gentoo.org/viewtopic-t-434049-highlight-nitro+2+6.html?sid=4db12c799cf55d471706661097831fc0](http://forums.gentoo.org/viewtopic-t-434049-highlight-nitro+2+6.html?sid=4db12c799cf55d471706661097831fc0) is the latest patchset, [http://forums.gentoo.org/viewtopic-t-423251-highlight-nitro+2+6.html?sid=4db12c799cf55d471706661097831fc0](http://forums.gentoo.org/viewtopic-t-423251-highlight-nitro+2+6.html?sid=4db12c799cf55d471706661097831fc0) is the latest stable one. I would wait till 2.6.16 comes out though.

---

### Post by handy on 2006-03-04
On my machine, ut2k4 runs atleast as fast on Ubuntu as it did xp pro', with everything turned up to the max in settings.  It plays faultlesly under all conditions.  

I pre-load on both of them.  

No other tweaks at all.

---

### Post by Eazy© on 2006-03-04
[QUOTE=Zeroedout]outta curiousity, how much RAM do you have? In UT2004 If you have more than 512, are you loading all the textures to RAM? I belive it was under one of the options tabs, and it really makes things smoother on my machine if everything is preloaded (though ofcourse, loading is a bit longer). Also, what filesystem are you using? I'm guessing ext3, however, I personally use ReiserFS, though I don't think either should make a difference for gameplay, if you got time to kill, it could be something to test out. The other thing, try compiling your kernel from scratch with the nitro patchset, that should definatly help performance. It might take a few tries if you've never compiled a kernel before, but once you do it, it can help quite a bit. [http://www.ubuntuforums.org/showthread.php?t=43065](http://www.ubuntuforums.org/showthread.php?t=43065) this is my favorite guide to use, and the instructions for using the nitro patchset work with this guide, and you should be able to logically fit the instructions together. If you can't figure it out, i'll be glad to help. I believe [http://forums.gentoo.org/viewtopic-t-434049-highlight-nitro+2+6.html?sid=4db12c799cf55d471706661097831fc0](http://forums.gentoo.org/viewtopic-t-434049-highlight-nitro+2+6.html?sid=4db12c799cf55d471706661097831fc0) is the latest patchset, [http://forums.gentoo.org/viewtopic-t-423251-highlight-nitro+2+6.html?sid=4db12c799cf55d471706661097831fc0](http://forums.gentoo.org/viewtopic-t-423251-highlight-nitro+2+6.html?sid=4db12c799cf55d471706661097831fc0) is the latest stable one. I would wait till 2.6.16 comes out though.[/QUOTE]


Hi and thanx for your respond!

First I have to admit that I have been stupid to use DM-Deck17 as my "testmap", becaus it is not very optimized, and maybe OpenGL is not made for that map. The "smoke pillar" in the center of that map really make the game lag. Deck17 runs very smooth on Direct3D though. I have tried many other maps and it runs fairly well as it is now, but not as good as in Direct3D (maybe I shouldnt ask for that).

I have 1024 Mb RAM, and preloading is on. I allready use ReiserFS, and I have compiled a Vanilla kernel using this guide: [http://www.ubuntuforums.org/showthread.php?t=84174](http://www.ubuntuforums.org/showthread.php?t=84174) 
I have tried with both 2.6.14 and 2.6.15 kernel with different ck-patches, but after installing my new kernel I had some trouble with the sound in UT2004. I compiled my own openal (have a Sund Blaster 5.1 digital soundcard) and it didnt work (no sound at all) with the new kernel, so I went back to my Ubuntu kernel 2.6.12-10-k7. I also didnt see much gain in performance, so perhaps I did something wrong when compiling the kernel.

I will try once again with the kernel you suggested with the nitro-patch.
When you say from scratch, does that mean that I should leave out to Import the configuration from my 2.6.12-10-k7 kernel, as suggested in the Howto for the Vanilla kernel?

A grateful Eazy :)

---

### Post by handy on 2006-03-05
I have played **deck 17** more than any other level on Ubuntu, 'cause I'm going for the one & only 1 million points on this character...:rolleyes:  

It will impress my son, OK?! :KS 

I have no prob's at all with **deck 17**, (running my machine on bog stock 32bit Breezy 5.10) or anywhere else as previously stated!?

I'm thinking that intense calculations in the CPU might be the bottleneck for you?

What hardware are you running?

Please reply, it will help me understand, so that I can possibly help someone else with this stuff later?

Thanks, 

handy

---

### Post by Zeroedout on 2006-03-05
[quote=Eazy©].....
I have 1024 Mb RAM, and preloading is on. I allready use ReiserFS, and I have compiled a Vanilla kernel using this guide: [http://www.ubuntuforums.org/showthread.php?t=84174]("http://www.ubuntuforums.org/showthread.php?t=84174") 
I have tried with both 2.6.14 and 2.6.15 kernel with different ck-patches, but after installing my new kernel I had some trouble with the sound in UT2004. I compiled my own openal (have a Sund Blaster 5.1 digital soundcard) and it didnt work (no sound at all) with the new kernel, so I went back to my Ubuntu kernel 2.6.12-10-k7. I also didnt see much gain in performance, so perhaps I did something wrong when compiling the kernel.

I will try once again with the kernel you suggested with the nitro-patch.
When you say from scratch, does that mean that I should leave out to Import the configuration from my 2.6.12-10-k7 kernel, as suggested in the Howto for the Vanilla kernel?

A grateful Eazy :)[/quote] 
Yea, i've tried compiling my own openal aswell, but i had the same prob. When you compile the kernel, you made sure that the option for supporting a gig of ram was compiled in? It's weird that the D3D smoke effect isn't causing much of a slowdown but opengl is. Why don't you try running one of the ut2k4 benchmarks, and compare the average FPS? That way you'll know forsure if it's actually the renderers/OS, or something else. If the d3d smoke effect is as good looking but not causing a slow down, it'd be something to investigate.

---

### Post by aljones15 on 2006-03-05
I installed the ut2004 demo on my machine and it's slow as molasses. it's actually slower than doom 3 (which runs ok with all the options turned off) and Quake 3 runs perfectly on my computer with everything on or near highest. I've tried turning everything in UT2004 off and it still lags even when not on the net. I think UT for linux is probably a shoddy port and that's the problem. I have counter-strike running in wine with all graphics options set to the lowest and it's more playable than UT. Never seen anything like it.

---

### Post by Eazy© on 2006-03-05
@handy
My hardware:
MB: Abit NF7 nForce2 Based AMD FSB400, Dual DDR400, AGP 8X

CPU: AMD Athlon XP 2600+ Thoroughbred

VGA: Gainward Geforce 6600 GT 128MB AGP (slightly overclocked. Seems to improve some.)

RAM: Apacer
        DRAM Size   1024 Mb (1012 Mb)
        DRAM Frequency  133.1 MHz
        FSB: DRAM  1:1
        CAS# Latency  2.0 clocks
        RAS# to CAS#  3 clocks
        RAS# Precharge  3 clocks
        Cycle Time (TRAS)  6 clocks
  # of memory modules  3
        Module 0   DDR-SDRAM PC2700 - 256 MBytes
        Module 1   DDR-SDRAM PC2700 - 512 MBytes
        Module 2   DDR-SDRAM PC2700 - 256 MBytes

Soundcard: Sound Blaster 5.1 digital

@Zeroedout
I did compile for supporting 1 gig ram and above (option: "High Memory Support --4GB -if you have more than 1GB of RAM" in menuconfig)

I will try the ut2k4 benchmarks, but there is nothing wrong with the FPS in Linux. If I look at the smoke pillar on Deck17 the FPS is good, about 90-100 FPS but it lags anyway, but I will try with benchmark and compare the result with Windows. I only need to figure out how to run benchmark in Linux first :)

---

### Post by Eazy© on 2006-03-05
Ok, I have made some benchmarks now using Umark, and it don't look good. When I compare ingame with "stat fps" it gives me the same FPS in both Linux and Windows, but the results in the benchmarks showes something else. 

So here are the results that Umark gives:

Linux:
[IMG]http://web.telia.com/~u00175529/UmarkLinux.png[/IMG]

Windows:
[IMG]http://web.telia.com/~u00175529/UmarkWinXP.png[/IMG]

Problems is that I play too much to have to boot to windows all the time, and the result of booting to windows when I want to play, is that I dont boot back to Linux, becaus I can do all the other things I like to do i Windows also. So if any one has a solution to my problem, it means I can stay in Linux, and that is what I really want :)

---

### Post by Lord Illidan on 2006-03-05
In your /etc/x11/xorg.conf, is there an entry under Device like this:

        Option          "RenderAccel"           "true"

---

### Post by Eazy© on 2006-03-05
[QUOTE=Lord Illidan]In your /etc/x11/xorg.conf, is there an entry under Device like this:

        Option          "RenderAccel"           "true"[/QUOTE]

When I have that in my Xorg.config the text in 2D becomes bugy. I have tested to put it in my xorg.config and made a benchmark, but it didn't improve the score or FPS.

---

### Post by handy on 2006-03-05
[QUOTE=aljones15]I installed the ut2004 demo on my machine and it's slow as molasses. it's actually slower than doom 3 (which runs ok with all the options turned off) and Quake 3 runs perfectly on my computer with everything on or near highest. I've tried turning everything in UT2004 off and it still lags even when not on the net. I think UT for linux is probably a shoddy port and that's the problem. I have counter-strike running in wine with all graphics options set to the lowest and it's more playable than UT. Never seen anything like it.[/QUOTE]

Having installed ut2k4 on more than one machine, & having run it under both 64bit & 32bit Breezy on my own machine without any prob's, with everything on to the max & 1600 x 1200 res', I don't believe that the linux ut2k4 install is buggy, & to call that game shoddy in anyway at all is almost blasphemy!! :KS  

Ut2k4, is not new software, it really should be well sorted by now, as far as compatibility issues are concerned.

I will be very interested to see how these problems pan out? :confused:

---

### Post by Draco Houston on 2006-03-06
I think it should also be noted that the Unreal engines (including the one they are currently working on) are all made using OpenGL, not DirectX. Just because it runs on windows doesn't mean that it is programmed with DirectX. Many games use OpenGL. The only thing that will change over the operating system is the drivers you are using.

---

### Post by leech on 2006-03-06
Are you sure you're not mistaking that for the Doom/Quake games?  They're developed using OpenGL, always have been since Quake 2 (if memory serves me right, though most of the time it doesn't, damn I'm getting old ;) )  

I always had heard that the Unreal Engine was developed using DirectX, but also has a pipeline developed for OpenGL, originally the first Unreal was developed for Software Mode and 3Dfx and PowerVR only, then patches added Direct3D and OpenGL.  I think Rendition was the other pipeline it supported.  Thank goodness we're now just down to OpenGL and DirectX, unlike the early days of 3D gaming when it was a lot more split up.

Leech

---

### Post by Curlydave on 2006-03-06
It might be because you're used to using Vsync. Graphics will always seem laggy with it off, and there's no way AFAIK to enable it in Linux.

---

### Post by Zeroedout on 2006-03-07
[quote=Curlydave]It might be because you're used to using Vsync. Graphics will always seem laggy with it off, and there's no way AFAIK to enable it in Linux.[/quote]

Really? If memory serves, I'm pretty sure their was an option for it in fglrx's xorg.conf. Though i could be wrong, i'm sure it was possbile to enable Vsync.

---

### Post by handy on 2006-03-07
I still wonder why these problems persist, we can see hardware that should do the job perfectly, yet still there are all these complications...

:confused: ?? :confused:

---

### Post by Eazy© on 2006-03-07
nvidia-settings --> OpenGL settings --> tick "Sync to VBlank" Be sure to enabel it in ut2004.ini also if you want to use it.

I do not use Vsync, becaus it works better without it on.

If the UT-series is made for OpenGL, I think it's strange it works better on Direct3D.

Would be nice if someone could post their Umark results so I had something to compare with, it would be great. [http://unrealmark.net/](http://unrealmark.net/)

One could also benchmark without Umark by follow [this]("http://64.233.179.104/search?q=cache:2xUMFkgL3xEJ:www.linux-gamers.net/modules/wiwimod/index.php%3Fpage%3DTWEAKGUIDE%2BUT2004+benchmark+ut2k4+linux&hl=sv&gl=se&ct=clnk&cd=4&client=firefox-a") guide (scroll down to Benchmarking).

I have almost given up hope in this matter, and maybe I have say good bye to Linux until I get better harware or have stoped gaming :cry:

---

### Post by handy on 2006-03-07
[QUOTE=Eazy©]nvidia-settings --> OpenGL settings --> tick "Sync to VBlank" Be sure to enabel it in ut2004.ini also if you want to use it.

I do not use Vsync, becaus it works better without it on.

If the UT-series is made for OpenGL, I think it's strange it works better on Direct3D.

Would be nice if someone could post their Umark results so I had something to compare with, it would be great. [http://unrealmark.net/](http://unrealmark.net/)

One could also benchmark without Umark by follow [this]("http://64.233.179.104/search?q=cache:2xUMFkgL3xEJ:www.linux-gamers.net/modules/wiwimod/index.php%3Fpage%3DTWEAKGUIDE%2BUT2004+benchmark+ut2k4+linux&hl=sv&gl=se&ct=clnk&cd=4&client=firefox-a") guide (scroll down to Benchmarking).

I have almost given up hope in this matter, and maybe I have say good bye to Linux until I get better harware or have stoped gaming :cry:[/QUOTE]

In my experience ut2k4 does not work better in direct3d!

If it is not settings, (& I changed none in Ubuntu) then it is hardware.

I'm using a 6800gt card, but I can't see why it won't work great at lower res' or with out so many graphics enhancements turned on?

Within limits of course... Whether your machine is the borderline... I have no idea!?

Sorry that I'm not much help at the moment, I'll see if I can find the time tomorrow night & look at  benchmarking for you.

---

### Post by cleary on 2006-03-07
Do you have the latest patches for ut?

In my experience I've run it (without issue) on vanilla kubuntu 5.04 with the following hardware:

s754 A64 3000+
512MB ram
nvidia FX5900 vanilla

s939 A64 3200+
1GB ram
nvidia 6600GT

I also ran ut2003 on an athlon 1.4/512MB/ti4200 running mandrake 9 and it was ok.
UT series have been the most hassle free proprietary games I've ever played under linux - love em ;)

---

### Post by Eazy© on 2006-03-08
Yes, I have the latest patch.

Einstein once said: "Everything is relative". Maybe if you would test to play on my machine, you maybe wouldn't experience the game to be as laggy as I do, and maybe I'm picky.  

All ppl here that says that UT2004 runs great, have you compared the game with Direct3D? I'm not saying that UT2004 dosen't run well on your computers, I'm just frustrated becaus most ppl says it runs well on their machines and I wonder what I'm might have done wrong configure my computer and UT2004.

---

### Post by handy on 2006-03-08
Again I say direct3d is no better on my machine.

I think that you should dual boot, it will solve both problems.

Horses for courses.

---

### Post by Zeroedout on 2006-03-08
hrmm, in post 18, your average fps was 85, strangly close to the refresh rate a moniter could be set at.......... Did you check in your xorg.conf to make sure Vsync is disabled? (I know you said that you did in nividia settings thing, but it's possible it was disabling it in some other way as opposed to disabling it right in xorg.conf. If it is disabled in xorg.conf , we know forsure it can't be an issue). That's the only thing I can think of. If that doesn't work, then you have one REALLY strange issue! congrats. Thats one of the pains of an open architecture (not that they outweigh the benifits, in my opinion anyway), point one for propriatry hardware.

---

### Post by Eazy© on 2006-07-17
First, I'm sorry to post on this old thread, but I never solved this until now. 

I got myselfe a new rig thinking it would solve my problem. The computer parts I bought would be enough to play ut2004 twice at the same time.

I bought a AMD 64 x2 4400+, Nvidia 7900GT, MSI-K8N, 1024 mb ram. This would be enough for UT2004 I was thinking while I reinstalled Kubuntu. As usually, I installed the smp K7-Kernel as I though should. Lastly I installed UT2004. I started UT2004 and tried it out. Dudes, I almost cried, It was the same s**t as with my old hardware. :confused: ](*,) 

I have always installed the K7-Kernel after a fresh install of (K)Ubuntu as I have a AMD cpu. For some reason (I dont know why) I installed the i386-Kernel and tried to play UT2004. I almost cried again, but now with a smile on face :) All the troubles are gone, and its no diffrence from D3D.

So if you have the same or simular problem as I have, try with installing the i386-kernel if you have the K7-kernel installed.

It dosent matter for me if the K7-kernel dont work with UT2004, but it makes you wounder why it dont work (for me atleast).

---

### Post by vem0m on 2006-07-17
openGL is alot better thing is its all the other stuff u may have runnign causing that mine runs smoother on Linux then WinXP ever would have thought of running it simply for the fact XP along with every windows version after 95 is BLOATED and full of bugs, Viruses and Spyware

---

### Post by dlai on 2006-07-18
I'm glad it worked out... wow alot of trouble you went through. Thanks for the tip on the k7-kernel, had the exact same problem.

---

### Post by leech on 2006-07-19
That's quite odd that it doesn't work well with the k7 kernel for you.  I haven't played it in quite sometime, maybe I should give it a shot.  The only thing I could think of that would cause this, would be that UT2k4 doesn't support some of the AMD extensions as it should.  Or possibly the nvidia drivers do not.

I have an AMD 64 as well, and haven't had any problems with performance of UT2k4, I play it at 1600x1200 with everything set to max as well.

Leech

---

### Post by User_Program on 2006-07-19
When following this thread I though it was a Umark bug.  Setting Umark to low detail gives me a lower score then in high detail?  But it looks like you have fixed the problem.  If you still need the comparison.  I don't use Windows so it will be alittle onesided.

[IMG]http://webpages.charter.net/user_program/Images/Umarkscore.jpeg[/IMG]

---

### Post by Eazy© on 2006-07-21
[IMG]http://web.telia.com/~u00175529/umark.png[/IMG]

This is on my new hardware:

Mainboard: MSI K8N SLI
CPU: AMD Athlon 64 X2 Dual Core Processor 4400+
GFX: GeForce 7900 GT
RAM: 1024 Mb

Kernel: 2.6.15-23-386

This score is good enough for me. UT2004 run very nice now. If anyone has any idea of why the K7-kernel gives bad performance, I wouldnt mind if you post a solution :)

Ps. Would be nice if more ppl post their results with umark!

---

### Post by mushroom.ru on 2006-07-28
I have exactly the same problem on my PC
Ubuntu Dapper 6.06
Intel D865PERL
Intel Pentium IV - 3,2 Ghz
1024 Mb RAM
Ati Radeon 9600XT 256 Mb

ut2004 for linux is laggy against windows version.

I have 2.6.15-26-386 kernel compiled with fglrx support using this manual [http://ubuntuforums.org/showpost.php?p=1108696&postcount=26](http://ubuntuforums.org/showpost.php?p=1108696&postcount=26)

Maybe i had mistake in my configuration.
Can anyone give advice?

---

### Post by Perfect Storm on 2006-07-28
Try change kernel:
```
sudo apt-get install linux-686
```
reboot.

and see if it have an impact

---

### Post by Miguel on 2006-07-28
> **Artificial Intelligence said:**
> Try change kernel:
```
sudo apt-get install linux-686
```
reboot.

and see if it have an impact

Quite a few people are experiencing lack of frequency scaling with the 686 kernel. It's curious, because the gnome applet shows the frequency that should be but "cat /proc/cpuinfo" always reports max MHz.

---

### Post by mushroom.ru on 2006-07-31
> **Artificial Intelligence said:**
> Try change kernel:
```
sudo apt-get install linux-686
```
reboot.

and see if it have an impact


Big thanks Artificial Intelligence. It`s all that i need.:p ;) :D ;-) 

Another big thanks.
It`s now perfect and smooth graphic. 
I`d configure much better graphic in my ut2004 for linux version than in my windows version and there`re no lags. I`m happy.

---

