---
title: "video game recording have black screen"
date: 2014-02-02
forum: Gaming &amp; Leisure
---

### Post by goodbye-windows(tm) on 2014-02-02
Hi all, 

I've tried just about everything to record criticalmass game sessions on my desktop. I have plenty of processor power, but the recordings come out with a black screen (sound is normal). 

The game doesn't allow me to minimize the window with the game in it, so I have to start the recording, then click on the icon to start the game play. Then, when the game is ended, I have to switch back to the desktop screen and terminate the recording. The portions of the recording before and after the game play are normal and look great. I'm not sure if I have a problem with my system or whether the video recording program isn't being properly told to record the games window.

```
xub1204@xub1204-System-Product-Name:~$ sudo lshw -C display
[sudo] password for xub1204: 
  *-display               
       description: VGA compatible controller
       product: RS780L [Radeon 3000]
       vendor: Hynix Semiconductor (Hyundai Electronics)
       physical id: 5
       bus info: pci@0000:01:05.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi vga_controller bus_master cap_list rom
       configuration: driver=fglrx_pci latency=0
       resources: irq:18 memory:d0000000-dfffffff ioport:d000(size=256) memory:febe0000-febeffff memory:fea00000-feafffff
xub1204@xub1204-System-Product-Name:~$ 

```

I'm running 12.04 Ubuntu. 

Criticalmass is in the software center, so it's available for download if someone wants to test their system with it.

TIA

Art

---

### Post by gerowen on 2014-02-02
It's installing for me so I'll give it a shot in just a second, but I thought I'd mention something.  To record games, if you're using gtk-recordmydesktop, click "Advanced" and make sure "Full shots at every frame" is checked.  This will eat up more CPU power, but 3-D games and the like won't record properly if it isn't checked.

Here's a screenshot, click to enlarge.
[ATTACH=CONFIG]250017[/ATTACH]

---

### Post by gerowen on 2014-02-02
So here's what it looked like for me when I recorded using gtk-recordmydesktop.  I'm guessing the game window was small because it was set to a different resolution than the desktop size that recordmydesktop was capturing.  I'm trying it at a bigger resolution now and will post back.

