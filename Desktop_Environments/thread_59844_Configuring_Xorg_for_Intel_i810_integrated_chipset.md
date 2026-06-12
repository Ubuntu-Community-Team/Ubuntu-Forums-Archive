---
title: "Configuring Xorg for Intel i810* integrated chipset"
date: 2005-08-25
forum: Desktop Environments
---

### Post by KPingus on 2005-08-25
Howdy,

I am not new to Linux but all new to [K]Ubuntu which I freshly installed on my desktop. I struggled a bit getting X.Org to properly use my Intel 82865G integrated video chip at resolutions other than 640x400.

I have managed to find all the information I needed (mostly on the fantastic Ubuntu forums) but the info was largely scattered all around. I thought it might be useful to others if I collected it all here in a short "howto".

*Note: I am not guaranteeing that anything below is accurate or useful and if you smoke your hardware after following the directions below, you're on your own. I will assume no responsibility. It did work for me out of the box. I only provide this in the hope that it will be useful to others.*

I have KUbuntu 5.04 and my monitor is a ViewSonic VG800 digital flat panel (18"). Xorg works just fine with the vesa driver but unfortunately, selecting the i810 drivers produces one of these two situations:

-  the X server falls back on a 640x480 resolution
- the monitor prevents high resolutions by displaying a 'Out of range' message

This monitor is capable of 1280x1024 at 60Hz non interlaced. Its specs are as follows:

Horizontal sync: 30-83 kHz
Vertical refresh: 50-75 Hz

These rates can be determined from several sources:

- Your vendor's website
- Your monitor user's manual
- The output of the X.Org vesa driver
- The output of 'sudo ddcprobe | grep monitorrange' if supported

The i810 drivers shipped with KUbuntu 5.04 seem outdated/buggy/inappropriate---I don't know which but either way, they are unable to achieve a resolution of 1280x1024. Let's update them:

0- Make sure you have gcc installed (you can install it using, e.g., the
    Synaptic Package Manager or any manager of your choice). Also make
    sure you have installed the kernel headers that correspond the the
    kernel you are using. You can find out using 'uname -r'. Make sure that
    the file
      /usr/src/linux-headers-`uname -r`/.config
    is the same as
      /boot/config-`uname -r`
    If it isn't, copy it over:
    % cp /boot/config-`uname -r` /usr/src/linux-headers-`uname -r`/.config

1- Download the latest snapshots from the DRI project
   [http://dri.freedesktop.org/snapshots/](http://dri.freedesktop.org/snapshots/)
   We need to grab the snapshots named
     common-...-linux.i386.tar.bz2
     i915-...-linux.i386.bz2

2- Stop the X server (and possibly [kg]dm)

3- Unpack the two archives in TWO DIFFERENT
   directories. Switch to the i915 directory and run
   'sudo ./install.sh'

4- Switch to the 'common' directory and do the same.

5- Edit your /etc/X11/xorg.conf and replace the 'vesa' driver with 'i810'

6- Restart your X server (e.g, type 'startx')

If you're not getting a resolution of 1280x1024, check your /etc/X11/xorg.conf and make sure that the resolution you want appears in all the "Display" SubSections of the "Screen" section.

If that doesn't do it, here follows a means to obtain a useful modeline and force the driver to use it:

Switch back to the vesa driver and have it use the resolution you like. Then:

% grep '_active' ~/Xorg.0.log
h_active: 1280  h_sync: 1328  h_sync_end 1440 h_blank_end 1688 h_border: 0
v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1066 v_border: 0

Dropping the last number of each line, collect this data into one long line:
1280 1328 1440 1688 1024 1025 1028 1066

Now obtain the clock speed:

% grep 'clock:' ~/Xorg.0.log
clock: 108.0 MHz   Image Size:  357 x 286 mm

The modeline is now complete:
Modeline "1280x1024_vesa" 108.0 1280 1328 1440 1688 1024 1025 1028 1066

and you can insert it in the "Monitor" section of your /etc/X11/xorg.conf

Next, in the "Screen" section, insert a subsection as so:
        SubSection "Display"
                Viewport        0 0
                Depth           24
                Modes           "1280x1024_vesa"
        EndSubSection
where we specify that the above modeline must be used.

Hopefully, things work fine now. I hope this short howto is useful to others.

---

### Post by syntruth on 2005-08-25
I use the default Xorg i810 drivers just fine, at 1280x1024x24, but I'm not using a flat panel, but a CTX crt.   Both in Gentoo and now in Kubuntu, but I'll keep this in mind since I am aiming to claim a new flat-panel myself.

---

### Post by libertyaikido on 2005-08-30
I'm not having any luck with compiling the drivers.  I keep getting an error that it can't find a kernel config file even though I have the correct kernel headers installed.  They match my running kernel.
```
blarsen@Scooby:/usr/src/linux/i915$ uname -r
2.6.10-5-386

blarsen@Scooby:/usr/src/linux/i915$ cd /usr/src/linux-headers-2.6.10-5/

blarsen@Scooby:/usr/src/linux-headers-2.6.10-5$ pwd
/usr/src/linux-headers-2.6.10-5
```
I even copied over the kernel config file from boot so that the .config file in /usr/src/linux matched the running kernel's config.

Here is the exact error message from the dri.log file.
```
Makefile:163: *** Cannot find a kernel config file.  Stop.
```
Any ideas on what needs to change?

---

### Post by incinerator on 2005-08-31
1.) libertyaikido: when specifying the path to the kernel headers, ALWAYS include the sub-architecture of the kernel you have installed.

E.g. DO NOT use /usr/src/linux-headers-2.6.10-5 BUT use
/usr/src/linux-headers-2.6.10-5-386 or whatever kernel is installed. Have a look into /usr/src/, that will give you the right path name.

2.) I suggest moving this thread to the [Hoary 5.04 Customization Tips & Tricks]("http://www.ubuntuforums.org/forumdisplay.php?f=58").

