---
title: "GeForce 9600 drivers for linux?"
date: 2008-02-23
forum: Gaming &amp; Leisure
---

### Post by A4006 on 2008-02-23
I dual boot Vista Ultimate and Ubuntu, using Vista for gaming, and I'm thinking about buying one of the new bleeding-edge Nvidia GeForce 9600 cards as an upgrade from my older 8500 GT, since I can't get the performance I want out of games like Crysis with my current card.  I've previously had issues with drivers for my current card in Ubuntu, and I'm hesitant to buy a new one if it won't work, or won't be fully compatible with Ubuntu.  So, are there Linux drivers out there for the 9000 series, and are they fairly easy to get/install (like with Envy)?  I've looked around a bit but haven't seen anything, thanks is advance for any help.

---

### Post by Sockerdrickan on 2008-02-23
There will probably be support soon by nVidia and open source 2D support a little further away.

---

### Post by Crafty Kisses on 2008-02-23
There will be soon, don't worry.

---

### Post by gazzanova on 2008-02-27
> **A4006 said:**
> I dual boot Vista Ultimate and Ubuntu, using Vista for gaming, and I'm thinking about buying one of the new bleeding-edge Nvidia GeForce 9600 cards as an upgrade from my older 8500 GT, since I can't get the performance I want out of games like Crysis with my current card.  I've previously had issues with drivers for my current card in Ubuntu, and I'm hesitant to buy a new one if it won't work, or won't be fully compatible with Ubuntu.  So, are there Linux drivers out there for the 9000 series, and are they fairly easy to get/install (like with Envy)?  I've looked around a bit but haven't seen anything, thanks is advance for any help.

have you tried the version 17.05 linux drivers? 

[ftp://download.nvidia.com/XFree86/Linux-x86/171.05/](ftp://download.nvidia.com/XFree86/Linux-x86/171.05/)

apparently they work with the 9600GT

[http://www.nvnews.net/vbulletin/showthread.php?p=1573493#post1573493](http://www.nvnews.net/vbulletin/showthread.php?p=1573493#post1573493)

---

### Post by A4006 on 2008-02-27
I can't really try it since I don't have the card.. but thanks for the links.

---

### Post by cookieofdoom on 2008-02-27
When I got the 8800GT I had to wait about a month for drivers. I got it almost as soon as it came out (which was exactly when my old video card died, kinda worked out nice). I altered my xorg.conf to use vesa as the driver (nv didn't work), and used openbox over compiz-fusion for a few weeks.

If you wait a couple of weeks prices will come down and you'll be sure of good driver support. If my old card hadn't died, I'd have probably done that. Either way, Nvidia will definitely support the card soon (if they don't already).

---

### Post by A4006 on 2008-02-27
Yeah, I'm gonna wait until the 9800's come out at least, I might even get a 9800.  This is kinda off topic, but would I be able to get better performance out of a 8800 similarly priced to a 9600?  I've looked around a little, but there's not a whole lot of info out about performance. Thanks.

---

### Post by keltren on 2008-02-28
> **A4006 said:**
> but would I be able to get better performance out of a 8800 similarly priced to a 9600?  I've looked around a little, but there's not a whole lot of info out about performance. Thanks.
For the same money you can get either a cheap 8800gt or an expensive 9600gt - The reviews I've seen list a 5-10% performance difference in favour of the 8800gt. But if you compare a cheap 8800 with an expensive 9600 the difference might even be non-existent.

I've gone for a 9600gt myself (Evga) as the 9er cards run a lot cooler and probably also quieter than the 8800gt - I like my system as quiet as possible so this was the selling point for me. Noise is similar to a Zalman VF900 cooler at minimum setting i.e. probably as close to inaudible as you'll get with a fan :-)

---

### Post by A4006 on 2008-02-28
Ok, thanks.

---

### Post by revpfil on 2008-02-28
yes, the the 171.05 drivers from Nvidia work with the 9600gt on ubuntu.
Not the best performance I've ever seen (some stutters and lines with compiz), but they definitely work well enough to get that far, so it's not bad :)
That link again is:
[ftp://download.nvidia.com/XFree86/Linux-x86/171.05/](ftp://download.nvidia.com/XFree86/Linux-x86/171.05/)

---

### Post by cookieofdoom on 2008-02-28
> **revpfil said:**
> yes, the the 171.05 drivers from Nvidia work with the 9600gt on ubuntu.
Not the best performance I've ever seen (some stutters and lines with compiz), but they definitely work well enough to get that far, so it's not bad :)
That link again is:
[ftp://download.nvidia.com/XFree86/Linux-x86/171.05/](ftp://download.nvidia.com/XFree86/Linux-x86/171.05/)

Those are beta drivers, right?

---

### Post by keltren on 2008-02-29
not exactly beta...the 171.05 driver is basically meant for nvidia tesla systems, the 9600 isn't officially supported by that driver. So the "bugs" and flakey behaviour may simply be due to the fact that it's probably optimized for a completely different system ;-)

