---
title: "Nvidia GeForce driver problem"
date: 2005-10-16
forum: Desktop Environments
---

### Post by nrwilk on 2005-10-16
I'm trying to setup the drivers for my GeForce 6600, because, well, I like hardware 3D acceleration.  hehe

I tried this series of commands that were suggested in another thread:

```

sudo apt-get install nvidia-glx
sudo nvidia-glx-config enable
sudo reboot
```

I had already gotten the nvidia-glx file from adept, but hadn't known that I had to enable it.

After this, when I rebooted the startup process halted after the initial loading screen, showing me the less-pretty text version of the load-up process (syncing with ntp server, etc...).  After that, it got no further.  So, I hit ctrl-alt F2 to get another console, logged in and tried to start X with the startx command.

I get this error:
```
ERROR: API mismatch: The NVIDIA kernal module is version 1.0.7174, but this X module is version 1.0.7667.  Please be sure that your kernal module and all NVIDIA driver files have the same driver version.
```

Can someone please help me resolve this issue?  I'm using Kubuntu i386 Breezy release on a AMD 64 3500+, GeForce 6600TD, 1GB ram.

Thank you so much for any help!!!

---

### Post by nrwilk on 2005-10-16
I really hate to bump this so quickly, but I need the box to do some online homework.  Does anyone have any ideas?

Do I need to update my kernal, or downgrade my Nvidia drivers?

I'm sure someone here knows a solution to this problem.

Thanks for any help that can be provided!

PS, I got this card because I knew it was supported in both Windows and ubuntu.  I know I can get it running, I just need some help.

---

### Post by Lord Illidan on 2005-10-16
I think you need to update your kernel...
Or else try getting the official nvidia drivers from [www.nvidia.com](www.nvidia.com)

---

### Post by nrwilk on 2005-10-16
[QUOTE=Lord Illidan]I think you need to update your kernel...[/QUOTE]

This is going to sound extremely stupid, I'm sure...

How do I update the kernal?
Remember, I have only the command line to work with for now.

[QUOTE=Lord Illidan]Or else try getting the official nvidia drivers from [www.nvidia.com](www.nvidia.com)[/QUOTE]

Aren't there a lot of problems that arise from using the proprietary drivers?

---

### Post by 89c51 on 2005-10-16
[QUOTE=Fealos]Aren't there a lot of problems that arise from using the proprietary drivers?[/QUOTE]

i use hoary and the only problem i had was when x was updated
i reinstalled and solved the whole thing

---

### Post by astoltz on 2005-10-16
You need to install the version of linux-restricted-modules that matches your kernel.

---

### Post by nrwilk on 2005-10-16
[QUOTE=89c51]i use hoary and the only problem i had was when x was updated
i reinstalled and solved the whole thing[/QUOTE]

