---
title: "Issue with 8800 GTS"
date: 2009-02-20
forum: General Help
---

### Post by Nukinfuts on 2009-02-20
I have a laptop with a Nvidia GeForce 8800 GTS 512MB GDDR3 video card. I have tried multiple reinstalls, propietary drivers, and envyNG. I have tried Hardon and now Intrepid, all have this same issue.

No matter what i do my resolution is stuck on 1650x1080 and it is making me insane. Searches and trying things has not gotten me anywhere. Any ideas?

---

### Post by Nukinfuts on 2009-02-20
And now when i go under system and click on "Nvidia X Server Settings" it tells me i do not appear to be using the Nvidia X Driver. Must be Envy's fault.

This is retarded.....

---

### Post by Therion on 2009-02-20
Okay, so where are you now?  Meaning what version of Ubuntu do you have installed for starters?
And what is the native resolution of your laptop and what resolution are you wanting it to display?

---

### Post by Nukinfuts on 2009-02-20
Intrepid, 32bit.

Not sure what the native is, i cant even remember what i have been using in vista. I can tell you where it is at now is on less then the max in vista. When i reboot i will jump into Vista and check. I would like to choose any resolution i want like a normal person.

My old laptop had an 8600 and i never had this issue.

---

### Post by Nukinfuts on 2009-02-21
Today for the second time i booted up and got a dialog about low graphics mode. Envy seems to have caused more problems and fixed none. And i tried to install the drivers from nvidia but no matter how i do it (even ctrl+alt+F1) i keep getting "please close xserver".

What a pain...

---

### Post by Nukinfuts on 2009-02-22
The startup error has yet to return, but im getting nowhere.

---

### Post by makisupa123 on 2009-02-22
Interesting avatar...


You need to stop the GDM service in order to run the nvidia installer.

```
/etc/init.d/gdm stop
```

My advice is run envyng (-t) and make sure the driver from synaptic has been removed.  Then reboot, stop gdm, and run the installer you downloaded.  

Now for your resolution issue:

I'm not real sure why you want to run at a resolution other than the native resolution of your panel, but you might ned to add them to your xorg.conf.

--Mak

---

### Post by Nukinfuts on 2009-02-22
>>I'm not real sure why you want to run at a resolution other than the native resolution of your panel

Because i dont like constantly squinting or using zoom. it hurts my eyes. I love ubuntu but using it shouldnt remove my option to choose a resolution im comfortable with. Over a year and 2 computers this is the first issue with the video so i cant complain.

I will give that a shot.

---

### Post by OliW on 2009-02-22
I'd seriously consider using assistive technologies and/or increased font dpi over a non-native resolution.

---

### Post by 0bso on 2009-02-22
> **Nukinfuts said:**
> Today for the second time i booted up and got a dialog about low graphics mode. Envy seems to have caused more problems and fixed none. And i tried to install the drivers from nvidia but no matter how i do it (even ctrl+alt+F1) i keep getting "please close xserver".

What a pain...

try deleting /usr/lib/libGLcore.so.1, /usr/lib/libGLcore.so.180.29, /usr/lib/xorg/modules/extensions/libglx.so, and /usr/lib/xorg/modules/extensions/libglx.so.180.29. 

Then run nvidia-uninstall in terminal. Reboot and install the driver from the Hardware Drivers menu.

I had the same problem yesterday after updating drivers and that's what fixed it.

---

### Post by Nukinfuts on 2009-02-22
> **OliW said:**
> I'd seriously consider using assistive technologies and/or increased font dpi over a non-native resolution.

I like what i like. I dont see why correcting this issue to get ubuntu to work the way it always has for me in the past would be such a bad thing.

> **0bso said:**
> try deleting /usr/lib/libGLcore.so.1, /usr/lib/libGLcore.so.180.29, /usr/lib/xorg/modules/extensions/libglx.so, and /usr/lib/xorg/modules/extensions/libglx.so.180.29. 

