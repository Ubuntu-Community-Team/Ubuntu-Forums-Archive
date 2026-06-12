---
title: "New to Ubuntu, Help with VLC and fullscreen games."
date: 2009-05-02
forum: General Help
---

### Post by rofflesupplecake on 2009-05-02
Hi, I just tried out ubuntu with 9.04, it is running quite well with the exception of 2 problems: When I run VLC I get 2 separate things: the player itself and the manager, and the video output which is separate. This problem never occurred to me on windows with the exception if its full screen and loses attention to another program. How can you fix this? My other problem is when I try running fullscreen games such as Warsow/Nexuiz/Frets of Fire, the computer starts lagging really hard and its basically unplayable at the menu level, how can you fix this, and what causes this?

Thanks :)

---

### Post by Woody1987 on 2009-05-02
not sure about vlc, but for the fullscreen game issue, what video card do you have?

---

### Post by rofflesupplecake on 2009-05-02
> **Woody1987 said:**
> not sure about vlc, but for the fullscreen game issue, what video card do you have?

ATI Radeon 2400 HD
I also forgot to mention, Amarok is not working at all for me, I cant add music files to my collection or play any mp3 files, how can you fix that?

Thanks.

---

### Post by Woody1987 on 2009-05-02
Are using the proprietary driver (System->Administration->Hardware Drivers) or using the opensource driver (this will be the default driver that comes with ubuntu). If its the opensource driver then this will explain the problem your having as they have very poor 3d performance on ati cards for the radeon HDxxxx generations. I suggest you install the proprietary one to give you the performance. It would be a good idea after you install the drivers that you run sudo aticonfig --initial -f in the terminal.

Im not sure about amarok, you could try installing the codecs this should allow you to play most things. open up add/remove programs and search for ubuntu restricted extras.

---

### Post by 3Miro on 2009-05-02
The thing with VCL is not a bug, but a feature. I have seen in many places and I don't know if it can be "fixed". Try looking around the menus and/or searching some sort of manual on google.

As for the game, first it will not run without the proprietary driver. Second, are you using wine? The game might not be supported.

---

### Post by rofflesupplecake on 2009-05-02
I tried to install the ATI driver and I get this following error when I click activate

SystemError: Failed to lock /var/cache/apt/archives/lock

I am not using WINE, I am using open source games just to try them out.

---

### Post by Woody1987 on 2009-05-02
Your getting that error because another program is running which is trying to update/install/uninstall another program. If you have synaptic or add/remove programs open, then close them and try to install the driver again. The reason for this is so that you don't end up installing two things at once which can cause problems with things like dependencies.

---

### Post by mb_webguy on 2009-05-02
> **3Miro said:**
> The thing with VCL is not a bug, but a feature. I have seen in many places and I don't know if it can be "fixed". Try looking around the menus and/or searching some sort of manual on google.

As for the game, first it will not run without the proprietary driver. Second, are you using wine? The game might not be supported.

Actually, it's both a feature and a bug.  VLC can display in a separate window or embedded in the interface.  This is a feature -- you can set it to whichever you prefer.

However, the version of VLC in the Jaunty repositories has a bug that prevents you from embedding the video in the interface, and another that prevents controls from being displayed for a video in fullscreen.  [This PPA]("https://launchpad.net/~medigeek/+archive/ppa") provides a fixed version of VLC.

---

### Post by rdmike on 2009-05-03
You may need to ditch pulseaudio to get Amarok to work properly; that's what I had to do.

---