OK, so it made a backup of the file it changed when I enabled the nividia-glx driver.  How can I use that backup to get X working again in order to download the proprietary driver to see if that one will work.  Furthermore, how can I update my kernal (isn't that pretty important?)

[QUOTE=astoltz]You need to install the version of linux-restricted-modules that matches your kernel.[/QUOTE]

do you mean that you can only have driver versions that match the version number of your kernal?  I only saw one Nvidia-glx driver when I downloaded it in Adept, where can Ifind the driver that matches my kernal?  Or, if I update my kernal, will it match the currently installed driver?

Thanks!

---

### Post by malacoda on 2005-10-16
I had a similar problem.

My initial install would go well, but once I installed the nVidia drivers via the Adept Pkg manager my system would hang up each time I booted right after finishing 'Checking Battery Status'.

After a bit of research and some input from others, I came to suspect the nVidia drivers I was using from the repositories via Adept Pkg Mgr had a bug that locked up X11 (or xserver or what ever you want to call it...).

I decided to install from source by following tseliot's how-to:
[http://www.ubuntuforums.org/showthread.php?t=75074&highlight=nvidia]("http://www.ubuntuforums.org/showthread.php?t=75074&highlight=nvidia")

Before you do though I recommend installing Mozilla Firefox first.  When I tried downloading the driver he recommends (from the nVidia website) my desktop would become corrupt (due to not having the video driver installed yet) if I used Konqeror.

Installing the driver per this how-to resolved my 'boot hang' issue.

---

### Post by astoltz on 2005-10-16
[QUOTE=Fealos]
do you mean that you can only have driver versions that match the version number of your kernal?  I only saw one Nvidia-glx driver when I downloaded it in Adept, where can Ifind the driver that matches my kernal?  Or, if I update my kernal, will it match the currently installed driver?[/QUOTE]

nvidia-glx depends on the package "linux-restricted-modules-[kernel_ver]". where [kernel_ver] is the version of the kernel you have installed.  Touble is, ANY linux-restricted-modules-xxxx will satisfy the nvidia-glx dependancy so it's quite easy to get the version mix-ups.  I'm using the 2.6.12-9-k7 kernel so I had to install the linux-restricted-modules-2.6.12-9-k7 package before nvidia-glx.  Search in synaptic - there are lots of linux-restricted-modules-xxxxxxx packages that match the various kernels out there.

---

### Post by nrwilk on 2005-10-16
[QUOTE=astoltz]nvidia-glx depends on the package "linux-restricted-modules-[kernel_ver]". where [kernel_ver] is the version of the kernel you have installed.  Touble is, ANY linux-restricted-modules-xxxx will satisfy the nvidia-glx dependancy so it's quite easy to get the version mix-ups.  I'm using the 2.6.12-9-k7 kernel so I had to install the linux-restricted-modules-2.6.12-9-k7 package before nvidia-glx.  Search in synaptic - there are lots of linux-restricted-modules-xxxxxxx packages that match the various kernels out there.[/QUOTE]


Is this method better than using the following command?

```
sudo apt-get install nvidia-glx-legacy
```

Because I found this in another thread, and I used it, and now I get the nvidia splash at X startup, so I assume the drivers work, but I can't test for sure because almost every single screensaver does not work now.  Even non-OpenGL savers that ran before I had these drivers.  The wierd part is, most of the OpenGL screensavers run the little tiny preview in the window, but if I hit "test" it's only a black screen (even GL-Gears).  Is this normal?  I can run one of these screensavers ONCE, but then after that, until I reboot, I can't view them anymore.  Also, if I run GL-Gears using this method, I only get ~400FPS, which seems to be WAY low for my setup (Athlon 64 3500+, 1GB ram, GeForce 6600TD).  Does this have to do with the legacy drivers?  Are these the drivers I need for a GeForce 6600TD?

Thanks again!

---

### Post by brentoboy on 2005-10-16
I had the same problem.

Go with the vesa driver,  and if you want "action" download the stuff on nvidia's site, and follow the Howto: NVIDIA post that is all over this forum.

Those seem to be the only real option. - or, download the source to the ubuntu nv driver, and compile it  to your runing kernel - but for all the hastle, you might as well go with the proprietary "free" nvidia driver from the folks who made the chip.

---

### Post by nrwilk on 2005-10-16
[QUOTE=brentoboy]I had the same problem.

Go with the vesa driver,  and if you want "action" download the stuff on nvidia's site, and follow the Howto: NVIDIA post that is all over this forum.

Those seem to be the only real option. - or, download the source to the ubuntu nv driver, and compile it  to your runing kernel - but for all the hastle, you might as well go with the proprietary "free" nvidia driver from the folks who made the chip.[/QUOTE]

OK, I'm going to install those proprietary drivers as soon as I get the chance.

But, what is causing my inability to run 95% of my screensavers?  I assume it's not the driver because I can't even run non-OpenGL ones.

---

### Post by RAOF on 2005-10-17
If you've got a working X, I'd suggest running synaptic and searching for "linux".  Remove the nvidia-glx packages, the legacy package, and the "linux-restricted" stuff which don't correspond to your kernel version.

Install nvidia-glx again.  Make sure you have the "linux-restricted-modules-k7" (or whatever kernel you run) installed - this package should always depend on the correct restricted modules for the kernel.  It is this package that was causing the original error (the kernel version mismatch thing).

To get back your original xorg.conf, I believe you only need to run "sudo nvidia-glx-config disable"

I think the legacy drivers are the root of your screensaver problems - they're somewhat old, and the 6600 is quite new.  There's probably stuff those drivers don't do correctly for your card.

With all of this, I've been running the Breezy nvidia-glx package all the way through testing, and they've always worked fine for me (on amd64, though :)).  There's not much point in getting the drivers from nvidia - the package contains the 7667 version of those drivers, and the latest (version 7676) apparently have known bugs.  And are only really needed for the 7800.

---

### Post by YangFuShang on 2005-10-17
i couldnt find the linux-restricted for my kernel, 2.6.12-9-k8-smp though...

---

### Post by RAOF on 2005-10-17
[QUOTE=YangFuShang]i couldnt find the linux-restricted for my kernel, 2.6.12-9-k8-smp though...[/QUOTE]
Really?  My "apt-cache search linux-restricted" says:
```
linux-restricted-modules-2.6.12-9-amd64-k8-smp - Non-free Linux 2.6.12 modules on AMD K8 SMP
```
You should be able to install that.

Edit: oh, wait.  Is that a non-64-bit k8 kernel?  I didn't know they made them :)

---

### Post by shenki on 2005-10-17
I had this exact problem after following the HOWTO on this forum.

The problem is, that for some reason there is a nvidia kernel extension in /lib/modules/2.6.12-9-386/volatile/. When you install the drivers using the nvidia.run package, it installs it's kernel extension in /lib/modules/2.6.12-9-386/kernel/drivers/video. However, I think that modules.dep still points to the nvidia.ko in volatile.

To solve our problem, log out of gnome, press ctrl-alt-F1 to get to a virtual console, log in, and follow these steps:

```
sudo -s
/etc/init.d/gdm stop
modprobe -r nvidia
mv /lib/modules/2.6.12-9-386/volatile/nvidia.ko ~/nvidia.ko_ORIGINAL
ln -s /lib/modules/2.6.12-9-386/kernel/drivers/video/nvidia.ko /lib/modules/2.6.12-9-386/volatile/nvidia.ko
modprobe nvidia
/etc/init.d/gdm start

```

and you should be good to go. (for the uninitiated: you have just stoped gnome, removed the old nvidia module from the kernel and copied a backup to your home directory, and then made a link to the new module. The last two lines then load the new module, and resart gnome)

(note: this isn't how i fixed things; I ran the installer, and once it had compiled it's kernel module, I opened up another terminal and copied it out of /tmp to an alternate location, and then copied that extension into the volatile/ dir. So if anyone has problems, post here, and we can work out what is wrong with my solution)

---

### Post by nrwilk on 2005-10-17
[QUOTE=RAOF]If you've got a working X, I'd suggest running synaptic and searching for "linux".  Remove the nvidia-glx packages, the legacy package, and the "linux-restricted" stuff which don't correspond to your kernel version.

Install nvidia-glx again.  Make sure you have the "linux-restricted-modules-k7" (or whatever kernel you run) installed - this package should always depend on the correct restricted modules for the kernel.  It is this package that was causing the original error (the kernel version mismatch thing).

To get back your original xorg.conf, I believe you only need to run "sudo nvidia-glx-config disable"

I think the legacy drivers are the root of your screensaver problems - they're somewhat old, and the 6600 is quite new.  There's probably stuff those drivers don't do correctly for your card.

With all of this, I've been running the Breezy nvidia-glx package all the way through testing, and they've always worked fine for me (on amd64, though :)).  There's not much point in getting the drivers from nvidia - the package contains the 7667 version of those drivers, and the latest (version 7676) apparently have known bugs.  And are only really needed for the 7800.[/QUOTE]