From what I've seen this driver really doesn't like compiz - I've had compiz freeze up for 10-15s at times and segfault as well. 
Other than that it seems to work quite well though - did a 4 hour kara run (World of Warcraft) yesterday evening without a single hitch, all settings maxed at 1680x1050 and framerate rarely dipped below 60fps. 
That's with an e8400 cpu btw - and even with that wow still seems to be cpu limited under wine, gpu didn't go above 57c so the card wasn't under full load - did some load tests earlier under windows and under full load it hits around 64c.

---

### Post by jseiser on 2008-02-29
im glad they are supported, I just ordered this morning, 9600GT, amd Quad Core, 4GB's ram, So i planon getting some gaming in.  i got a whole system except monitor and HD since i have those, for 750, prices re so much better for PC parts then in the past, great time to be a nerd./

---

### Post by rev_b on 2008-03-03
The latest official 169.12 drivers appears to work fine with 9600GT :) 
[http://us.download.nvidia.com/XFree86/Linux-x86/169.12/NVIDIA-Linux-x86-169.12-pkg1.run](http://us.download.nvidia.com/XFree86/Linux-x86/169.12/NVIDIA-Linux-x86-169.12-pkg1.run)

As reported in Nvnews

Not really official support, but as long as it works...

---

### Post by keltren on 2008-03-04
Yeah so far no problems (and in case you're wondering that's me posting as well on the nvnews forum (kel) ;-) ).

I noted some performance issues, but as of yet I'm not sure if that's driver related or due to the particular app (i.e. audiosurf via wine, etqw). Other apps seem to run nice and fast though (i.e. WoW, Quake4). 
etqw performance has me scratching my head a bit as that's a native app and I've played Gears of War on Vista over the weekend at 1680x1050 with *everything* maxed and it was running damn smooth.

---

### Post by Hire on 2008-03-04
Do you use Compiz? Or metacity?

Try to open ONLY etqw and close any other app as Compiz, Tracker, Firefox, Wine etc..

However it is very strange because the performance between Linux and Windows is the same... so, for me, it is because you have too many app open together.

---

### Post by keltren on 2008-03-04
Yeah I have compiz running, with most apps that doesn't cause any performance issues though for me, but I'll give it a try.
Might also download the windows client and see how it fares there - settings so far were all maxed at 1680x1050, wouldv'e thought that should run at 40+ fps with this card (and a e8400 cpu), yet framerate seems more in the 20-30fps bracket.

---

### Post by keltren on 2008-03-04
Found the problem - looks like the 169.12 drivers aren't really good for the gf9600gt after all, 1680x1050 all maxed (+16 AF) I got around 15-25fps. Switching to the 171.05 drivers the framerate seems to pretty much be stuck at 60fps (vsync on) - now that's more like it :D

---

### Post by Spacebaboon on 2008-03-07
they don't work for me, not even the today-new 171.06 driver with 9600gt support.
[http://www.nvnews.net/vbulletin/showthread.php?t=109422](http://www.nvnews.net/vbulletin/showthread.php?t=109422)

I've followed the installation instructions, it's built the drivers, recompiled the kernel, and let it reconfigure my xorg.conf, but when I startx, it fails, saying it has found screens, but none suitable, and in the log it just says 
(EE) NVIDIA(0): Failed to initialize the NVIDIA graphics device!
(EE) Screen(s) found, but none have a usable configuration. 

I'm running Kubuntu Gutsy, Pentium Dual Core E2160, Sparkle 9600gt Silent.

---

### Post by keltren on 2008-03-08
Just installed the 171.06 drivers here and they run perfectly well - even the compiz problems I had with 171.05 seem to be gone from what I can tell so far.

> (EE) NVIDIA(0): Failed to initialize the NVIDIA graphics device!
Seems to indicate that somethings gone wrong with your install...either it's loading the wrong kernel driver or can't find the correct one from what I remember...maybe try to reboot and see if it works then? Allthough the nvidia install app is supposed to unload and delete the old kernel driver when it does the install...still worth a try and if it still doesn't work try another reinstall.

---

### Post by Spacebaboon on 2008-03-08
thanks for your reply :) I'll give it another go. I'm not sure if I'm doing it in the correct environment. I can't do a normal boot, as it will try to start the X server, which looks like it's continuing to load, but the screen is blank. so I'm starting in recovery mode from Grub, then doing 'init 3' to restart me normally but without starting X. and then downloading the new driver with wget, and running it with sudo and following the ncurses screens.

