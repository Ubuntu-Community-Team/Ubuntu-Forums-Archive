---
title: "After a while, screen turns black and flashes white stripes"
date: 2010-08-22
forum: Desktop Environments
---

### Post by 0percent on 2010-08-22
I just installed Ubuntu 10.04 on an old Compaq desktop, and after working on it for a while, screen randomly turns blank, usually with flashing horizontal white lines. Can anyone help? Someone already told me to try memtest, which I already performed, but nothing happened.(And I'm not very computer-savvy, so if you guys could please explain it to me in simpler terms, thanks).

---

### Post by rykel on 2010-08-23
I have a problem with the screen going black with white stripes at the top of the screen when booting up. It appears BEFORE the User Login Screen.

---

### Post by cutekazuya on 2010-08-23
Hello,

I had similar problem when the screen would go blank but i would get vertical grey lines.

I have the following graphics card:

"Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)"

To find out your graphics card type the following in termial:

```
lspci | grep VGA
```

apparently the driver which was in use "i915" was not working well with the xorg so i switched to "vesa" driver and since i have not ever had a problem.

```
sudo gedit /etc/X11/xorg.conf
```

The above command will show your current xorg.conf file, you want to change the Driver "whatever" to Driver "vesa"

or if its blank then copy/paste the following, save and reboot:

```

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
    Driver         "vesa"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

```

---

### Post by rykel on 2010-08-23
btw I got the problem after I installed some MacOSX theme and then removed it. I cannot recall exactly where I got the theme, but it was from someone's blog.

---

### Post by rykel on 2010-08-23
Hi, I solved my own problem! (by coincidence)

I purged nvidia-* and edubuntu-* from my system. One of them apparently "cleaned" up my bootup screen.   ):P

---