well I tried this, and I get the exact same version mismatch error when I try to start X.  Though, it did unbreak it when I typed
```
sudo nvidia-glx-config disable
```

I also tried the way with the proprietary drivers last night, and I got a big error that it seems no one else got.  I'm starting to get really frustrated because I got this card because it was suggested to me as being fully compatible with both Windows and ubuntu.

---

### Post by nrwilk on 2005-10-17
[QUOTE=shenki]I had this exact problem after following the HOWTO on this forum.

The problem is, that for some reason there is a nvidia kernel extension in /lib/modules/2.6.12-9-386/volatile/. When you install the drivers using the nvidia.run package, it installs it's kernel extension in /lib/modules/2.6.12-9-386/kernel/drivers/video. However, I think that modules.dep still points to the nvidia.ko in volatile.[/QUOTE]


Actually, the problem I got when trying to install the proprietary drivers was different.  When I got to the step where you give this command:
```
sudo sh NVIDIA-Linux-x86-1.0-7667-pkg1.run
```
it would go into the nvidia installer, but it would tell me that it could not find a version that matched my kernal, or something like that.  I uninstalled all the nvidia stuff before I tried this method, would that have made a difference?  I tried it twice, and both times got the same error.  There was also another error that I got both times, but it let me "ignore it and continue."