It sounds like there's a new nv driver, that might be a good starting point, so at least I can get something up. it's very slow to have to boot into windows to read any web pages, after the linux installs fail!

---

### Post by Chaoticwhizz on 2008-03-09
Ive tried the latest beta driver for Nvidia 9600 and cant get it work. It installs fine but after I reboot I just get a blank screen when it would normally load the X server. When this happens, my monitor flashes a "no signal" message and then goes into low power mode. I can dual-boot into Windows XP fine as well as boot into Kubuntu using the "vesa" driver. I have uninstalled and reinstalled the driver several limes. Even tried removing anytning that mentions mvidia from adept (Kubuntu package manager) I cant find anything out of place in the xorg.0.log files since it only lists the like last time I used VESA.  The "NV" driver does not work at all

---

### Post by keltren on 2008-03-09
If your xorg.conf mentions the "nv" driver you're using the opensource nvidia driver, which is very unlikely to support the 9600. The closed source driver is called "nvidia" so the graphic card section in your xorg.conf needs to look something like this:

```
Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 9600 GT"
EndSection
```

---

### Post by Spacebaboon on 2008-03-09
the nv driver has been updated - 2nd paragraph here
[http://www.phoronix.com/scan.php?page=news_item&px=NjM3OQ](http://www.phoronix.com/scan.php?page=news_item&px=NjM3OQ)

I haven't had time to try this yet.

---

### Post by Chaoticwhizz on 2008-03-09
> **keltren said:**
> If your xorg.conf mentions the "nv" driver you're using the opensource nvidia driver, which is very unlikely to support the 9600. The closed source driver is called "nvidia" so the graphic card section in your xorg.conf needs to look something like this:

```
Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 9600 GT"
EndSection
```

I was running the Nvidia driver. I meant to say that I had also tried the nv driver and couldnt get that to work either. I shouldnt post when I am frustrated and half-asleep

Since my last post, I ran "sudo nvidia-xconfig" which made several changes to my xorg.conf file. but after rebooting the monitor loses signal and shuts down just like before. in case it helps, my monitor is a brand new 19 inch Hanns-G JW199D. it is also widescreen. The monitor works perfectly in WinXP 

here is my xorg.conf after running the above nvidia-xconfig
```

# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder3)  Wed Feb 20 17:07:14 PST 2008

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
    RgbPath         "/usr/X11R6/lib/X11/rgb"
EndSection

Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
    Load           "glx"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Unknown"
    HorizSync       30.0 - 110.0
    VertRefresh     50.0 - 150.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```

---

### Post by Spacebaboon on 2008-03-11
I'm still trying to get mine to work. I ran the nv-bug-report.sh, the full output is too big to paste in here, but I've found what I think is the problem.

NVRM: loading NVIDIA UNIX x86 Kernel Module  171.06  Wed Feb 20 16:40:08 PST 2008
NVRM: loading NVIDIA UNIX x86 Kernel Module  100.14.19  Wed Sep 12 14:12:24 PDT 2007
NVRM: API mismatch: the client has the version 171.06, but
NVRM: this kernel module has the version 100.14.19.  Please
NVRM: make sure that this kernel module and all NVIDIA driver
NVRM: components have the same version.

that's quite a difference! I think it's because when I set the system up originally, I turned on the restricted driver for NVidia in the settings manager.

as I'm restricted to a command-line interface until I get X working, how would I remedy this?

---

### Post by Chaoticwhizz on 2008-03-11
> **Spacebaboon said:**
> I'm still trying to get mine to work. I ran the nv-bug-report.sh, the full output is too big to paste in here, but I've found what I think is the problem.

NVRM: loading NVIDIA UNIX x86 Kernel Module  171.06  Wed Feb 20 16:40:08 PST 2008
NVRM: loading NVIDIA UNIX x86 Kernel Module  100.14.19  Wed Sep 12 14:12:24 PDT 2007
NVRM: API mismatch: the client has the version 171.06, but
NVRM: this kernel module has the version 100.14.19.  Please
NVRM: make sure that this kernel module and all NVIDIA driver
NVRM: components have the same version.

that's quite a difference! I think it's because when I set the system up originally, I turned on the restricted driver for NVidia in the settings manager.

as I'm restricted to a command-line interface until I get X working, how would I remedy this?

Can you get it to work using the vesa driver? vesa is a basic 2D only driver to use when no other video driver works.Try this

```
sudo nano /etc/X11/xorg.conf
```

nano is a basic easy-to-use text editor that works from the command line. When the file opens scroll until you see driver "nvidia" and change it to "vesa" then save the file, exit nano and reboot. If the above line doesnt swork then nano may not be installed. You can just install through apt-get 
```
sudo apt-get install nano
```

Hope this helps.

---

### Post by Spacebaboon on 2008-03-12
I'm more a vi man, actually.

but that helped, the vesa driver let me get X going well enough, and I was able to disable the Nvidia restricted driver, which was the problem.

with that gone, and with a reinstall of the NVidia driver, everything is running perfectly.

thanks for all the help :)

