---
title: "3D Cube (Beryl) on Duel Screens off 2 Graphics Cards"
date: 2007-10-15
forum: Desktop Effects &amp; Customization
---

### Post by Agent Stone on 2007-10-15
I have been trying to configure Ubuntu for duel screen, with the 3D Cube effect.

**Goal:**

To have the 3D Cube Effect, as well as Emerald Theme running with my Duel Screen setup.

Hardware Setup: 2 x Nvidia 6800GS (SLI Bridged, but Motherboard supports Software Switching of SLI Mode) with 2 x LCD Monitors - One monitor in one card, the reason for this is because on my Windows Partition, I run SLI, and switch between SLI and duel screen as needed for gaming. For office, and internet, and anything but gaming, I run the Linux Partition on the same hardware configuration.

**Progress & Issues:**

I have installed Beryl and Emerald packages, etc on both Ubuntu 7.04 and 7.1 RC4. When I set up Beryl and Emerald, the desktop effects and 3D cube work perfectly, however setting up duel screen afterwards, disables the desktop effects, and no amount of tweaking of settings could get the effects back, while in duel screen.

I then reinstalled Ubuntu, and tried setting up duel screen first, and then setting up the desktop effects such as the 3D Cube. Which resulted in broken windows, or desktop effects simply not applying, even after reboots, etc.

I am presuming that at present, Beryl, Compiz and Compiz Fusion while have support for the 3D Cube on my Graphics Card, and that as far as I could tell while Beryl has some support for duel screen, it does not have support for duel screen using two graphics cards, one for each screen?

Does anyone know where I am going wrong? Or a workaround for my hardware configuration? The Graphics Cards do have 2 Outputs, so with a DVI to VGA Converter I could run both screens of one monitor. However, it wastes the second card, and in the Windows Partition where I run multiple game clients on both screens, I would need to change the monitor over each time I change between Windows and Linux, which is not ideal.

Worst case, I could get a DVI to VGA Converter and a KVM Switch on some sort, if I can get the 3D Cube, and Desktop Effects to work with Duel Screen of one card to allow easy switching. Ideally using my current configuration is prefered though.

Thanks in advance for any help with this.

---

### Post by Rupertronco on 2007-10-15
Are you trying to configure twinview or xinerama? I've had an insanely hard time getting sli (780i chipset) to work in Linux at all, I've pretty much written off sli altogether for my linux install. 

I tried twinview and it ended up being a gigantic waste of time.

As of now I've got one card running dual screens on my Linux machine, and the sli system just has windows and a handful of games installed.

---

### Post by Amannim on 2007-10-17
I have Dual 6800 GS's with 2xLCD's on a DFI Lan Party mobo that also supports the Soft-SLI switch. Here's what I've learned with Feisty 7.04:

1) The Nvidia glx driver has to be installed. On a clean install, if you enable the desktop-effects, this will be done for you before you can enter the desktop effects menu.

2) There are two options for Dual Head with Nvidia. If you have 1 monitor in each GPU, your forced to use Xinerama in Linux, where as Windows will perform the DualView as expected. Unfortunately Beryl/Compiz does NOT support Xinerama and will segfault upon attempting to load. Supposedly people have made it work, but I haven't found 'how' they did it. I'm looking for a stable platform so I wasn't about to go exploring, if I ever get a 2nd box here with SLI, I'll be more than happy to experiment. 

The second option is to run 1xDVI and 1xCRT off the primary video card, and then Nvidia will allow you to enable Twinview. Its a shame Twinview doesn't support 1 monitor in each GPU, they have to be in the same card as far as I can tell. With TwinView enabled, Beryl/Compiz DOES work, and thats the setup I'm using right now. Unfortunately, Yes, it does seem our 2nd GPU is gone to waste. 

[http://forlong.blogage.de/article/2007/8/26/The-best-way-to-install-Compiz-Fusion-on-Ubuntu-Feisty]("http://forlong.blogage.de/article/2007/8/26/The-best-way-to-install-Compiz-Fusion-on-Ubuntu-Feisty")

Thats the guide I followed to setup Compiz. Worked like a charm. If you have problems with borders with emerald or can't run terminal (white screen), add the Composite section and the other section to your screen and then Emerald will work fine.

I'm still torn over what I want to do. On the one hand I get dual monitors /w sweet sweet Compiz in Linux, and Windows I can do DualView, on the other hand, I feel like I have a video card that is just collecting dust. To be honest though, when I ran benchmarks for SLI mode, I saw a very minor difference in performance, I think 3-5% at best using 3D Winmark 2001 from MadOnion.com. Playing around with the current setup the past few days, the display refresh feels faster. 

When I feel brave I'll run some benchmarks again, in the mean time, I'm off to setup Wine and all my other apps/utils.

Oh! I almost forgot, if you run 1 monitor per GPU, if you set them up independent, you can use Compiz too, you just cant trade windows easily between each monitor, which was not what I was looking for. Though it was kind of fun having 2 cubes to spin around.

---

### Post by Agent Stone on 2007-10-17
Thanks Amannim,

You hardware setup seems near identical to mine, so many thanks for your helpful post.

I want one cube spanned over two screens ideally, so I can move windows from screen to screen, and spin the cube, etc. Similar to what you wanted to achieve. 

I have no real problem leaving one graphics card unused when running linux. The second card is more for windows gaming performance when running multiply Eve Clients you see.

I think what I will do is wait one more day for the release of Ubuntu 7.1 and then try again. I have purchased a DVI to VGA Adapter, so what I plan on doing is moving the monitor so they both run of the same graphics card, and with any luck, I can get Compiz up and running, spanned over two screens.

So something like...

1) Move second monitor over to DVI slot of first graphics card using VGA/DVI Adapter.
2) Install clean version of Ubuntu
3) Enable Nvidia Restricted Drivers
4) Enable Twinview
5) Add Compiz, and Emerald packages
6) Enjoy one large cube over two screens

Hopefully it will all work ok. I am still quite new to this, so I expect I will break things a few times.

> **Amannim said:**
> If you have problems with borders with emerald or can't run terminal (white screen), add the Composite section and the other section to your screen and then Emerald will work fine.
I did not understand this part of your post though? What is Composite section and Other Section and how do I add them to my screen? I am noob, and have not heard that terminology before.

---

### Post by Amannim on 2007-10-17
Sorry about that, when I remembered that statement I was about to go AFK.

In the /etc/X11/xorg.conf after you've setup everything, you'll probably have to add:


#Add the following option to your screen
Section "Screen"
...
    Option         "AddARGBGLXVisuals" "True"
EndSection

#Add the following section to the end of xorg.conf
Section "Extensions"
    Option         "Composite" "true"
EndSection

Last night I got Wine running and World of Warcraft, and its so much fun spinning the cube with WoW running lol. Took a stab at Ventrilo and got sound input/output working, but I cannot connect to any servers. No matter, I host the Ventrilo server on another Linux box so I'm just gonna make everyone go back to Teamspeak. lol!

<3 Ubuntu

---