GRRRRRRRRRRRRRRRrrr.:( :( :(

---

### Post by brentoboy on 2005-10-17
[QUOTE=Fealos]
I also tried the way with the proprietary drivers last night, and I got a big error that it seems no one else got.  I'm starting to get really frustrated because I got this card because it was suggested to me as being fully compatible with both Windows and ubuntu.[/QUOTE]

What was your error.

You are going to have to remove the nvidia-glx stuff from synaptic (sounds like you did this already)

Make sure you have gcc-3.4 and g++-3.4, build-essential - the kernel headers and all that stuff

Change your default C compiler to 3.4 (the one the kernel was compiled with)

# sudo CC=gcc-3.4
# sudo export CC

then, you should be able to compile the nvidia kernel module.

# sudo sh NVIDIA-Linux-x86-1.0-7667-pkg1.run

Get used to doing it, becuase every time the ubuntu team tweaks the kernel and recomiples it, your gonna break, and you'll have to run those three lines again.  :)

---

### Post by shenki on 2005-10-17
so what were the steps you went through to create this error? If you follow the guide that you linked to, it tells you to:

1) install build-essential, kernel-sources, gcc-3.4, etc
2) log out of gnome and stop gdm
3) 'export CC=gcc-3.4'
4) run the installer, saying 'no' to downloading a kernel interface module

you cannot download a kernel module from the nivida site, as they (currently) only provide pre build modules for other distro's.

---

### Post by nrwilk on 2005-10-17
[QUOTE=brentoboy]What was your error.

You are going to have to remove the nvidia-glx stuff from synaptic (sounds like you did this already)

Make sure you have gcc-3.4 and g++-3.4, build-essential - the kernel headers and all that stuff

Change your default C compiler to 3.4 (the one the kernel was compiled with)

# sudo CC=gcc-3.4
# sudo export CC

then, you should be able to compile the nvidia kernel module.

# sudo sh NVIDIA-Linux-x86-1.0-7667-pkg1.run

Get used to doing it, becuase every time the ubuntu team tweaks the kernel and recomiples it, your gonna break, and you'll have to run those three lines again.  :)[/QUOTE]


I followed the instuctons expicitly.

I removed everything.  I downloaded the three files from adept, I stopped KDM, I did these:
# sudo CC=gcc-3.4
# sudo export CC
then when it enters the nvidia installation program it gives me an error.  I'll do it again, and I'll write down the error to post, brb.

---