---

### Post by jseiser on 2008-03-13
this card works fine with arch 32, but with ubuntu hardy 64, and arch 64, X crashes with a screens error, the same xorg works fine with 32bit arch.  So i imagine its a driver issue?  he, i feel wrong running this 9600 and a phenom with evilwm. lol.

---

### Post by brainkilla on 2008-03-13
> **Spacebaboon said:**
> they don't work for me, not even the today-new 171.06 driver with 9600gt support.
[http://www.nvnews.net/vbulletin/showthread.php?t=109422](http://www.nvnews.net/vbulletin/showthread.php?t=109422)

I've followed the installation instructions, it's built the drivers, recompiled the kernel, and let it reconfigure my xorg.conf, but when I startx, it fails, saying it has found screens, but none suitable, and in the log it just says 
(EE) NVIDIA(0): Failed to initialize the NVIDIA graphics device!
(EE) Screen(s) found, but none have a usable configuration. 

I'm running Kubuntu Gutsy, Pentium Dual Core E2160, Sparkle 9600gt Silent.

Are you running the stock kernel, or have you compiled a vanilla one? Anything newer than 2.6.23 will cause you serious troubles, due to some miniscule yet significant changes in the kernel tree... I had to revert to 2.6.23 thanks to the fact the card could not be initialised with 2.6.24.2, which I was running at the moment of purchase (that is, yesterday ;) ).  It took me an afternoon to figure out what was the exact nature of my problem, but when I did everything automagically worked... oh, yes, running XFX 9600GT over here :guitar:

---

### Post by sonnet on 2008-03-15
Hi guys I needs your help!
I was able to install the drivers 171.06 for the card 9600gt.
The only problem is that if I reboot then I will be back to the generic drive.
It happened before, so now, I reinstalled everything and I have the drivers working again,but how can I make sure that when I reboot the drivers will still be working?

---

### Post by Neo0351 on 2008-03-15
> **sonnet said:**
> Hi guys I needs your help!
I was able to install the drivers 171.06 for the card 9600gt.
The only problem is that if I reboot then I will be back to the generic drive.
It happened before, so now, I reinstalled everything and I have the drivers working again,but how can I make sure that when I reboot the drivers will still be working?

Sounds like the same problem I had when I first install 9600gt.  After many hours I figured out I had to disable the nv drivers.

```
sudo gedit /etc/default/linux-restricted-modules-common 
```
 
At the bottom, it should look something like this

```
DISABLED_MODULES="nv"
```

---

### Post by Chaoticwhizz on 2008-03-20
Im still having problems. Installing the driver happens without incident but after I reboot it only goes to cmd line. After logging in and running startx I get the included screenshot. Also, when I try to load the VESA driver I get to the Kubuntu login screen but after that it looks like the scanlines are out of sync. Please help. This past couple weeks have reminded me how much I dislike using Windows for everything except gaming

My only other options are waiting until the stable Nvidia driver comes out or possibly trying out Heron when it is released next month.

---

### Post by Melcar on 2008-03-20
There is going to be a review of the card and the latest drivers on Phoronix.

---

### Post by Neo0351 on 2008-03-21
> **Chaoticwhizz said:**
> Im still having problems. Installing the driver happens without incident but after I reboot it only goes to cmd line. After logging in and running startx I get the included screenshot. Also, when I try to load the VESA driver I get to the Kubuntu login screen but after that it looks like the scanlines are out of sync. Please help. This past couple weeks have reminded me how much I dislike using Windows for everything except gaming