Then run nvidia-uninstall in terminal. Reboot and install the driver from the Hardware Drivers menu.

I had the same problem yesterday after updating drivers and that's what fixed it.

Thanks for the tip. When i get home i will give all this a try and see if i can get it fixed.

---

### Post by Nukinfuts on 2009-02-22
i stopped gdm and ran the installer, only to hit a kernel error. Here is the log file:

> 
nvidia-installer log file '/var/log/nvidia-installer.log'
creation time: Sun Feb 22 14:50:34 2009
installer version: 1.0.7

option status:
  license pre-accepted    : false
  update                  : false
  force update            : false
  expert                  : false
  uninstall               : false
  driver info             : false
  precompiled interfaces  : true
  no ncurses color        : false
  query latest version    : false
  OpenGL header files     : true
  no questions            : false
  silent                  : false
  no recursion            : false
  no backup               : false
  kernel module only      : false
  sanity                  : false
  add this kernel         : false
  no runlevel check       : false
  no network              : false
  no ABI note             : false
  no RPMs                 : false
  no kernel module        : false
  force SELinux           : default
  no X server check       : false
  no cc version check     : false
  force tls               : (not specified)
  X install prefix        : (not specified)
  X library install path  : (not specified)
  X module install path   : (not specified)
  OpenGL install prefix   : (not specified)
  OpenGL install libdir   : (not specified)
  utility install prefix  : (not specified)
  utility install libdir  : (not specified)
  doc install prefix      : (not specified)
  kernel name             : (not specified)
  kernel include path     : (not specified)
  kernel source path      : (not specified)
  kernel output path      : (not specified)
  kernel install path     : (not specified)
  proc mount point        : /proc
  ui                      : (not specified)
  tmpdir                  : /tmp
  ftp mirror              : [ftp://download.nvidia.com](ftp://download.nvidia.com)
  RPM file list           : (not specified)

Using: nvidia-installer ncurses user interface
-> License accepted.
-> Installing NVIDIA driver version 180.29.
-> No precompiled kernel interface was found to match your kernel; would you li
   ke the installer to attempt to download a kernel interface for your kernel f
   rom the NVIDIA ftp site ([ftp://download.nvidia.com)?](ftp://download.nvidia.com)?) (Answer: Yes)
-> No matching precompiled kernel interface was found on the NVIDIA ftp site;
   this means that the installer will need to compile a kernel interface for
   your kernel.
-> Performing CC sanity check with CC="cc".
-> Performing CC version check with CC="cc".
ERROR: Unable to find the kernel source tree for the currently running kernel. 
       Please make sure you have installed the kernel source files for your
       kernel and that they are properly configured; on Red Hat Linux systems,
       for example, be sure you have the 'kernel-source' or 'kernel-devel' RPM
       installed.  If you know the correct kernel source files are installed,
       you may specify the kernel source path with the '--kernel-source-path'
       command line option.
ERROR: Installation has failed.  Please see the file
       '/var/log/nvidia-installer.log' for details.  You may find suggestions
       on fixing installation problems in the README available on the Linux
       driver download page at [www.nvidia.com](www.nvidia.com).

---

### Post by Nukinfuts on 2009-02-23
0bso's idea didnt fix it either.

---

### Post by makisupa123 on 2009-02-23
The error message is fairly explicit.  The kernel mods included in the installer are unacceptable so it needs to build these modules.  In order to do this it needs the source of your running kernel.  

```
sudo apt-get install linux-source
```

Then run the installer again.

Also:  I second OliW's suggestion.  There are better ways of making things more readable/larger than running your panel at a lower resolution.  But we can cross that bridge once X is working again.

--Mak

---

### Post by Nukinfuts on 2009-03-10
I fixed it and forgot to come back and post. Honestly, i dont even know how. I removed envy and magically it fixed ittself. My resolution can be changed, compiz works great, etc.

Ironically i ended up running the resolution i had when i started this thread that i hated so much because now im used to it....heh

---