### Post by nrwilk on 2005-10-17
OK, I tried with both gcc3.3 and gcc 3.4 using these two sets of commands: ```
CC=gcc3.3 export CC
``` and ```
CC=gcc3.4 export CC
``` Both times it told me that it could not find a correct driver to match my kernel, but I said no when it asked whether I'd like it to download one. It told me it would try to compile one, and I said ok. It gave me an error about the version of gcc I was using both times. Should I try any other gcc versions?

here is a copy of my NVIDIA installer log:
```

nvidia-installer log file '/var/log/nvidia-installer.log'
creation time: Mon Oct 17 14:17:00 2005

option status:
  license pre-accepted    : false
  update                  : false
  force update            : false
  expert                  : false
  uninstall               : false
  driver info             : false
  no precompiled interface: false
  no ncurses color        : false
  query latest driver ver : false
  OpenGL header files     : true
  no questions            : false
  silent                  : false
  no backup               : false
  kernel module only      : false
  sanity                  : false
  add this kernel         : false
  no runlevel check       : false
  no network              : false
  no ABI note             : false
  no RPMs                 : false
  force tls               : (not specified)
  force compat32 tls      : (not specified)
  X install prefix        : /usr/X11R6
  OpenGL install prefix   : /usr
  compat32 install prefix : (not specified)
  installer install prefix: /usr
  utility install prefix  : /usr
  kernel name             : (not specified)
  kernel include path     : (not specified)
  kernel source path      : (not specified)
  kernel output path      : (not specified)
  kernel install path     : (not specified)
  proc mount point        : /proc
  ui                      : (not specified)
  tmpdir                  : /tmp
  ftp mirror              : ftp://download.nvidia.com
  RPM file list           : (not specified)

Using: nvidia-installer ncurses user interface
WARNING: Skipping the runlevel check (the utility `runlevel` failed to run).
-> License accepted.
-> No precompiled kernel interface was found to match your kernel; would you li
   ke the installer to attempt to download a kernel interface for your kernel f
   rom the NVIDIA ftp site (ftp://download.nvidia.com)? (Answer: No)
-> No precompiled kernel interface was found to match your kernel; this means
   that the installer will need to compile a new kernel interface.
-> Kernel source path: '/lib/modules/2.6.12-9-386/build'
-> Performing CC test with CC="gcc3.3".
-> gcc-version-check failed:
   
   ./usr/src/nv/conftest.sh: line 9: gcc3.3: command not found
   Could not compile gcc-version-check.c
   
   If you know what you are doing and want to ignore the gcc version check, sel
   ect "No" to continue installation.  Otherwise, select "Yes" to abort install
   ation, set the CC environment variable to the name of the compiler used to c
   ompile your kernel, and restart installation.  Abort now? (Answer: Yes)
ERROR: Installation has failed.  Please see the file
       '/var/log/nvidia-installer.log' for details.  You may find suggestions
       on fixing installation problems in the README available on the Linux
       driver download page at www.nvidia.com.

```

---

### Post by brentoboy on 2005-10-17
it should say 2 things in that error:

Your current default compiler is gcc x.x

Your kernel was compiled with gcc x.x

please fix it. :)

What does it say for each of those?

You need your default to match the kernel - which SHOULD be gcc 3.4  (that was the latest stable when ubuntu selected a compiler for the kernel for breezy, and it looks like they will stick with it for the durration of breezy - maybe even longer)

Breezy shipps with a default compiler gcc 4.0 - most the ubuntu apps were compiled with it.  It is good enough unless you are compiling a kernel module - which MUST match the compiler used for the kernel - for stability reasons.

key points:

CC is capitol, also notice the dash between gcc and 3.4
# CC=gcc-3.4

after that is done
#export CC

then run the install script.

what does the error say exactly?

---

### Post by nrwilk on 2005-10-17
Wow do I feel crappy. it was because I was using the command ```
CC=gcc3.4
``` instead of ```
CC=gcc-3.4
``` got it working! yay! Although it seems the screensavers still don't work. Let me restart and try it again.