My only other options are waiting until the stable Nvidia driver comes out or possibly trying out Heron when it is released next month.

Exactly what driver are you trying to use?

---

### Post by Chaoticwhizz on 2008-03-21
> **Neo0351 said:**
> Exactly what driver are you trying to use?

Im using the 171.06 beta drivers which suport my Geforce 9600GT card. I have at least gotten it to work in VESA again. I had to change the color depth from 24 to 16.

---

### Post by Neo0351 on 2008-03-21
Ok, here's how I my 9600GT working with the 171.06 drivers.
First make sure you have all these replacing 2.6.22 with your kernel 

```
uname -r
sudo apt-get install linux-headers-'uname -r'
sudo apt-get install linux-restricted-modules-'uname -r'
sudo apt-get install linux-source-2.6.24 build-essential
```

Then ctrl+alt+F1 and log in as root
```
killall gdm
chmod a+x /location/to/driver
sh /location/to/driver
```

After installed

```
nano /etc/default/linux-restricted-modules-common
```

Last line should look like

```
DISABLED_MODULES="nv"
```

Hope this helps

---

### Post by Alpinist on 2008-03-22
Thought I'd post what I went through with this card.

When I first installed the card I booted to a black screen.  Just changing xorg.config to a vesa driver didn't work. But after I ran sudo dpkg-reconfigure xserver-xorg I was able to get it to work.  (As described in thread  [http://ubuntuforums.org/showthread.php?t=690760](http://ubuntuforums.org/showthread.php?t=690760))

