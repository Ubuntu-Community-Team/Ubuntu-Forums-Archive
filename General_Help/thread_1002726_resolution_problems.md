---
title: "resolution problems"
date: 2008-12-05
forum: General Help
---

### Post by ekolimits on 2008-12-05
ok i have changed my resolution of the desktop and it went blank on me and wont change... also i cant change it back because i cant see what i am doing... and now every time i start it it goes blank... anyone know what i can do?

---

### Post by Grolsche on 2008-12-05
I am only a fairly new user myself. But have you tried starting in recovery mode?

---

### Post by ekolimits on 2008-12-05
i have, and then i asks me how i want to boot in and i dont really know what to say so i chose the first option.. normal.. and my screen goes blank once ubuntu uses my selected resolution which is not supported by my monitor... its awkward that ubuntu does not have a windows like option as to when you press nothing for at least 20 seconds it will return to your last good resolution setting.... im really stuck here and i dont want to reinstall...
thanx for trying though... i may be wrong but maybe im not using the recovery the right way.

---

### Post by eternalnewbee on 2008-12-05
I don't have a solution for you, ekolimits, but trying to help.
Be patient. Your problem should be solvable.
> its awkward that ubuntu does not have a windows like option as to when you press nothing for at least 20 seconds it will return to your last good resolution setting.... im really stuck here and i dont want to reinstall...
It's not awkward. This is another world (hope you understand the metaphor).
Don't think about reinstalling. 99.9% sure.

---

### Post by overdrank on 2008-12-05
> **ekolimits said:**
> i have, and then i asks me how i want to boot in and i dont really know what to say so i chose the first option.. normal.. and my screen goes blank once ubuntu uses my selected resolution which is not supported by my monitor... its awkward that ubuntu does not have a windows like option as to when you press nothing for at least 20 seconds it will return to your last good resolution setting.... im really stuck here and i dont want to reinstall...
thanx for trying though... i may be wrong but maybe im not using the recovery the right way.

Hi and if you are booting recovery mode then try the xfix option, then boot normally. Hopefully this will correct the graphics issue.

---

### Post by ekolimits on 2008-12-05
ok tryed recovery and xfix option... it said it was overwriting but when i started normally in a few seconds i got the blank screen again. once linux addressed my resolution settings. aw man... ima try other stuff... did this happen to anyone else in the past?

---

### Post by ekolimits on 2008-12-05
hmm... i looked through my recovery options and root can maybe help... could i configure my resolution through a comand in root mode?

---

### Post by overdrank on 2008-12-05
> **ekolimits said:**
> hmm... i looked through my recovery options and root can maybe help... could i configure my resolution through a comand in root mode?

Xfix should have done this, you can try and reconfigure your xorg from a shell ```
sudo dpkg-reconfigure -phigh xserver-xorg
``` what is the model of the graphics card and what resolution are you using?

---

### Post by ekolimits on 2008-12-05
ok thank you for everything so far, its really getting somewhere.
i tryed your code in the shell and all it seemed to do is exactly what xfix atempted to do... how bout if i try to boot up ubuntu with my disc in the disc mode... wouldnt that boot properly in default settings since its burnt that way and no changes can be made to a disc... and then maybe access the configuration file where resolution info is stored and change it? If yes then where will i be able to find this conf file on my linux partition... since im also running XP... thats how come we are talking right now LOL

ok my graphics card is NVIDIA RIVA TNT2 Model64 Pro... its old...

---

### Post by kuhlbeans on 2008-12-05
Can you give us a little more information about what exactly happens?  You startup, the BIOS shows, then do you even get the Ubuntu loading progress bar?  Or does it get past the bootup sequence to where the login screen would normally show up?  

One thing you can do, once Ubuntu begins trying to startup, is hit ALT+F2 to enter verbose mode.  This should go back to the traditional text boot where you can see each item that is loaded.  This may help identify what is failing.  

If bootup is successful this won't help because it will say "starting gdm" or something similar (which is the login manager/screen) and then your screen will go black.  This probably means there is a problem with your X setup.  When the screen goes black you can try ctrl+alt+delete to kill X and hopefully take you to a command prompt.  Alternatively you can hit alt+F2 (or F3, F4, etc) to get to go to one of the virtual consoles where it should ask you to log in.  Once here you'll want to go to /etc/X11 directory and remember all the following commands must be done with sudo.  There should be a file here called xorg.conf, which is the X configuration file.  You may have some backups in the directory of the form xorg.conf.#.  You can try replacing your existing xorg.conf with these one by one to see if any of them work (using the mv or cp commands).  To see if it works just type startx at a command line to fire up X, when it starts it will read whatever is in xorg.conf.  If you find one that works great, make a backup of it in your home directory so if this ever happens again you can easily cp it from home into /etc/X11.  If one doesn't work you'll have to use an X configuration generator or create one by hand.  There are plenty of resources on the web to help, just ask Google.  Arch Linux has a very good resource on X here:  [http://wiki.archlinux.org/index.php/Xorg](http://wiki.archlinux.org/index.php/Xorg)