EDIT:
Driver seems to work well, but I can't benchmark with Gears(GL) because I still cannot open most of the screensavers. I downloaded these packages:

kscreensaver
kscreensaver-xsavers
rss-glx
xscreensaver
xscreensaver-data
xscreensaver-nognome

is there anything I need to do after I download these to get them to be compatible?  It is my understanding that the xscreensaver-nognome makes the xscreensavers compatible with KDE, right?  Do I need to enable it somehow?

Under Hoary all these savers just worked.  (of course that was on a PPC machine, with a radeon 9800 Pro with no drivers, so I got about 3 FPS on all of them)

---

### Post by brentoboy on 2005-10-17
[QUOTE=Fealos]Wow do I feel crappy. it was because I was using the command ```
CC=gcc3.4
``` instead of ```
CC=gcc-3.4
``` got it working! yay! Although it seems the screensavers still don't work. Let me restart and try it again.
[/QUOTE]

Dont let it get you too down, I spent 5 days, and hoarty, K-hoarty, breezy, k-breezy, breezy64, ....  

trying to fix the same thing... and I was missing the hyphen and not capitolizing the CC.  Now, its a 15 second snap getting it working when I start over, or get an updated kernel.  -nothing like learning the hard way, right?

:)

---

### Post by nrwilk on 2005-10-18
Anyone have an idea why I can't run any of the screensavers?

Information on my packages two posts up if it helps...

---

### Post by jonesy on 2005-10-18
The only thing I can think of for screensavers is if the GLX components are not being properly installed or there are permission problems with the nvidia device entries.  As your user, can you type "glxinfo" in a terminal window?  At the top, it should say that direct rendering is enabled and then list a whole bunch of other useless crap.  The lines to pay attention to are:

display: :0  screen: 0
direct rendering: Yes
server glx vendor string: NVIDIA Corporation
server glx version string: 1.3
server glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_SGIX_fbconfig,
    GLX_SGIX_pbuffer, GLX_SGI_video_sync, GLX_SGI_swap_control,
    GLX_ARB_multisample, GLX_NV_float_buffer
client glx vendor string: NVIDIA Corporation
client glx version string: 1.3
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_visual_info,
    GLX_EXT_visual_rating, GLX_EXT_import_context, GLX_SGI_video_sync,
    GLX_NV_swap_group, GLX_NV_video_out, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer,
    GLX_SGI_swap_control, GLX_NV_float_buffer, GLX_ARB_fbconfig_float
GLX version: 1.3
GLX extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_SGIX_fbconfig,
    GLX_SGIX_pbuffer, GLX_SGI_video_sync, GLX_SGI_swap_control,
    GLX_ARB_multisample, GLX_NV_float_buffer, GLX_ARB_get_proc_address
OpenGL vendor string: NVIDIA Corporation
OpenGL renderer string: GeForce FX 5500/PCI/SSE2
OpenGL version string: 2.0.0 NVIDIA 76.67

Note that the direct rendering is enabled and the OpenGL version string is 2.0.0 NVIDIA 76.67.  Those lines indicate that the driver is properly installed and enabled.

---

