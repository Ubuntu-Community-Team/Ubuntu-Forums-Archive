---
title: "Reviving what should be left dead."
date: 2013-07-30
forum: Desktop Environments
---

### Post by dark ariel7 on 2013-07-30
I just got a new windows 8 laptop so I gave my dad my older desktop that I built from scratch. It was no speed demon running a dual core celeron e1200 1gb of ram and a nvidia gt430. It is currently running windows 7 fine. I am now trying to revive my dads old piece of junk. It has 1gb of, i believe, ddr1 ram, a 2.3Ghz processor and a pci, not pcie, gt 520. I don't want or need it to roar and blast through 1080 content or play games. I only want to browse the web with no lag and to watch SD video online on crunchyroll. Lubuntu was actually a little too and I mean a little too heavy. Video lagged ever so slightly. Still noticeable though. I have not tried puppy linux but I am not partial for it. I have tried it before. It is a little lacking in support and a little complicated for simple manners such as drivers. As a last resort it doable but not a first choice. I am downloading joli OS to attempt that as a solution. Does anyone know anything that would work?

---

### Post by bfmetcalf on 2013-07-30
You could try ArchLinux or a derivative with just an window manager like openbox.  Runs pretty well on my Raspberry Pi which has less in it than that computer does.

---

### Post by lykwydchykyn on 2013-07-30
"slow" is subjective, but you should get reasonable performance out of that hardware.  There are tons of lightweight distros out there, but the question is how bare-bones do you want to go to get a little more performance?  

Web browsing isn't the simple task it was ten years ago; all the javascript & css animations, flash, and hi-res images are pretty taxing on an older system, especially if you don't have a good video driver available.   You can get a lighter environment and maybe save a few MB of system RAM and a few CPU cycles, but if web and video is laggy I suspect your bottleneck is with GPU support.  What driver were you using with the gt 520?

---

### Post by dark ariel7 on 2013-07-31
well like I mentioned I am not super high on the idea of barebones precisely because support for things like video drivers is lacking.when I installed ubuntu on it it had a hard time until I installed the "Current" Nvidia driver but it was still a little laggy on the video side. Lubuntu was ok from the start but is laggy ever so slightly. For Lubuntu I am not sure what the driver is but I got it from the propriatery extra drivers. Lubuntu like is really my limit on barebones.

---

### Post by skinnymg1 on 2013-07-31
Try install Ubuntu and then installing a lighter weight DE. There are many to choose from. I would suggest Fluxbox, but that is my own opinion. With the stats you quoted though Xubuntu should be ok.

---

### Post by dark ariel7 on 2013-07-31
[SIZE=2][FONT=arial]I dont think a ubuntu derivative will work. I even tried lubuntu the lightest one and it still lagged. Although like 
[/FONT][/SIZE][SIZE=2][FONT=arial][lykwydchykyn]("http://ubuntuforums.org/member.php?u=603141")  mentioned it could very weill be a driver issse. If anyone knows the proper driver for this card under lubuntu and or ubuntu that may help.[/FONT][/SIZE]

---

### Post by lykwydchykyn on 2013-07-31
> **dark ariel7 said:**
> [SIZE=2][FONT=arial]I dont think a ubuntu derivative will work. I even tried lubuntu the lightest one and it still lagged. Although like 
[/FONT][/SIZE][SIZE=2][FONT=arial][lykwydchykyn]("http://ubuntuforums.org/member.php?u=603141")  mentioned it could very weill be a driver issse. If anyone knows the proper driver for this card under lubuntu and or ubuntu that may help.[/FONT][/SIZE]

There's really only two options; the built-in open source driver (nouveau) or the proprietary Nvidia driver.  There's no guarantee that an older card is going to be well-supported by either of those.

It might be worth trying some completely non-Ubuntu, non-Debian distro just to see if your hardware is happier with it.  Distros do tend to patch up X11 and mesa in small-but-possibly-significant different ways, so maybe a Fedora, OpenSuse, SlackWare, or (as already suggested) Arch Linux would perform differently.  