I'm not sure about ATI, but since you have an NVIDIA card I'd highly recommend installing their proprietary drivers (as opposed to the default open source ones) and use their control panel to adjust resolution and other settings, it has always worked well for me.

---

### Post by ekolimits on 2008-12-05
ok im on ubuntu disk version now... and the screen goes blank not black... unsupported imput because i accidentally chose a resolution my monitor wont do... or graphics cards as well...now i hear ubuntu startup right before the sound plays... the screen goes out due to leading my resolution setting. thats all its a minor problem that should be solved easily... i figure now that im logged into ubuntu linux via the cd... with all graphics good... just resolution is small and that is why i wanted to change it in the first place.. lol ... but if someone can direct me to how i can access the configuration in order to change my resolution on my hardisk installed version of ubuntu

---

### Post by fowie on 2008-12-05
If you're using the liveCD and the resolution is ok, just copy /etc/X11/xorg.conf and paste it over the /etc/X11/xorg.conf file on your hard disk installed version (either mount your hard drive while running the liveCD and do it, or just paste it somewhere (like into an email) and then boot up on the hard drive, hit ctrl-alt-f1 to get a tty prompt, and copy it in by hand)

---

### Post by ekolimits on 2008-12-05
Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

thats in my xorg.conf file... what does it mean?

---

### Post by GMScribe on 2008-12-05
I'm having the same issue, I don't think that the issue is with the xorg.conf file, I would like to know where these "Configured Monitor" values etc are stored. The resolution changing program seems to be changing something elsewhere which is messing up the settings regardless of which manual resolution you set.

---

### Post by ekolimits on 2008-12-05
i have come to the same conclusion as you... the resolution conf is somewhere else... xorg.conf just points to it... anyone know where we ccan find the propper conf file?

---

### Post by GMScribe on 2008-12-05
Yeah,

I have manually configured everything in the .conf based on my tv's specs, no change at all, I wish linux has better documentation or at least a better gui tool. The ubuntu screen reso tool is rather basic and broken.

---

### Post by ekolimits on 2008-12-05
so can anyone help us out here or am i just going to uninstall it and reinstall...

---

### Post by ekolimits on 2008-12-05
no one knows? :(

---

### Post by GMScribe on 2008-12-06
I guess not =S This is frustrating, fedora 10 install doesn't like my south bridge so I can't install that in ubuntu's place either.

---

### Post by kuhlbeans on 2008-12-07
The resolution of your monitor *is* in your xorg.conf, or at least it should be.  If it is not there that's the problem I would guess.  The way the conf file is organized and sets things up can be a bit confusing.  I've copied the relevant parts of mine below (there's other stuff for input devices and such in the file).

```

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "CMO"
    HorizSync       30.0 - 75.0
    VertRefresh     60.0
    ModeLine       "1440x900@60" 106.47 1440 1520 1672 1904 900 901 904 932 -hsync +vsync
    ModeLine       "1280x800@60" 83.5 1280 1344 1480 1680 800 801 804 828 -hsync +vsync
    ModeLine       "1280x720@60" 74.5 1280 1336 1472 1664 720 721 724 746 -hsync +vsync
    ModeLine       "1280x768@60" 80.1 1280 1344 1480 1680 768 769 772 795 -hsync +vsync
    ModeLine       "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 9500M GS"
    Option         "NoLogo" "true"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "nvidia-auto-select +0+0; 1440x900@60 +0+0; 1280x800@60 +0+0; 1280x720@60 +0+0; 1280x768@60 +0+0; 800x600@60 +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection
```

As you can see the Screen is composed of your monitor and videocard.  There's some extra stuff for my screen from nvidia's twinview (the twinview and metamodes options) that you may not have and/or need.  The resolutions are set up in the ModeLines for the monitor.  Also note that the driver for the videocard is "nvidia", which requires the binary drivers.  I believe the open-source included one is "nv", or if that still barfs you can try "vesa" as a last resort... or whatever is in the xorg.conf for the liveCD that works.

---