---

### Post by libertyaikido on 2005-08-31
OK.  It started compiling but ended with this error:
```
CONFIG_X86_CMPXCHG needs to be enabled in the kernel.
```
That configuration option isn't even in the kernel config file.  Does this mean I have to patch the kernel to allow me this option?

---

### Post by libertyaikido on 2005-08-31
Well it turns out that I didn't have to do any of the above to get it to work.

I saw on another thread that someone having the same problem noticed that the Horizontal and Vertical refresh rates were missing from their /etc/X11/xorg.conf file.  I added the appropriate rates for my monitor and it worked.

I didn't have to mess with drivers or anything.  Just FYI.

Thanks for your response though.  I appreciate it. :grin:

---

### Post by savage on 2005-09-09
Thank you so much. I was about to return the laptop I just got. Your instructions were the trick. I learned so much more about kernel and driver compilation doing this. For some reason it didn't work until I compiled a new kernel, took alot of tries to get that right. Research your hardware first.

Intel Pentium Pro Mobile
System Chip: Intel NG82915GM / FW82801FB (ICH6)
Intel GMA900
Intel i915gm

---

### Post by zAo on 2005-09-09
Otherwise:
Try the Xorg driver in 16bit mode, not 24bit. You'll probably have DRI in > 640*480 resolutions now :)

---

### Post by ztrek7 on 2005-09-10
I am not having a problem with my resolution, but, I think installing the 915G dri module is my answer. 

My problem: Any opengl program freezes computer to the point that a hard reset is needed. Even glxinfo freezes computer. I have a Toshiba Tecra A3, using intel 915GM video.  I installed Kubuntu Hoary. I used synaptic to put kernel at 2.6.10-5. 

I am getting the same error on the compilation. Cannot find kernel config file. I checked my /usr/src , and I do not have the -386 or any sub architecture. just linux-headers-2.6.10-5.

Any ideas? Or anyone know of the answer to my problem, maybe this is not it.

Thanks,

z

---

### Post by ztrek7 on 2005-09-10
I *guess* i figured out the -i386 part, i used synaptic to get headers, plus the one that has -386. Now, it starts to compile, but, I get:

CONFIG_X86_CMPXCHG needs to be enabled in the kernel.

Now, how do I recompile the kernel I have, and enable this option? I would like to leave all the settings, maybe take out the hardware I don't have, and put this option in. 

Any help would be appreciated.

Thanks,

Z

---