### Post by 0percent on 2010-08-23
To cutekazuya: Well, I found out that my graphics card is: 00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 03; however, I was not able to use the 2 last codes. When typing in the second code, it asked for my sudo password or something, which I, for some reason, could not type in (they're asking for my account password, right?), and for the last code, it just said "command not found" after each line.

---

### Post by cutekazuya on 2010-08-26
> **0percent said:**
> To cutekazuya: Well, I found out that my graphics card is: 00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 03; however, I was not able to use the 2 last codes. When typing in the second code, it asked for my sudo password or something, which I, for some reason, could not type in (they're asking for my account password, right?), and for the last code, it just said "command not found" after each line.

```
sudo gedit /etc/X11/xorg.conf
```

Above command will ask you for your sudo password, this is administrator password, type in the password that you use to login, it might be the same one.

the third section wrapped in code is not command to type into terminal but to copy/paste the data to the xorg.conf file that is opened by typing ```
sudo gedit /etc/X11/xorg.conf
```

---

### Post by extra.points on 2010-08-28
I have this problem too, for a new install.  the edit of xorg.conf won't work for a cd install, right?, so what other option do I have available?

---

### Post by waggers on 2010-08-30
I have the same graphics card, and more or less the same problem - random crashes with the screen going black, and some vertical white stripes flashing in the top half of the screen.  It hasn't happened when booting up, before the login screen (yet) so the problem isn't identical to Rykel's.

I tried adding ```
Driver         "vesa"
``` to the "Device" section of /etc/X11/xorg.conf as cutekazuya suggested, but on reboot that puts my system on a horribly low resolution with no ability to change it in System>Preferences>Monitors.

So then I tried replacing my existing device, monitor and screen sections with the code cutekazuya posted, but that caused my system to freeze completely on startup and I had to go into recovery mode and revert the changes.  So I'm back to square one.

Any further suggestions?

---

### Post by 0percent on 2010-08-30
Thanks cutekazuya, the problem hasn't shown up at all so far!

---

### Post by ckuru on 2010-08-30
I have a similar problem. I installed Ubuntu netbook version on my HP netbook Mini 110 with Windows 7. After installing Ubuntu the first boot up failed. It hangs with a black screen with a flashing text-mode cursor. After several attempts (just rebooting) it worked. However, about 95% of the time the machine fails to boot - after 3-4 seconds, and without showing anything on the screen (text or graphical), it hangs with a black screen with a flashing text-mode cursor. Pressing Ctrl-Alt-F7 (or any other keys) has no effect.

Can someone help me put on this ?

Thanks.
CK

---

### Post by rykel on 2010-09-01
> **ckuru said:**
> I have a similar problem. I installed Ubuntu netbook version on my HP netbook Mini 110 with Windows 7. After installing Ubuntu the first boot up failed. It hangs with a black screen with a flashing text-mode cursor. After several attempts (just rebooting) it worked. However, about 95% of the time the machine fails to boot - after 3-4 seconds, and without showing anything on the screen (text or graphical), it hangs with a black screen with a flashing text-mode cursor. Pressing Ctrl-Alt-F7 (or any other keys) has no effect.

Can someone help me put on this ?

Thanks.
CK

CK, your problem *might* be due to Ubuntu Lucid NOT working properly with the Intel Graphics chipset. At the bootup, press ESCAPE to see the "GRUB" screen. Press E to edit. Add "i915modeset=1" after "quiet". Press B to boot.

If my instructions above are wrong somewhere, I apologise because I am writing this from memory... hopefully someone reading this can point them out!

I am sorry for you that you have to go through the above hassle just to see a screen. I am giving up Ubuntu soon! (Ubuntu is becoming like Fedora - getting from bad to worse in detecting hardware and "working out of the box" with each new version. Not sure if Fedora is still THAT bad though!)

---

### Post by waggers on 2010-09-02
Here's my existing /etc/X11/xorg.conf file; what do I need to change to what to stop the random crashes but to carry on operating at 1024x768 resolution?

```

Section "Device"
	Identifier	"Configured Video Device"
	Option		"UseFBDev"		"true"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
EndSection
```

---

### Post by cutekazuya on 2010-09-03
> **waggers said:**
> I have the same graphics card, and more or less the same problem - random crashes with the screen going black, and some vertical white stripes flashing in the top half of the screen.  It hasn't happened when booting up, before the login screen (yet) so the problem isn't identical to Rykel's.

I tried adding ```
Driver         "vesa"
``` to the "Device" section of /etc/X11/xorg.conf as cutekazuya suggested, but on reboot that puts my system on a horribly low resolution with no ability to change it in System>Preferences>Monitors.

So then I tried replacing my existing device, monitor and screen sections with the code cutekazuya posted, but that caused my system to freeze completely on startup and I had to go into recovery mode and revert the changes.  So I'm back to square one.

Any further suggestions?

copy/paste below to your xorg file
```

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Unknown"
    HorizSync       30.0 - 75
    VertRefresh     50.0 - 85
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "vesa"
    Option	   "UseFBDev" "true"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

```

this should give you 1024x768 resolution at login screen and then you can set user screen by system>preferences>monitor

Basically by using driver "vesa" the random crashes will stop,  have been using it for over a month now at work without any issues.

if you have resolution issues then make sure you set the following for your monitor correctly, lookup your monitor manual:

HorizSync       30.0 - 75
VertRefresh     50.0 - 85

if you set them properly, you should get a list of all resolution your monitor can support.

hope this helps...

---

### Post by cadogan281 on 2010-09-03
thanks cutekazuya,that seemed to have fixed the problem.:p i have tried to overload my pc like when it usually crashes,but it doesnt do it anymore.i guess ubuntu doesnt like the older video cards.

---

### Post by pope_face on 2010-09-03
Alright, I know this has been essentially resolved, but I may be having the same issue, although I'm not sure. I'm running Ubuntu 10.04 32-bit Netbook Remix on a Gateway LT3115h with an AMD Athlon 64 and ATI Radeon graphics card (X1200 or something, IIRC... I can get the exact specs if needed). Here's what happens:

I'll be using my computer for a while (anywhere between 10 minutes and 2 hours), when all of a sudden the menu bar/title section just becomes a jumble of mostly white with some short, horizontal black bars, arranged diagonally... sort of like a television with an extraordinarily bad picture, or those Pay-Per-View channels that you haven't paid for. The only program I've really been using recently is Opera (happened even before install), and on occasion the horizontal lines spread down to the menu, tab, and URL sections of Opera. If I roll my mouse over any icons, they typically pop into focus. The desktop also gets the same issue, but with purple and black lines instead of white and black (although my desktop is black and white). The icons become sort of "fuzzy", and the lettering turns "blocky" and becomes impossible to read, as if it's become "extra-bold" (can't explain it otherwise). However, all this only happens to Ubuntu fonts... the icons on my desktop launch panels, as well as the options in the "shut-down" menu are affected, but fonts within Opera (webpages and tabs) are unaffected. Finally, sometimes the mouse just turns into a block of the same white/black stripes.

I'm also having an issue where the mouse is invisible after a sleep/wakeup of my computer, but I'm not sure if that's a related issue. I can still use the mouse, but I can't see it, so I just have to guess based on what's highlighted.

If I manage to upload the screenshot, I'll post it here, but hopefully someone will understand what I'm getting at. I tried the xorg.conf fix, but I'm getting an error that's telling me that the file doesn't exist. Hopefully I can get this sorted... I just bought this laptop and installed Ubuntu on it, and I've had minimal issues with my desktop install (although it's only a few months old), so I'm hoping to get this resolved... preferably before school starts on Tuesday.

Fil

---

### Post by waggers on 2010-09-04
> **cutekazuya said:**
> copy/paste below to your xorg file
```

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Unknown"
    HorizSync       30.0 - 75
    VertRefresh     50.0 - 85
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "vesa"
    Option	   "UseFBDev" "true"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

```

this should give you 1024x768 resolution at login screen and then you can set user screen by system>preferences>monitor

Basically by using driver "vesa" the random crashes will stop,  have been using it for over a month now at work without any issues.

if you have resolution issues then make sure you set the following for your monitor correctly, lookup your monitor manual:

HorizSync       30.0 - 75
VertRefresh     50.0 - 85

if you set them properly, you should get a list of all resolution your monitor can support.

hope this helps...
Thanks cutekazuya for your perseverance. After making that change, Ubuntu displayed the following message on startup:
```
Ubuntu is running in low graphics mode.
The following error is encountered.
You may need to update your configuration to solve this.

(EE) VESA(0): Driver cannot support depth 24
(EE) Screen(s) found, but none have a usable configuration
```

After which it gave me a range of options; after trying a couple which just froze my computer I selected to restore the default configuration, which let me in.  Now my xorg.conf file is completely empty.

Waiting to see if we still experience crashes now; if so I'll try again with one or other of cutekazuya's suggestions, unless there's a better idea around?

---

### Post by cutekazuya on 2010-09-04
> **waggers said:**
> Thanks cutekazuya for your perseverance. After making that change, Ubuntu displayed the following message on startup:
```
Ubuntu is running in low graphics mode.
The following error is encountered.
You may need to update your configuration to solve this.

(EE) VESA(0): Driver cannot support depth 24
(EE) Screen(s) found, but none have a usable configuration
```

After which it gave me a range of options; after trying a couple which just froze my computer I selected to restore the default configuration, which let me in.  Now my xorg.conf file is completely empty.

Waiting to see if we still experience crashes now; if so I'll try again with one or other of cutekazuya's suggestions, unless there's a better idea around?

hi, put a hash "#" before the default depth and also the horizontal and vertical refresh rates to comment them out something like this...

```
Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Unknown"
    #HorizSync       30.0 - 75
    #VertRefresh     50.0 - 85
    #Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "vesa"
    Option	   "UseFBDev" "true"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    #DefaultDepth    24
    SubSection     "Display"
        #Depth       24
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
EndSection
```

strange but depth 24 should work with vesa driver.

Anyways, the i915 driver does not work very well with the new x server in ubuntu 10.04 so using the standard vesa driver fixes the random crashes. I also have another older nvidia card and using it the xorg cpu usage would jump high on simple mouse movement. I dont think many older card drivers work very well with the new x server. 

keep trying, dont give up, when it works its well worth it.

---

### Post by waggers on 2010-09-04
Thanks, that at least gets me to the login screen on restart - but on 640x480 resolution again and I can't change it to anything else once logged in.

---

### Post by cutekazuya on 2010-09-04
> **waggers said:**
> Thanks, that at least gets me to the login screen on restart - but on 640x480 resolution again and I can't change it to anything else once logged in.

thats a good sign, what i would like you to do now is remove the hash from HorizSyn and VertRefresh and set it to the below values

HorizSync       30.0 - 65
VertRefresh     50.0 - 65

also try 

HorizSync       30.0 - 60
VertRefresh     50.0 - 60

you should then get 1024 hopefully, alternatively lookup the right values for your monitor and set it to that.

---

### Post by waggers on 2010-09-04
My monitor is a Dell E773C; I looked up the correct values but unfortunately I'm still stuck on 640.  My xorg file now reads like this:
```
Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Unknown"
    HorizSync       30.0 - 70
    VertRefresh     50.0 - 160
    #Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "VESA"
    Option	   "UseFBDev" "true"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    #DefaultDepth    24
    SubSection     "Display"
        #Depth       24
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
EndSection
```

---

### Post by cutekazuya on 2010-09-05
> **waggers said:**
> My monitor is a Dell E773C; I looked up the correct values but unfortunately I'm still stuck on 640.  My xorg file now reads like this:
```
Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Unknown"
    HorizSync       30.0 - 70
    VertRefresh     50.0 - 160
    #Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "VESA"
    Option	   "UseFBDev" "true"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    #DefaultDepth    24
    SubSection     "Display"
        #Depth       24
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
EndSection
```

remove the "Option "UseFBDev" "true"" by inserting hash before it

#Option	   "UseFBDev" "true"

see if that helps.

---

### Post by waggers on 2010-09-05
No change I'm afraid

---

### Post by cutekazuya on 2010-09-06
> **waggers said:**
> No change I'm afraid

hm.. type the following in termnial and let me know your card

```
lspci | grep VGA
```

then install ddcprobe

```
sudo apt-get install xresprobe
```

then run the following command:

```
sudo ddcprobe
```

which should output something like:

```

vbe: VESA 3.0 detected.
oem: VIA P4N800 PRO
vendor: 
product:  
memory: 65536kb
mode: 640x480x256
mode: 640x480x64k
mode: 640x480x16m
mode: 800x600x256
mode: 800x600x64k
mode: 800x600x16m
mode: 1024x768x256
mode: 1024x768x64k
mode: 1024x768x16m
mode: 1280x1024x256
mode: 1280x1024x64k
mode: 1280x1024x16m
mode: 1600x1200x256
mode: 1600x1200x64k
edid: 
edidfail
```

Notice that the attempt to probe the monitor's capabilities using the EDID protocol failed on my pc, necessitating the use of the xorg.conf

let me know if edid fails on yours or the output, i would also try below as a xorg file

```

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Unknown"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "vesa"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
EndSection
```

sorry for all the trial and error.

---

### Post by waggers on 2010-09-06
Output from lspci | grep VGA:
```
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)
```
Output from sudo ddcprobe:
(this is with a blank xorg.conf file by the way)
```


vbe: VESA 3.0 detected.
oem: Intel(r)845G/845GL/845GE/845GV Graphics Chip Accelerated VGA BIOS
vendor: Intel Corporation
product: Intel(r)845G/845GL/845GE/845GV Graphics Controller Hardware Version 0.0
memory: 832kb
mode: 1280x1024x256
mode: 1280x1024x64k
mode: 1280x1024x16m
mode: 1024x768x256
mode: 1024x768x64k
mode: 1024x768x16m
mode: 640x480x16m
mode: 800x600x64k
mode: 800x600x16m
mode: 132x25 (text)
mode: 132x43 (text)
mode: 132x50 (text)
mode: 132x60 (text)
mode: 640x480x256
mode: 800x600x256
mode: 640x480x64k
edid: 
edid: 1 3
id: d005
eisa: DELd005
serial: 3031796d
manufacture: 39 2003
input: sync on green, analog signal.
screensize: 32 24
gamma: 2.200000
dpms: RGB, active off, no suspend, no standby
timing: 640x480@60 Hz (VGA)
timing: 640x480@75 Hz (VESA)
timing: 800x600@60 Hz (VESA)
timing: 800x600@75 Hz (VESA)
timing: 1024x768@75 Hz (VESA)
ctiming: 640x480@85
ctiming: 800x600@85
ctiming: 1024x768@85
ctiming: 1280x1024@60
ctiming: 1152x864@75
dtiming: 1024x768@93
monitorserial: 6418039R01YM
monitorname: DELL E773c
monitorrange: 30-70, 50-160

```
About to try the suggested xorg file, will let you know what happens...

> sorry for all the trial and error.
No worries, thanks for not giving up

---

### Post by cutekazuya on 2010-09-06
niceone, could you run ddcprobe command using xorg file when its using vesa driver so we can see if edid is failing.

I have the same card with similar monitor.

If edid fails with vesa we have to add modeline 1024*768 and it should be good to go.

---

### Post by waggers on 2010-09-06
> **cutekazuya said:**
> niceone, could you run ddcprobe command using xorg file when its using vesa driver so we can see if edid is failing.

I have the same card with similar monitor.

If edid fails with vesa we have to add modeline 1024*768 and it should be good to go.
here's the ddcprobe output using the xorg file:
```
vbe: VESA 3.0 detected.
oem: Intel(r)845G/845GL/845GE/845GV Graphics Chip Accelerated VGA BIOS
vendor: Intel Corporation
product: Intel(r)845G/845GL/845GE/845GV Graphics Controller Hardware Version 0.0
memory: 832kb
mode: 1280x1024x256
mode: 1280x1024x64k
mode: 1280x1024x16m
mode: 1024x768x256
mode: 1024x768x64k
mode: 1024x768x16m
mode: 640x480x16m
mode: 800x600x64k
mode: 800x600x16m
mode: 132x25 (text)
mode: 132x43 (text)
mode: 132x50 (text)
mode: 132x60 (text)
mode: 640x480x256
mode: 800x600x256
mode: 640x480x64k
edid: 
edid: 1 3
id: d005
eisa: DELd005
serial: 3031796d
manufacture: 39 2003
input: sync on green, analog signal.
screensize: 32 24
gamma: 2.200000
dpms: RGB, active off, no suspend, no standby
timing: 640x480@60 Hz (VGA)
timing: 640x480@75 Hz (VESA)
timing: 800x600@60 Hz (VESA)
timing: 800x600@75 Hz (VESA)
timing: 1024x768@75 Hz (VESA)
ctiming: 640x480@85
ctiming: 800x600@85
ctiming: 1024x768@85
ctiming: 1280x1024@60
ctiming: 1152x864@75
dtiming: 1024x768@93
monitorserial: 6418039R01YM
monitorname: DELL E773c
monitorrange: 30-70, 50-160
```

---

### Post by cutekazuya on 2010-09-06
I think there is something else causing the low res for you.

The issue might be not giving the video card enough shared memory in the BIOS. 

Can you have look at bios settings and increase it to say 8mb or make it higher than whatever it is set to.

---

### Post by tbird6820 on 2010-09-06
I'm having same problem,system crashes and flashing vertical white bars about half way.

00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 03)

my current resolution:   1600 x 900 (16.9)
refresh rate:            60 Hz
Rotation:                Normal

---

### Post by cutekazuya on 2010-09-07
> **tbird6820 said:**
> I'm having same problem,system crashes and flashing vertical white bars about half way.

00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 03)

my current resolution:   1600 x 900 (16.9)
refresh rate:            60 Hz
Rotation:                Normal

```
sudo gedit /etc/X11/xorg.conf
```
The above command will show your current xorg.conf file

if it is NOT blank, you want to change the Driver "whatever" to Driver "vesa"

if its blank then copy/paste the following, save and reboot:

HorizSync and VertRefresh should bet set to your monitor values, lookup your monitor manual.

```

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
    Driver         "vesa"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
        Modes      "1600x900" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

```

---

### Post by tbird6820 on 2010-09-07
I did the copy,paste,save and rebooted and everything looks alittle stretched and I'm at 1280x1024 with 0 hz.

I can't get the 1600x900 and as long as it does crash I'm a happy camper!

---

### Post by waggers on 2010-09-07
> **cutekazuya said:**
> I think there is something else causing the low res for you.

The issue might be not giving the video card enough shared memory in the BIOS. 

Can you have look at bios settings and increase it to say 8mb or make it higher than whatever it is set to.
That was it! I changed the video buffer in BIOS from 1MB to 8MB and used this xorg.conf ```
Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Unknown"
    HorizSync       30.0 - 70
    VertRefresh     50.0 - 160
    #Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "VESA"
    Option	   "UseFBDev" "true"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    #DefaultDepth    24
    SubSection     "Display"
        #Depth       24
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
EndSection
```
and when I restarted, boom I'm in 1024x768 resolution.  Thank you so much!

---

### Post by cutekazuya on 2010-09-07
> **tbird6820 said:**
> I did the copy,paste,save and rebooted and everything looks alittle stretched and I'm at 1280x1024 with 0 hz.

I can't get the 1600x900 and as long as it does crash I'm a happy camper!

With vesa in xorg, it wont crash because ive had same issue and since using vesa driver its never happened even once.

To get 1600x900

Check if monitor probing is failing, as suggested in earlier posts

If it is failing lookup your monitor manual set horiz and vert refresh rates in xorg

Otherwise comment out with # or delete the horiz and vert lines in xorg. Simples

---

### Post by cutekazuya on 2010-09-07
> **waggers said:**
> That was it! I changed the video buffer in BIOS from 1MB to 8MB and used this xorg.conf ```
Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Unknown"
    HorizSync       30.0 - 70
    VertRefresh     50.0 - 160
    #Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "VESA"
    Option	   "UseFBDev" "true"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    #DefaultDepth    24
    SubSection     "Display"
        #Depth       24
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
EndSection
```
and when I restarted, boom I'm in 1024x768 resolution.  Thank you so much!

Brilliant, i am glad it helped.

---

### Post by tbird6820 on 2010-09-07
Ok now I did it.... I changed the rates and rebooted and it freezes at the logo, can't log in, had to use another computer to post.

---

### Post by cutekazuya on 2010-09-08
Hello everyone,

Here is a list of all the problems and solutions gathered so far for random crash with intel graphics card on lucid lynx.

This post is for everyone who has an intel card and face random crashing with vertical or horizontal grey lines across the screen and also for anyone who has screen resolution issues.

To find your graphics card, use the below code:

```
lspci | grep VGA
```

you should see output like:

```
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)

```

**_Random Crash issue:_**

To fix the random crashes, you have to tell ubuntu to use "vesa" driver instead of the "i915" that it uses for intel cards. You can also try to downgrade the "i915" driver and report back if it helps.

To use the vesa driver:

```
sudo gedit /etc/X11/xorg.conf
```

enter your sudo password and you will see either a blank file or with some contents in it. In either case, copy the following data to the file, save and reboot:

```
Section "Monitor"
    Identifier     "Configured Monitor"
EndSection

Section "Device"
    Identifier     "Configured Video Device"
    Driver         "vesa"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Configured Video Device"
    Monitor        "Configured Monitor"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
EndSection

```

upon reboot, Ubuntu will use the "vesa" driver and your system will not randomly crash anymore.

_**Screen resolution issues:**_

install ddcprobe

```
sudo apt-get install xresprobe
```

then run command 
```
sudo ddcprobe
```

if you have an output as below that shows edid fail:

```
vbe: VESA 3.0 detected.
oem: VIA P4N800 PRO
vendor: 
product:  
memory: 65536kb
mode: 640x480x256
mode: 640x480x64k
mode: 640x480x16m
mode: 800x600x256
mode: 800x600x64k
mode: 800x600x16m
mode: 1024x768x256
mode: 1024x768x64k
mode: 1024x768x16m
mode: 1280x1024x256
mode: 1280x1024x64k
mode: 1280x1024x16m
mode: 1600x1200x256
mode: 1600x1200x64k
edid: 
edidfail
```

You will then have to lookup your monitor manual for HorizSync & VertRefresh and use them in the xorg file as below:

```
Section "Monitor"
    Identifier     "Configured Monitor"
    HorizSync       30.0 - 70
    VertRefresh     50.0 - 150
EndSection

Section "Device"
    Identifier     "Configured Video Device"
    Driver         "vesa"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Configured Video Device"
    Monitor        "Configured Monitor"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
EndSection

```

Additionally, you can also specify resolution under the section "Screen" e.g.

```
SubSection     "Display"
    #Depth       24
    Modes      "1024x768" "800x600" "640x480"
EndSubSection
```

If you still have resolution issues, it might be because video card hsa not be allocated enough shared memory in the BIOS. 

Can you have look at bios settings and increase it from 1mb to 8mb or make it higher than whatever it is set to.

Finally,

If you cant get to login screen, you get a blank screen or it freezes

At grub, Press E to edit and try adding "i915.modeset=1" after "quiet" without the double quotes. Also try remove the quiet and splash.

---

### Post by tbird6820 on 2010-09-08
Ok I got it back with Press and hold Alt+SysRq keys, then press R E I S U B one after another (while holding Alt+SysRq). 

I'll retry again with HorizSync & VertRefresh rates.

---

### Post by wkhasintha on 2010-09-08
I seem to have got this problem too

---

### Post by tbird6820 on 2010-09-08
I can't seem to get 1600 x 900 (16.9)
video buffer in BIOS is 8MB

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Unknown"
    HorizSync       21.0 - 83.0
    VertRefresh     50.0 - 76.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "vesa"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
        Modes      "1600x900" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection



vbe: VESA 3.0 detected.
oem: Intel(r)845G/845GL/845GE/845GV Graphics Chip Accelerated VGA BIOS
vendor: Intel Corporation
product: Intel(r)845G/845GL/845GE/845GV Graphics Controller Hardware Version 0.0
memory: 8000kb
mode: 1280x1024x256
mode: 1280x1024x64k
mode: 1280x1024x16m
mode: 1024x768x256
mode: 1024x768x64k
mode: 1024x768x16m
mode: 640x480x16m
mode: 800x600x64k
mode: 800x600x16m
mode: 132x25 (text)
mode: 132x43 (text)
mode: 132x50 (text)
mode: 132x60 (text)
mode: 640x480x256
mode: 800x600x256
mode: 640x480x64k
edid: 
edid: 1 3
id: 18c5
eisa: HSD18c5
serial: 01010101
manufacture: 43 2009
input: separate sync, sync on green, analog signal.
screensize: 45 25
gamma: 2.200000
dpms: RGB, active off, suspend, standby
timing: 720x400@70 Hz (VGA 640x400, IBM)
timing: 640x480@60 Hz (VGA)
timing: 640x480@75 Hz (VESA)
timing: 800x600@60 Hz (VESA)
timing: 800x600@75 Hz (VESA)
timing: 1024x768@87 Hz Interlaced (8514A)
timing: 1024x768@70 Hz (VESA)
timing: 1024x768@75 Hz (VESA)
ctiming: 1280x1024@60
ctiming: 1400x1050@60
dtiming: 1600x900@59
monitorname: HF207
monitorrange: 21-83, 56-76 (my manual calls out VRR:50Hz to 76Hz HF:24kHz to 71kHz no change)
monitorserial: 943CM3XY0175

---

### Post by cutekazuya on 2010-09-09
vesa is a generic driver and you might not get all the resolutions for your monitor. try increasing VertRefresh 50 - 85

---

### Post by tbird6820 on 2010-09-09
> **cutekazuya said:**
> vesa is a generic driver and you might not get all the resolutions for your monitor. try increasing VertRefresh 50 - 85



thanks I'll try this latter this afternoon and let you know also when I loaded 10.04 on this computer I had a different monitor connected, I was thinking of maybe reloading 10.04 with this monitor connected.:o

---

### Post by u_lockjustice on 2010-09-10
I had (hopefully will not turn back into 'have') this problem and I want to thanks to all the people who posted. This is my first time using Ubuntu.

---

### Post by cutekazuya on 2010-09-10
> **u_lockjustice said:**
> I had (hopefully will not turn back into 'have') this problem and I want to thanks to all the people who posted. This is my first time using Ubuntu.

you are welcome and hopefully this bug will be fixed soon.

---

### Post by tbird6820 on 2010-09-10
> **cutekazuya said:**
> vesa is a generic driver and you might not get all the resolutions for your monitor. try increasing VertRefresh 50 - 85





I tried this.. no change and its alot better than before and it not crashing:p:p 

Thanks so much cutekazuya):P

---

### Post by perspectoff on 2010-09-10
The problem is definitely the integrated Intel graphics (which are on the 845GV motherboard).

There must be 5 or 6 identical threads currently running on Ubuntu forums. here's one that has going on for 8 months with identical problems:

[http://ubuntuforums.org/showthread.php?t=1442684](http://ubuntuforums.org/showthread.php?t=1442684)

Here's the solution that works for me:

* When booting up, choose recovery mode as root (or "root with networking"). This will give the command line (as root user). (If you are able to boot into the command line, then you don't need to do this, of course.)

* Edit the Grub2 configuration file:

sudo nano /etc/default/grub

* Change the line:

GRUB_CMDLINE_LINUX_DEFAULT="quiet"

to

GRUB_CMDLINE_LINUX_DEFAULT="i915.modeset=0"

* Then regenerate the Grub2 configuration file:

sudo grub-mkconfig --output=/boot/grub/grub.cfg

When I reboot, my Intel graphics work.

Some people have indicated that "i915.modeset=1" works for them, but it did not for me.

Here is the solution I used to use:

[https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4](https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4)

---

### Post by tbird6820 on 2010-09-11
> **perspectoff said:**
> The problem is definitely the integrated Intel graphics (which are on the 845GV motherboard).

There must be 5 or 6 identical threads currently running on Ubuntu forums. here's one that has going on for 8 months with identical problems:

[http://ubuntuforums.org/showthread.php?t=1442684](http://ubuntuforums.org/showthread.php?t=1442684)

Here's the solution that works for me:

* When booting up, choose recovery mode as root (or "root with networking"). This will give the command line (as root user). (If you are able to boot into the command line, then you don't need to do this, of course.)

* Edit the Grub2 configuration file:

sudo nano /etc/default/grub

* Change the line:

GRUB_CMDLINE_LINUX_DEFAULT="quiet"

to

GRUB_CMDLINE_LINUX_DEFAULT="quiet i915.modeset=0"

* Then regenerate the Grub2 configuration file:

sudo grub-mkconfig --output=/boot/grub/grub.cfg

When I reboot, my Intel graphics work.

Here is the solution I used to use:

[https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4](https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4)









Ok I'll try it... just a few questions.

If I go to terminal, paste sudo nano /etc/default/grub 
than PW

change this GRUB_HIDDEN_TIMEOUT_QUIET=true
to this:GRUB_CMDLINE_LINUX_DEFAULT="quiet i915.modeset=0

than you said, regenerate is that ctri + than enter? than ctri x than terminal, sudo grub-mkconfig --output=/boot/grub/grub.cfg



this is ny GNU nano 2.2.2           File: /etc/default/grub   

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

---

### Post by cutekazuya on 2010-09-13
> **perspectoff said:**
> The problem is definitely the integrated Intel graphics (which are on the 845GV motherboard).

There must be 5 or 6 identical threads currently running on Ubuntu forums. here's one that has going on for 8 months with identical problems:

[http://ubuntuforums.org/showthread.php?t=1442684](http://ubuntuforums.org/showthread.php?t=1442684)

Here's the solution that works for me:

* When booting up, choose recovery mode as root (or "root with networking"). This will give the command line (as root user). (If you are able to boot into the command line, then you don't need to do this, of course.)

* Edit the Grub2 configuration file:

sudo nano /etc/default/grub

* Change the line:

GRUB_CMDLINE_LINUX_DEFAULT="quiet"

to

GRUB_CMDLINE_LINUX_DEFAULT="quiet i915.modeset=0"

* Then regenerate the Grub2 configuration file:

sudo grub-mkconfig --output=/boot/grub/grub.cfg

When I reboot, my Intel graphics work.

Here is the solution I used to use:

[https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4](https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4)

I have tried the above and it still crashes, the crashes are alot less frequent but it does still crash.

so far, only vesa stops the crashes completely.

---

### Post by tbird6820 on 2010-09-13
> **perspectoff said:**
> The problem is definitely the integrated Intel graphics (which are on the 845GV motherboard).

There must be 5 or 6 identical threads currently running on Ubuntu forums. here's one that has going on for 8 months with identical problems:

[http://ubuntuforums.org/showthread.php?t=1442684](http://ubuntuforums.org/showthread.php?t=1442684)

Here's the solution that works for me:

* When booting up, choose recovery mode as root (or "root with networking"). This will give the command line (as root user). (If you are able to boot into the command line, then you don't need to do this, of course.)

* Edit the Grub2 configuration file:

sudo nano /etc/default/grub

* Change the line:

GRUB_CMDLINE_LINUX_DEFAULT="quiet"

to

GRUB_CMDLINE_LINUX_DEFAULT="quiet i915.modeset=0"

* Then regenerate the Grub2 configuration file:

sudo grub-mkconfig --output=/boot/grub/grub.cfg

When I reboot, my Intel graphics work.

Here is the solution I used to use:

[https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4](https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4)




I got to the recovery menu entered and rebooted, no change.
It is what it is.  Thanks

---

### Post by rmcellig on 2010-09-21
I am having the same white stripes appearing on my Dell 4500S. I tried what was suggested in this thread and now my screen is 640X480. How can I get it back to where it was before with no white stripes happening?

These are my settings in the xorg.conf file:

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Unknown"
    #HorizSync       30.0 - 75
    #VertRefresh     50.0 - 85
    #Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "vesa"
    Option	   "UseFBDev" "true"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    #DefaultDepth    24
    SubSection     "Display"
        #Depth       24
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

---

### Post by cutekazuya on 2010-09-22
@rmcellig

You get white stripes because it is freezing due to problems with  cache incoherency on 845G chipsets. I believe the devs are working for a solution.

here is the bug report

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/577308](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/577308)

The only way you can stop the freezing completely is to use the -vesa driver, it is all explained in the previous posts so please read

[http://ubuntuforums.org/showpost.php?p=9819880&postcount=36](http://ubuntuforums.org/showpost.php?p=9819880&postcount=36)

---

### Post by rmcellig on 2010-09-22
What I ended up doing was doing a full reinstall of Ubuntu 9.10. So ar so good. I am selling this Dell anyway and I just wanted to make sure I have a good OS on it. Ubuntu 9.10 is fine until they can fix the bug issue with 10.04 and the white stripes issue.

---

### Post by Avidanborisov on 2010-10-02
I did everything but my resolution now is 1024x786 instead of 1280x1024. Also, in the monitor configuration everything is unknown and the refresh rate is 0Hz . is this OK? and what should I do?

---