### Post by nrwilk on 2005-10-18
> display: :0 screen: 0 direct rendering: Yes server glx vendor string: NVIDIA Corporation server glx version string: 1.3 server glx extensions: GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, GLX_SGI_video_sync, GLX_SGI_swap_control, GLX_ARB_multisample, GLX_NV_float_buffer client glx vendor string: NVIDIA Corporation client glx version string: 1.3 client glx extensions: GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context, GLX_SGI_video_sync, GLX_NV_swap_group, GLX_NV_video_out, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, GLX_SGI_swap_control, GLX_NV_float_buffer, GLX_ARB_fbconfig_float GLX version: 1.3 GLX extensions: GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, GLX_SGI_video_sync, GLX_SGI_swap_control, GLX_ARB_multisample, GLX_NV_float_buffer, GLX_ARB_get_proc_address OpenGL vendor string: NVIDIA Corporation OpenGL renderer string: GeForce FX 5500/PCI/SSE2 OpenGL version string: 2.0.0 NVIDIA 76.67 My output from glxinfo is almost identical: > direct rendering: Yes server glx vendor string: NVIDIA Corporation server glx version string: 1.3 server glx extensions: GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, GLX_SGI_video_sync, GLX_SGI_swap_control, GLX_ARB_multisample, GLX_NV_float_buffer, GLX_ARB_fbconfig_float client glx vendor string: NVIDIA Corporation client glx version string: 1.3 client glx extensions: GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context, GLX_SGI_video_sync, GLX_NV_swap_group, GLX_NV_video_out, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, GLX_SGI_swap_control, GLX_NV_float_buffer, GLX_ARB_fbconfig_float GLX version: 1.3 GLX extensions: GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, GLX_SGI_video_sync, GLX_SGI_swap_control, GLX_ARB_multisample, GLX_NV_float_buffer, GLX_ARB_fbconfig_float, GLX_ARB_get_proc_address OpenGL vendor string: NVIDIA Corporation OpenGL renderer string: GeForce 6600/PCI/SSE2/3DNOW! OpenGL version string: 2.0.0 NVIDIA 76.67  

Gah! Those got all garbled, sorry! 

Another difference between now and before is that each screensaver used to at least display a preview in the tiny preview box inside the kcontrol window, but the screensavers themselves wouldn't work full-screen. Now those tiny previews are blank too. Ok, I got the previews back by somehow juggling the packages in Adept, but they still do not display when I hit the "test" button. I found out, though, that if I set a certain screensaver to run after a certain amount of idle time, it will. It won't run when I test it, but it will run when it automatically turns on. Is this common? Is this how it is for everyone? 

Secondly, when people use Gears(GL) to sort of benchmark their graphic performance, are they running it full-screen? Or are they getting that FPS value from the little preview window? Because people with a similar setup to me have FPS rates in Gears(GL) of about ~4000-5000 and I get that in the tiny preview, but when it's running full-screen, I get ~350 average. 

Thirdly, it seems people run the command ```
$ glxgears
``` in order to get the benchmark values. This opens a small window for me, but I get no FPS output. How can I get it to output my FPS? Thank you! EDIT: found the correct option : ```
$ glxgears -iacknowledgethatthistoolisnotabenchmark
``` or ```
$ glxgears -printfps
```

---

### Post by jonesy on 2005-10-18
i usually run glxgears from the command prompt in which case usually it just outputs the fps to the terminal window.  As far as screensavers are concerned, i'm using NVIDIA, always have, on several systems, and i've never seen problems with the screen savers like you are describing.  Sorry I can't be of more help.  Does it exhibit the same behavior in gnome?

---

### Post by nrwilk on 2005-10-18
[QUOTE=jonesy]i usually run glxgears from the command prompt in which case usually it just outputs the fps to the terminal window.  As far as screensavers are concerned, i'm using NVIDIA, always have, on several systems, and i've never seen problems with the screen savers like you are describing.  Sorry I can't be of more help.  Does it exhibit the same behavior in gnome?[/QUOTE]

I can deal with it, I'd just like it all to run as smoothly as possible.

But, I am happy with my FPS scores when running glxgears -printfps:

```
$ glxgears -printfps
19981 frames in 5.0 seconds = 3996.131 FPS
19988 frames in 5.0 seconds = 3997.592 FPS
20008 frames in 5.0 seconds = 4001.429 FPS
19938 frames in 5.0 seconds = 3987.533 FPS
```

I think that's pretty good, right?

---

### Post by jonesy on 2005-10-18
Compared to the 1400 i'm getting, yeah, it's good.

---