Then I followed the instructions by Atomp in page 2 of this thread:
[http://ubuntuforums.org/showthread.php?t=717978&highlight=9600GT&page=2](http://ubuntuforums.org/showthread.php?t=717978&highlight=9600GT&page=2)

Unfortunately when I got to the command sudo /etc/init.d/gdm stop (actually, I'm on kubuntu so it is sudo /etc/init.d/kdm stop) my screen went completely blank.  Could not regain control of the screen again after stopping kde.

Also the package name on that thread seems incorrect.  I am using NVIDIA-Linux-x86_64-171.06-pkg2.run.

Finally I booted to safe mode.  Tried to run the package install and it said I needed to be at runlevel 3.  Ran initlevel 3 and it booted to kde.  Did ctr-alt-F1 and tried to run install and it complained kde was running. Stopped kde again and this time amazingly I sill had a command prompt and not a blank screen. Then was able to perform the install.

A lot of work but is now working very well. Around 15000 fps on glxgears, that is over 10 times better than my onboard 6150.

During this ordeal I did boot into windows (something I haven't done in months) and the driver on CD installed very easily with no problem.  Hopefully Hardy will handle the card better than Gutsy.

---

### Post by jamesnewell on 2008-04-01
Thanks Neo0351, I finally got the drivers working, I had missed disabling nv.

I had Compiz working straight after i got the drivers working but it no longer works and am not sure as to what has caused it.

Can anyone tell me how to fix this?

```
SKIP_CHECKS=yes compiz 
```

```

Checking for Xgl: not present. 
Detected PCI ID for VGA: 03:00.0 0300: 10de:0622 (rev a1) (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: not present. 
SKIP_CHECKS is yes, so continuing despite problems.
Checking for nVidia: present. 
Checking for FBConfig: Error: glXCreateContext failed
not present. 
SKIP_CHECKS is yes, so continuing despite problems.
Checking for Xgl: not present. 
/usr/bin/compiz.real (core) - Fatal: glXCreateContext failed
/usr/bin/compiz.real (core) - Error: Failed to manage screen: 0
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :0.0
```

Thanks,

James

---

### Post by Neo0351 on 2008-04-02
Post your xorg.conf please.

---

### Post by jamesnewell on 2008-04-03
xorg.conf

```
# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 1.0  (buildmeister@builder26)  Wed Feb 20 09:25:39 PST 2008

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
    RgbPath         "/usr/X11R6/lib/X11/rgb"
EndSection

Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
    Load           "glx"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "ViewSonic VX2235wm"
    HorizSync       30.0 - 82.0
    VertRefresh     50.0 - 75.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 9600 GT"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "TwinViewXineramaInfoOrder" "DFP-0"
    Option         "metamodes" "DFP-0: 1680x1050 +0+0, DFP-1: nvidia-auto-select +1680+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```

---

### Post by Neo0351 on 2008-04-03
I'm not sure what your problem is, my guess would be maybe a package update broke it.  You might try reinstalling compiz.  i'm not using it right now because it doesn't play nice with my video card while watching movies.  It draws my background on the widescreen black line things.

---

### Post by jamesnewell on 2008-04-03
Tried uninstalling compiz with

```
 sudo apt-get remove --purge compiz*
```

and reinstalling with

```
sudo apt-get install  compiz compizconfig-settings-manager
```

Restarted and still got the same message as before. Guess I'll just have to wait for compiz.

Does anyone else have compiz working on this card?

Thanks.

---

### Post by jamesnewell on 2008-04-05
Seems to be working with the latest updates. Thanks Ubuntu!

---

### Post by Chaoticwhizz on 2008-04-07
> **Neo0351 said:**
> Ok, here's how I my 9600GT working with the 171.06 drivers.
First make sure you have all these replacing 2.6.22 with your kernel 

```
uname -r
sudo apt-get install linux-headers-'uname -r'
sudo apt-get install linux-restricted-modules-'uname -r'
sudo apt-get install linux-source-2.6.22 build-essential
```

Then ctrl+alt+F1 and log in as root
```
killall gdm
chmod a+x /location/to/driver
sh /location/to/driver
```

After installed

```
nano /etc/default/linux-restricted-modules-common
```

Last line should look like

```
DISABLED_MODULES="nv"
```

Hope this helps

I followed these instructions to the letter and still get a black screen with "No Signal" message on reboot. Both monitor and 9600GT card work fine on WinXP. Monitor is a 19 in widescreen Hanns-G JW199D. Here is my xorg.conf file
```

# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder3)  Wed Feb 20 17:07:14 PST 2008

# xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"

# Uncomment if you have a wacom tablet
#	InputDevice     "stylus"	"SendCoreEvents"
#	InputDevice     "cursor"	"SendCoreEvents"
#	InputDevice     "eraser"	"SendCoreEvents"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
EndSection

Section "Files"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "us"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ImPS/2"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
    Identifier     "stylus"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "stylus"
    Option         "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "eraser"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "eraser"
    Option         "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "cursor"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "cursor"
    Option         "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "Monitor"
    Identifier     "JW199D"
    HorizSync       30.0 - 71.0
    VertRefresh     50.0 - 75.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "nVidia Corporation NVIDIA Default Card"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "nVidia Corporation NVIDIA Default Card"
    Monitor        "JW199D"
    DefaultDepth    16
    Option         "UseFBDev" "false"
    Option         "glx"
    SubSection     "Display"
        Depth       24
        Modes      "1440x900"
    EndSubSection
EndSection

```

---

### Post by Neo0351 on 2008-04-08
im not an expert with the xorg.conf, so back it up and then try this.  make you "screen" section look like this
```
Section "Screen"
    Identifier     "Default Screen"
    Device         "nVidia Corporation G72 [GeForce 7300 LE]"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
        Modes      "nvidia-auto-select"
    EndSubSection
```

then add this section
```
Section "Module"
    Load           "glx"
EndSection
```

hope this works and for reference here mine
```
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder26)  Wed Feb 20 09:25:02 PST 2008

# xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"

# Uncomment if you have a wacom tablet
#	InputDevice     "stylus"	"SendCoreEvents"
#	InputDevice     "cursor"	"SendCoreEvents"
#	InputDevice     "eraser"	"SendCoreEvents"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
EndSection

Section "Files"
EndSection

Section "Module"
    Load           "glx"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "us"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ImPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
    Identifier     "stylus"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "stylus"
    Option         "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "eraser"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "eraser"
    Option         "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "cursor"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "cursor"
    Option         "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "Monitor"
    Identifier     "Generic Monitor"
    HorizSync       30.0 - 70.0
    VertRefresh     50.0 - 160.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "nVidia Corporation G72 [GeForce 7300 LE]"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "nVidia Corporation G72 [GeForce 7300 LE]"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
        Modes      "nvidia-auto-select"
    EndSubSection
EndSection

```

---

### Post by Mantrasong on 2008-04-14
Well, I did have it working quite nicely (worked on the first attempt, I was surprised) but the latest update (for Hardy Heron) seems to have broken it. I tried installing the newest drivers ([http://us.download.nvidia.com/XFree86/Linux-x86_64/173.08/NVIDIA-Linux-x86_64-173.08-pkg2.run](http://us.download.nvidia.com/XFree86/Linux-x86_64/173.08/NVIDIA-Linux-x86_64-173.08-pkg2.run)), but I'm still stuck at 640x480 resolution. 

I know its still in development, but any suggestions would be appreciated.

Xorg.conf:
```
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder62)  Wed Apr  2 08:22:13 PST 2008

# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by failsafeDexconf, using
# values from the debconf database and some overrides to use vesa mode.
#
# You should use dexconf or another such tool for creating a "real" xorg.conf
# For example:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen      0  "Default Screen" 0 0
    InputDevice    "Generic Keyboard" "CoreKeyboard"
    InputDevice    "Configured Mouse" "CorePointer"
EndSection

Section "Module"
    Load           "glx"
    Load           "v4l"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "us"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
EndSection

Section "Monitor"
    Identifier     "Configured Monitor"
    VendorName     "Plug 'n' Play"
    ModelName      "Plug 'n' Play"
    Gamma           1
    ModeLine       "640x480@60" 25.2 640 656 752 800 480 490 492 525 -hsync -vsync
EndSection

Section "Device"
    Identifier     "Configured Video Device"
    Driver         "nvidia"
    BoardName      "vesa"
    Screen          0
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Configured Video Device"
    Monitor        "Configured Monitor"
    DefaultDepth    24
    SubSection     "Display"
        Virtual     640 480
        Depth       24
        Modes      "640x480@60"
    EndSubSection
EndSection

```

---

### Post by Neo0351 on 2008-04-14
was the kernel updated in the latest updates?  if so, have you tried using the old kernel that worked?

---

### Post by Mantrasong on 2008-04-15
I'm pretty sure the Kernel was not updated, since the kernel number was the same from the last time I did the installation. I think something related to Xorg might have been updated, but I didn't look at the list too closely. Is there any way to go back and see what was updated?

---

### Post by astoroth88 on 2008-04-15
@ the question about the 8800 vs 9600 prices:   I purchased the 9600 GT superclocked edition for $180, which is $10 more than the 8800 GT on newegg.com.  The 9600GT superclocked ran a little hot running BF2 on highest settings, it ran the game copmletely fine @ 60 fps but after 4 hours it completely locked up and i had to shut down my pc manually.  I hear that the 8800GT doesn't have heating issues, the 9600GT is just slightly faster (100mhz more on gpu i think) and that's all i really noticed other than the name but i didn't bother going into extensive details with the descriptions, i just read the clocks and slot type.

One other thing though, how do i install these drivers, i'm newb to ubuntu. I click on the links and get the HTML code page.

---

### Post by Neo0351 on 2008-04-15
> **astoroth88 said:**
> @ the question about the 8800 vs 9600 prices:   I purchased the 9600 GT superclocked edition for $180, which is $10 more than the 8800 GT on newegg.com.  The 9600GT superclocked ran a little hot running BF2 on highest settings, it ran the game copmletely fine @ 60 fps but after 4 hours it completely locked up and i had to shut down my pc manually.  I hear that the 8800GT doesn't have heating issues, the 9600GT is just slightly faster (100mhz more on gpu i think) and that's all i really noticed other than the name but i didn't bother going into extensive details with the descriptions, i just read the clocks and slot type.

One other thing though, how do i install these drivers, i'm newb to ubuntu. I click on the links and get the HTML code page.



> **Neo0351 said:**
> Ok, here's how I my 9600GT working with the 171.06 drivers.
First make sure you have all these replacing 2.6.22 with your kernel 

```
uname -r
sudo apt-get install linux-headers-'uname -r'
sudo apt-get install linux-restricted-modules-'uname -r'
sudo apt-get install linux-source-2.6.22 build-essential
```

Then ctrl+alt+F1 and log in as root
```
killall gdm
chmod a+x /location/to/driver
sh /location/to/driver
```

After installed

```
nano /etc/default/linux-restricted-modules-common
```

Last line should look like

```
DISABLED_MODULES="nv"
```

Hope this helps

everything ive heard the 9600gt runs cooler than the 8800gt.  thats part of the reason i bought mine.  mine has never got above 45C.  could be your case cooling or the fact that yours is superclocked.

---

### Post by Mantrasong on 2008-04-15
Alright, well I lied, and the kernel was updated, but it turned out that all I had to do was update the auto-generated xorg-config.

I changed this 

```
Section "Screen"
    Identifier     "Default Screen"
    Device         "Configured Video Device"
    Monitor        "Configured Monitor"
    DefaultDepth    24
    SubSection     "Display"
        Virtual     640 480
        Depth       24
        Modes      "640x480@60"
    EndSubSection
EndSection
```

to this

```
Section "Screen"
    Identifier     "Default Screen"
    Device         "Configured Video Device"
    Monitor        "Configured Monitor"
    DefaultDepth    24
    SubSection     "Display"
 #       Virtual     640 480
 #       Depth       24
 #       Modes      "640x480@60"
          Modes     "1028x768@60"
    EndSubSection
EndSection
```

and it autodetected just fine after that. I suspect that all I actually had to do was remove the Virtual line, but I haven't had time to test this yet.

@astoroth88 If you're looking for where to get the drivers, these are the newest drivers:[http://us.download.nvidia.com/XFree86/Linux-x86_64/173.08/NVIDIA-Linux-x86_64-173.08-pkg2.run](http://us.download.nvidia.com/XFree86/Linux-x86_64/173.08/NVIDIA-Linux-x86_64-173.08-pkg2.run), and Neo0351's instructions worked wonderfully for me.

---

### Post by Burkey on 2008-04-15
Interesting comments about 169 vs 171 drivers.. I am on a laptop with a 9500m in it running hardy's default setup (169 driver).

Anyone else have this laptop chip and what drivers are you using?  I have not gotten to do any decent game tests on it yet but tanked Mag's the other night and saw framerates range from the 40's to over 200.  I am installing Crossover games trial right now to see how it fares but would love to read some more from other wow players.

---

### Post by RebateFX on 2008-04-18
> **Neo0351 said:**
> 
After installed

```
nano /etc/default/linux-restricted-modules-common
```

Last line should look like

```
DISABLED_MODULES="nv"
```

Hope this helps

Thanks for that last bit. I've been getting tired of reinstalling the nvidia driver every time I booted up because it kept reverting back to low res mode :)
Works like a charm now!

---

### Post by xmas47 on 2008-04-19
If you're still having trouble getting the driver installed for the 9600GT you should check out this thread

[http://ubuntuforums.org/showthread.php?t=717978&page=2]("http://ubuntuforums.org/showthread.php?t=717978&page=2")

---

### Post by Chaoticwhizz on 2008-05-03
I finally got the newest beta driver to work for my Nvidia 9600gt card. The funny thing is that all I needed to do was update the BIOS on my motherboard. Apparently, one of the corrections that the BIOS update fixed was a power management issue.This is what was likely causing the video card to immediately go into low power mode. I have a Chaintech VNF4 Ultra ZENITH VE motherboard. The BIOS I updated to was released in October 2006. 

After you have the driver installed, if your monitor goes blank and you get a "No Signal" message right at the moment when the X server should start loading at the boot up process then you may be having the same issue. Hope this helps.

---

### Post by kimme on 2008-06-18
> **Neo0351 said:**
> Ok, here's how I my 9600GT working with the 171.06 drivers.
First make sure you have all these replacing 2.6.22 with your kernel 

```
uname -r
sudo apt-get install linux-headers-'uname -r'
sudo apt-get install linux-restricted-modules-'uname -r'
sudo apt-get install linux-source-2.6.22 build-essential
```

Then ctrl+alt+F1 and log in as root
```
killall gdm
chmod a+x /location/to/driver
sh /location/to/driver
```

After installed

```
nano /etc/default/linux-restricted-modules-common
```

Last line should look like

```
DISABLED_MODULES="nv"
```

Hope this helps

I'm testing this out now and will report if it works because my previous efforts have all been in vain to get this 9600 GT card to work properly in Ubuntu with compiz enabled.

---

### Post by karansachdev on 2008-07-07
Hey guys  i have written a howto of Nvidia 9600Gt on hardy x64 . check out 
[http://karansachdev.blogspot.com](http://karansachdev.blogspot.com)
let me know if i missed out anything.

---

### Post by hraqhraq on 2008-08-14
> **Neo0351 said:**
> Ok, here's how I my 9600GT working with the 171.06 drivers.
First make sure you have all these replacing 2.6.22 with your kernel 

```
uname -r
sudo apt-get install linux-headers-'uname -r'
sudo apt-get install linux-restricted-modules-'uname -r'
sudo apt-get install linux-source-2.6.24 build-essential
```

Then ctrl+alt+F1 and log in as root
```
killall gdm
chmod a+x /location/to/driver
sh /location/to/driver
```

After installed

```
nano /etc/default/linux-restricted-modules-common
```

Last line should look like

```
DISABLED_MODULES="nv"
```

Hope this helps

Thank You very Much. You helped me a lot Keep coming here please.:KS

---