Of course, before you do that, it might be worth watching the output of "top" or "htop" while you play back a video just to see if there's a clear bottleneck in the system resources.

---

### Post by dark ariel7 on 2013-07-31
[COLOR=#000000]"Of course, before you do that, it might be worth watching the output of "top" or "htop" while you play back a video just to see if there's a clear bottleneck in the system resources"[/COLOR]
[COLOR=#000000]I have no idea what that means. I will however most definitely try a non ubuntu os.[/COLOR]

---

### Post by slw210 on 2013-07-31
antiX is pretty lightweight.

I run Ubuntu 12.04 LTS on an old PIII 933MHz, 512MB RAM with nVidia GeForce 2 and Xubuntu 12.04 LTS on AMD Duron 900MHz, 768MB RAM with onboard S3 Twister, for old 2000 era hardware they seem to run pretty bug free right out of the box.

Only Ubuntu I could get running right on the AMD w/onboard S3 Twister was the Xubuntu LTS. Zorin OS lite, antiX and Crunchbang were also fast and light as were all the Puppy distro's including Simplicity.

What I could do with your "*old piece of junk*". If nothing else get a new card.

---

### Post by dark ariel7 on 2013-07-31
Is the pci gt 520 really not good enough for flash video anymore? Really I am only hoping for 360p or 480p payback.

---

### Post by dark ariel7 on 2013-07-31
will running openbox on lubuntu help out?

---

### Post by sudodus on 2013-07-31
> **dark ariel7 said:**
> [COLOR=#000000]"Of course, before you do that, it might be worth watching the output of "top" or "htop" while you play back a video just to see if there's a clear bottleneck in the system resources"[/COLOR]
[COLOR=#000000]
I have no idea what that means. I will however most definitely try a non ubuntu os.[/COLOR]

Open a terminal window and run the command

```
top
```

and check how hard the CPU is working (is it near 100%?) when you watch a video.

You can also try ***Knoppix***, which is good at recognizing hardware. It is often good at running old hardware.

---

### Post by sudodus on 2013-07-31
> **dark ariel7 said:**
> will running openbox on lubuntu help out?

In some cases yes. It is easy to login to the Openbox session. I use it sometimes to run video.

---

### Post by dark ariel7 on 2013-07-31
I tried Lubuntu and monitored the CPU usage. It was constantly at 100% while playing a video. Does that mean that it is a lost cause? I will keep trying, at least for now, to see if I can squeeze a little more performance.

---

### Post by dark ariel7 on 2013-07-31
Fedora LXDE 19 will simply not boot I get as far as [here]("http://www.tecmint.com/wp-content/uploads/2013/07/f-1.jpg"). I tried it on my laptop and on the old PC but it simply does not boot live. I had a similar issue on all my other install but I fixed it by booting with [FONT=Ubuntu Mono]nomodset activated in ubuntu.[/FONT]

---

### Post by dark ariel7 on 2013-08-01
tried fedora 19 xfce same thing ocurred.

---

### Post by QIII on 2013-08-01
Bodhi Linux is based on Ubuntu 12.04 -- stripped down to the chassis and using Enlightenment 17.

Worth a try.  Should work very well on those specs.

---

### Post by dark ariel7 on 2013-08-01
tried fedora 19 xfce same thing ocurred. I will give Bodhi A try. I need a lighter browser too though. I only need flash but google chrome seems to be  a little too heavy.

---

### Post by sudodus on 2013-08-01
nvidia gt430 works well with a proprietary graphics driver. It will improve the performance a lot and also make it possible to use vdpau, that helps playing mp4 files with h264 encoding using the gpu (instead of the cpu).

When the cpu is at 100%, it is limiting the performance.

Was this when you were running flash video in the browser? Unfortunately the flash software is proprietary, and the linux version is not as good as the Windows version. It needs better hardware for the same performance. Sometimes it is possible to download a video file version and play it locally with some light video player, for example mplayer or mplayer2.

Try Lubuntu's openbox session, and try Knoppix (as well as Bodhi)

Good luck :-)

---

### Post by dark ariel7 on 2013-08-01
[FONT=arial]I tried the openbox session but saw no notisable results. The 100% was indeed while playing flash video. I feel like flash is super bloated if it takes more than a 2.3GHz processor just to play SD and low quality video. Fedora, if it ever works, looks promising and so does knoppix. I wanna give lubuntu another chance but I dont feel like it will make it. Do you think that there is any chance that a better driver will help cpu usage? I found that on my old desktop when I installed the appropriate driver even non-gpu heavy task went better because the software took better advantage of the hardware and the Gpu took some stress off of the Cpu. Also do you think any BIO settings will help?
As a total tangent does anyone know why I have to enable [COLOR=#000000]nomodset too boot Ubuntu?[/COLOR][/FONT]

---

### Post by sudodus on 2013-08-01
The problem with flash is the same for all linux distros. If it is possible to play the video with an old version of flash, that might be less bloated and faster. But then you have the security risk :-/ Otherwise I think there is no easy solution with flash.

It is really worthwhile to install a proprietary driver for nvidia gt430. I run it like that with Ubuntu/Lubuntu 12.04.2 and Ubuntu Studio 12.04.2 in an ageing hp xw8400 workstation with Xeon CPUs. I run version 304.88.

```
$ glxinfo|grep -i opengl
OpenGL vendor string: NVIDIA Corporation
OpenGL renderer string: GeForce GT 430/PCIe/SSE2
OpenGL version string: 4.2.0 NVIDIA 304.88
OpenGL shading language version string: 4.20 NVIDIA via Cg compiler
```

---

### Post by gordintoronto on 2013-08-01
Exactly what CPU is in the computer? You can run this command: lshw -class cpu

---

### Post by dark ariel7 on 2013-08-01
intel celeron  cpu 2.93 GHz
version 15.3.4
serial 0000-0F34-0000-0000-0000-0000

---

### Post by dark ariel7 on 2013-08-01
also I have been unclear because I had a box for a different card in my desk that I kept reading as I was writting. I have a PCI(not e) GT 520 from Zotac in my old hunk of junk.

---

### Post by sudodus on 2013-08-02
> **dark ariel7 said:**
> intel celeron  cpu 2.93 GHz
version 15.3.4
serial 0000-0F34-0000-0000-0000-0000

I would use Lubuntu or Xubuntu with that CPU.

---

### Post by sudodus on 2013-08-02
> **dark ariel7 said:**
> also I have been unclear because I had a box for a different card in my desk that I kept reading as I was writting. I have a PCI(not e) GT 520 from Zotac in my old hunk of junk.

It is still worthwhile to try an nvidia proprietary driver. I'm not sure that it works, but it is worth trying.

---

### Post by dark ariel7 on 2013-08-02
that is actually what I am trying at the moment. installing as I write this.

---

### Post by dark ariel7 on 2013-08-02
and now ubuntu will not recognize my card and does not show any proprietary drivers for my system. I installed ubuntu once before on this pc and installed Nvidia current and it worked but I cant get anything from the software sources section of settings. Any clues?

---

### Post by dark ariel7 on 2013-08-02
also should that processor be capable of running flash video? because if not then it is not even worth talking about. except maybe for kicks.

---

### Post by sudodus on 2013-08-02
1. Which version are you trying (12.04 or 13.04)? And which flavour (Lubuntu, Xubuntu, Ubuntu)? If no proprietary graphics is found, it is because it has been dropped. If 12.04 has no working proprietary graphics, there is no currently supported Ubuntu flavour and version (that supports your graphics card).

2. Do you mean the Celeron CPU? I think it should be able to run at least low resolution (360) videos with flash.

You could try some other linux distros, that might cooperate better with your old hardware: ***Knoppix*** and ***Puppy***. See also this link
[URL="http://ubuntuforums.org/showthread.php?t=2130640"]
Old hardware[/URL]

---

### Post by dark ariel7 on 2013-08-02
I am running the latest but will now fall back to the lts to see if then I get video drivers. Also is it really so bad to run an old OS? I was thinking of going back to the previous lts fpr ubuntu to see if I got any speed boost.

---

### Post by sudodus on 2013-08-02
For speed running an old computer it is good to go back to an old version of the OS. But you will get no security updates. If that does not bother you (if you use the computer only for playing or watching video, it can be OK. Or if you run a live system (without writing to disk (only to ram-drive), the system will be fresh again after rebooting, so it is not a big problem, if you would get some malware.

I would recommend that you try Xubuntu 12.04, and if it is not good, try Knoppix and Puppy. If they are not good, try an old version of Ubuntu or Xubuntu or Lubuntu.

If you only want to play with it, you can try anything small or old, also the extremely small DSL, damn small linux, and Kolibri (even smaller, but not linux).

---

### Post by dark ariel7 on 2013-08-02
OH and what do you think would be the oldest version of flash I can get away with? and how do I install such a version.

---

### Post by sudodus on 2013-08-02
I have no idea, it depends on what you want to play. [COLOR=#ff0000]Maybe someone else who is reading this can give good advice about Ubuntu versions and Flash versions.[/COLOR] Unfortunately the internet is continuously demanding more advanced graphic capability, so it is not possible to use old hardware for the modern internet pages with a lot of fance eye-candy and high-resolution video and inefficient flash software ...

But old computers can still do many other tasks.

---

### Post by dark ariel7 on 2013-08-02
I have to say this card is somewhat pissing me off. It will play a 720 mkv file from my pc no prob. there is the slightest amount of stutter, very watchable. It get constant solid 60fps in glxgears. However it will not play 360 video off the internet?!? nonsense. I must say that Xubuntu 13 really is a speed upgrade from ubuntu. Still no real support for the card though. Should I try installing directly from Nvidia?

---

### Post by dark ariel7 on 2013-08-03
Ok now I am past peeved and have reached raging rage. I installed windows 7 because I heard that it actually offers better performance with older hardware than windows XP. What happened? Well everything went perfectly fine and the it now plays SD video fine. Windows beat linux in this instance I guess.

---

### Post by sudodus on 2013-08-03
Well, the companies making propríetary tools support each other. Flash is optimized for Windows, (but not for linux, because there is too little money to earn).

---

### Post by hansdown on 2013-08-03
> **sudodus said:**
> Well, the companies making propríetary tools support each other. Flash is optimized for Windows, (but not for linux, because there is too little money to earn).

True +1.

---

### Post by Artemis3 on 2013-08-03
Yes, please understand Flash is proprietary, it is Adobe's sole responsibility for being so... slow in linux, which is why most people want to get rid of it asap. You cannot blame Linux or praise Windows for it, Adobe was optimized for Windows, and ignored/abandoned linux.

I simply avoid flash and especially flash video streaming with these old machines. There are some ways to make the streams be opened from, say, mplayer/vlc/totem for sites like youtube using plugins etc that might help; or one of the open source attempts.

---

### Post by dark ariel7 on 2013-08-03
well in this case it is not just the flash though. I think that windows deserves the praise because it is working flawlessly on a 10+ year old system. The whole system seems snappier. It is due, I think, to a lack of support for my video card on all other linux distributions. Even puppy linux crashed when I tried booting it. Sad really, I wanted to play with a linux system.

---

### Post by pqwoerituytrueiwoq on 2013-08-03
> **Artemis3 said:**
> Yes, please understand Flash is proprietary, it is Adobe's sole responsibility for being so... slow in linux, which is why most people want to get rid of it asap. You cannot blame Linux or praise Windows for it, Adobe was optimized for Windows, and ignored/abandoned linux.

I simply avoid flash and especially flash video streaming with these old machines. There are some ways to make the streams be opened from, say, mplayer/vlc/totem for sites like youtube using plugins etc that might help; or one of the open source attempts.as long as they don't use DRM you can use this method to play them in mplayer, vlt, totem, etc.
here is the script i made to find and play them off the ram
[http://pastebin.com/dFamyLd5](http://pastebin.com/dFamyLd5)
as long as the video downloads faster than it plays it works perfect
just pause it in the browser and run the script via a panel launcher

---