Video: [http://youtu.be/HRGHcvHCONA](http://youtu.be/HRGHcvHCONA)

---

### Post by gerowen on 2014-02-02
With the game set to the same resolution as my desktop, using gtk-recordmydesktop with "Full shots at every frame" checked, it worked fine for me.  The only issue I had was when I tried changing the resolution of the game, it acted all crazy and crashed and I couldn't really tell what was going on until it closed.  However, the resolution change did apply and here's a video showing how it looked under these circumstances.

Video: [http://youtu.be/QExHvvcU_dY](http://youtu.be/QExHvvcU_dY)

---

### Post by dannyboy79 on 2014-02-04
i use simplescreenrecorder to record my gameplays

---

### Post by goodbye-windows(tm) on 2014-02-08
This one is going to be marked as 'solved', although I think it's a bit of a cop out::>

I tried everything I could think of in 12.04 and 13.10...except for tracking down and installing a different video driver.

I finally made it work (although not perfectly), by downloading and installing the latest daily build of xubuntu 14.04. I don't have a good positive degree of confidence regarding the 'solution' but it's the best I could do. 

14.04 is very buggy, I hope the programmers and developers do better with 14.04 than they did with 13.10, which is a DISASTER +++.

At this time, I am going to maintain the daily build of 14.04 for the sole purpose of playing my video games that I want to be able to record.

Enjoy

Art

---

### Post by dannyboy79 on 2014-02-08
it most definitely related to your graphics driver as almost all recording software in linux captures with X11, so if you're graphics driver isn't installed properly you won't get great recordings. did you even bother trying simplescreenrecorder?

---

### Post by gerowen on 2014-02-08
> **goodbye-windows(tm) said:**
> This one is going to be marked as 'solved', although I think it's a bit of a cop out::>

I tried everything I could think of in 12.04 and 13.10...except for tracking down and installing a different video driver.

I finally made it work (although not perfectly), by downloading and installing the latest daily build of xubuntu 14.04. I don't have a good positive degree of confidence regarding the 'solution' but it's the best I could do. 

14.04 is very buggy, I hope the programmers and developers do better with 14.04 than they did with 13.10, which is a DISASTER +++.

At this time, I am going to maintain the daily build of 14.04 for the sole purpose of playing my video games that I want to be able to record.

Enjoy

Art

I've been running 13.10 since it was released on both my computers with no issues.  Don't blame the entire operating system for one particular issue.  If anybody is to blame here it's AMD for providing horrible driver support for *nix operating systems.  I am happy to hear you got it working somewhat though, hope you can get it all figured out.

---

### Post by goodbye-windows(tm) on 2014-02-10
> **dannyboy79 said:**
> did you even bother trying simplescreenrecorder?

Hi Danny,

I certainly did try simplescreenrecorder (in 12.04 Xubuntu, and 13.10 Xubuntu, before switching to 14.04 Xubuntu daily release version). I read absolutely every single bit of docs and indepenent posts about it (using google search). I wrote the author after exhausting all other self help tech support venues. I spent the vast majority of my effort trying to make simplescreenrecorder work.

In 14.04 pre-release version, it works, but the game is about 1/6 of the entire screen when the video is viewed. But, it's way better than a pure black screen!!! I can view the video in vlc, by using the 'zoom' feature. I'd like to be able to post a youtube video, but  an't do it until I get something that really works. But, for now, using the 'zoom' feature in vlc works well enough to meet my needs.

Regards,

Art

---

### Post by goodbye-windows(tm) on 2014-02-10
> **gerowen said:**
> I've been running 13.10 since it was released on both my computers with no issues.  Don't blame the entire operating system for one particular issue.  If anybody is to blame here it's AMD for providing horrible driver support for *nix operating systems.  I am happy to hear you got it working somewhat though, hope you can get it all figured out.

Glad to hear both your systems run well in 13.10. I wish mine worked as well as yours do.

I don't blame anyone and I do not gripe or bitch about 13.10 performance. Ubuntu is free and offered as is. For me to gripe about it is inappropriate. I'll send you a direct message with more information as I don't want this thread to be about the merit of 13.10-wish I had left the reference about 13.10 out of my past post...hindsight is 20-20.

Enjoy.

Art

---

### Post by dannyboy79 on 2014-02-10
you have a very old radeon card. Are you sure it's supported by fglrx? I would strongly suggest trying the mainline kernel 3.13 along with Oibaf's PPA for mesa and radeon open source driver. You shouldn't have any issues once you figure out your graphics driver issue.

---

### Post by goodbye-windows(tm) on 2014-02-10
> **dannyboy79 said:**
> you have a very old radeon card. Are you sure it's supported by fglrx? I would strongly suggest trying the mainline kernel 3.13 along with Oibaf's PPA for mesa and radeon open source driver. You shouldn't have any issues once you figure out your graphics driver issue.

Hi Danny,

I confess I didn't try any other kernels. I wonder if a newer kernel included with 14.04 is the reason why I have some success video recording the game?? I also had no idea that an open source video driver was available. I'll look into both, thanks for pointing out the alternatives!

I got the Asus mobo and the 6 core processor on a closeout special for $100 plus another $50 for 8 GB of 1600 MHz DDR3 ram, so I saved a bunch of $$ by not having to spend lots of bucks for the very latest and greatest. The only downside to the low cost mobo is the lack of usb 3 ports (I have 8 usb 2 ports) and the SATA ports are not sata 3 (they're sata II ports). I'd spend the extra bucks for a proper video card if it would solve the issue with recording the video games.

I don't need a gaming quality/high end video card as I'm not a serious gamer type. BUT, is buying a low end/medium end video card a viable option for fixing this issue???? I have all my expansion ports available and plan to buy a usb 3 add on card in the near future anyway.

Art

---

### Post by dannyboy79 on 2014-02-10
ok, maybe i'm missing something here. what CPU did you get? your lshw -C display info is showing a radeon 3000, are you saying you don't have a discrete graphics card and you're using the gpu that's built into your CPU (called an APU by AMD) 

And yes, there radeon open source driver is good BUT it's not as good as the proprietary amd driver on some grpahics cards. so it's possible your graphics card would do better with the open source drivers. what kernel are you running? yes, it's most likely because of the kernel in ubuntu 14.04 that you saw improvements. with the later kernel (3.13 for sure) there was major improvements with the radeon open source drivers and like i said, if you use Oibaf's PPA you can get a very recent version of mesa and the open source radeon driver which is far superior to the standrd open source radeon driver that ubuntu 14.04 includes by default.

---

### Post by goodbye-windows(tm) on 2014-02-10
I am saying that I do not have an added video card, I am very confident that I am using the 'card' built onto the mobo. I built (actually updated) the system myself and there are no cards plugged into any of the expansion plugs on the mobo.

The mobo is an ASUS M5A 78L-M LX series unit. The kernel is a .13.0-7-generic (#26-Ubuntu SMP Wed Feb 5 21:28:03 UTC 2014) (per the sysinfo utility program supplied with the 14.04 daily build from about 1 week ago). The GCC version is 4.8 (x86_64-linux-gnu), also per the sysinfo utility program. The Xorg version is 1.15.0 (06 February 2014  11:17:48AM). The cpu (as reported by the sysinfo utility program) is an AMD Phenom(tm) II X6 1045T Processor. 

I just did a fresh lshw, results below. 

sudo lshw -C display
[sudo] password for ofourdaily: 
  *-display               
       description: VGA compatible controller
       product: RS780L [Radeon 3000]
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 5
       bus info: pci@0000:01:05.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi vga_controller bus_master cap_list rom
       configuration: driver=radeon latency=0
       resources: irq:18 memory:d0000000-dfffffff ioport:d000(size=256) memory:febe0000-febeffff memory:fea00000-feafffff
ofourdaily@ofourdaily

I did a report from the system information and profiler program, the full report is posted at:

[http://paste.ubuntu.com/6910894/](http://paste.ubuntu.com/6910894/)

Let me know if you need other info.

Art

---

### Post by dannyboy79 on 2014-02-10
ah i see, you have an older chip. you were having issues before because you were somehow using fglrx (amd catalyst) which isn't even supported anymore. Read here: [http://phoronix.com/scan.php?page=article&item=amd_catalyst_legacy2&num=1](http://phoronix.com/scan.php?page=article&item=amd_catalyst_legacy2&num=1)
so you have no choice BUT to use the radeon open source drivers. If I were you I would install kernel 3.13 from mainline (there's 3 files you download as .deb files) and install them with dpkg and then install Oibaf's PPA for updated mesa from git and then you'll have the best possible graphics drivers for your system. If you want further help just let me know

---

### Post by goodbye-windows(tm) on 2014-02-10
Thanks Danny,

I was looking at Oibaf's PPA while you were replying to the last message. 

I've had this processor and mobo for awhile now, and there has been no signs of a video problem....even netflix runs in wine with the windows software setup. My nephew bought the same mobo and processor, and he doesn't report any quirks or signs of video that ain't up to snuff.

You mentioned installing the 3.13 kernel from mainline.....is that a different kernal than I already have???? Unless a 'mainline' kernel is a different or special beast, I think I already have it. The report I poisted on pastebin shows my current kernel as '3.13.0-7-generic (x86_64)'.

It sure sounds like I need the open source driver though, I'll look into it further.

In the meantime, do I need to install the 'mainline' kernel, or is it the same as the 3.13 kernel I already have???

TY so much for pointing me in the right direction.

Art

---

### Post by dannyboy79 on 2014-02-10
oh, i thought you posted earlier that you had kernel 3.0.7 or something like that. You don't need to install 3.13 mainline kernel since I guess Ubuntu 14.04 has it in there by default. So the only other thing you could do to get better performance from the radeon driver is to activate Oibaf's PPA. So what does sudo lshw -C display return now for your graphics driver?

---

### Post by goodbye-windows(tm) on 2014-02-11
> **dannyboy79 said:**
> So what does sudo lshw -C display return now for your graphics driver?


As of just a few minutes ago, it shows the following:


```
ofourdaily@ofourdaily:~$ sudo lshw -C display
[sudo] password for ofourdaily: 
  *-display               
       description: VGA compatible controller
       product: RS780L [Radeon 3000]
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 5
       bus info: pci@0000:01:05.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi vga_controller bus_master cap_list rom
       configuration: driver=radeon latency=0
       resources: irq:18 memory:d0000000-dfffffff ioport:d000(size=256) memory:febe0000-febeffff memory:fea00000-feafffff
ofourdaily@ofourdaily:~$ 


```

I'm reading about adding the ppa now-it's a big step, but it seems like I need to just DO IT!

I still have my old 12.04 Xubuntu install, I might try it on that install first.

Agn, thanks.

Art

---

### Post by goodbye-windows(tm) on 2014-02-11
Hi Danny,

I'm still reading about the mesa driver(s). 

At [http://www.phoronix.com/scan.php?page=news_item&px=MTQ5OTk](http://www.phoronix.com/scan.php?page=news_item&px=MTQ5OTk) it's stated that the mesa driver will be available as default starting in 14.04.

[HTML]There's lots of new features to Mesa 10.0  and will be officially released in November but it won't be found "out  of the box" in Ubuntu until the 14.04 LTS release next year.[/HTML]

Under the circumstances, I'm wondering if I am already running the mesa driver.....I had no success recording video until I installed a pre-release 14.04 daily build last week. After installing 14.04,  I can record video, although the size of the video is not quite right (yet). 

I did one of the tests for the new mesa driver, and it failed miserably. I also checked the ppa, and the ppa for the mesa driver isn't listed. I'm still working on it......back to the books.

Art

---

### Post by goodbye-windows(tm) on 2014-02-11
Still not sure whether I am already running the mesa driver.

Per the link at: 
[http://phoronix.com/forums/showthread.php?50038-Updated-and-Optimized-Ubuntu-Free-Graphics-Drivers](http://phoronix.com/forums/showthread.php?50038-Updated-and-Optimized-Ubuntu-Free-Graphics-Drivers)

I had to install 'glxinfo'

After that, I got the following results from terminal:

```
ofourdaily@ofourdaily:~$ glxinfo | grep OpenGL
OpenGL vendor string: X.Org
OpenGL renderer string: Gallium 0.4 on AMD RS780
OpenGL core profile version string: 3.1 (Core Profile) Mesa 10.0.1
OpenGL core profile shading language version string: 1.40
OpenGL core profile context flags: (none)
OpenGL core profile extensions:
OpenGL version string: 3.0 Mesa 10.0.1
OpenGL shading language version string: 1.30
OpenGL context flags: (none)
OpenGL extensions:
ofourdaily@ofourdaily:~$ 
```



```
ofourdaily@ofourdaily:~$ dpkg -l | grep libgl1-mesa-dri
ii  libgl1-mesa-dri:amd64                 10.0.1-1ubuntu2                        amd64        free implementation of the OpenGL API -- DRI modules
ii  libgl1-mesa-dri:i386                  10.0.1-1ubuntu2                        i386         free implementation of the OpenGL API -- DRI modules
ofourdaily@ofourdaily:~$
```
.

Oibaf's ppa is not listed, see snapshot of my ppa's, attached.

Am I already running Oibaf's mesa driver???

Art

---

### Post by dannyboy79 on 2014-02-11
it does NOT appear that you activated his ppa yet. when you issue glxinfo it would clearly state the driver type and version with the PPA custom string. Did you issue
```
sudo add-apt-repository ppa:oibaf/graphics-drivers
```
```
sudo apt-get update
```
```
sudo apt-get dist-upgrade
```
after that, run glxinfo again and post what it returns.

---

### Post by bc.haynes on 2014-02-15
I read somewhere (I couldn't find it.) that ATI/AMD is no longer supporting Radeon 2xxx,3xxx, and 4xxx drivers. You may have problems in the future. Sorry to rain on your day, but, I thought you should know.

---

### Post by bc.haynes on 2014-02-15
You might want to see this [http://askubuntu.com/questions/209876/upgraded-ubuntu-from-12-04-to-12-10-ati-radeon-hd-3450-catastrophe](http://askubuntu.com/questions/209876/upgraded-ubuntu-from-12-04-to-12-10-ati-radeon-hd-3450-catastrophe)

---

### Post by dannyboy79 on 2014-02-16
that's only in a stock ubuntu installation, if he uses Oibaf's PPA he'll be fine. Also, to point out that's only in relation to the proprietary ati driver, fglrx. I am helping him to get the open source radeon driver working.

---

