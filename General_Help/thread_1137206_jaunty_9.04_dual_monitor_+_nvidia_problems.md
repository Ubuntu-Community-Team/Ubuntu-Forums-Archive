---
title: "jaunty 9.04 dual monitor + nvidia problems"
date: 2009-04-25
forum: General Help
---

### Post by Davidux on 2009-04-25
Hello, I've just installed Jaunty and I have a couple of problems in setting up the dual monitor with separate x screens. I have a nvidia 8800gt card and i'm using the 64-bit version of linux. 

1) mouse cursor persisting on screen when moving from one screen to the other (it seems that there is already an open bug on this)
2) with 180 drivers and compiz on, there is a black vertical band on the right of secondary screen that cover the desktop; with the old drivers 173 this doesn't happen
3) this is the most annoying: when i open an application on the secondary screen it opens on the primary one, and of course it's not possible to move it since the desktop session are separated.

Before I used Ubuntu 8.04 and I never had these problems...
Does somebody have a solution, at least for point 3)?

---

### Post by jmvw on 2009-04-26
Hello,

You have a separate X screen set up. Go into the nvidia-settings  (you may want to start this from a terminal with sudo nvidia-settings) and change the configuration for the second monitor from separate X screen to Twinview. Save to the xorg.conf file and restart X (sudo killall -s HUP gdm)

Good luck.

---

### Post by Davidux on 2009-04-26
Thanks, I know twinview works (I've already tried it), but still it's strange that in Ubuntu 8.04 the separated X screens were working and now they're not working any more. Maybe is there a bug somewhere?

---

### Post by fooman on 2009-04-26
> **Davidux said:**
> Before I used Ubuntu 8.04 and I never had these problems...
Does somebody have a solution, at least for point 3)?

for point #3...open a terminal on the secondary screen and start the app from there.  

if you cannot get to a terminal on that screen, try installing "nautilus-open-terminal"...that will give you the ability to right-click on the secondary screen's desktop (or anywhere in nautilus) and choose "open in terminal" from the context menu.  

to install it....open a terminal on the main screen and run this command:

```
sudo apt-get install nautilus-open-terminal
```after it installs,  log-out and back in again.  when you get back to the desktops,  you should be able to right-click on screen 2,  choose "open in terminal" and open the app from there...it should then open on screen 2.

hope that helps.

---

### Post by thexravenx on 2009-04-27
I actually have the same problem with where the application loads. I have two twinview set up on two video cards: 2 montiors for each twinview. 

Certain applications like firefox will load in the second x screen. However most will only load in the primary x screen. I have tried using separate x screens for each monitor and the same issue occurs. 

So far I have tested the following applications:
calc
archive manager
TSclient
opening home folder from menu

All of these load only in the primary.

Firefox and open office do load in the secondary x screen from the menu.

---

### Post by Davidux on 2009-04-27
> **fooman said:**
> for point #3...open a terminal on the secondary screen and start the app from there.

Thanks, it surely helps until there is a solution from the development team :)

---

### Post by Davidux on 2009-04-27
> **thexravenx said:**
> I actually have the same problem with where the application loads. I have two twinview set up on two video cards: 2 montiors for each twinview. 

Certain applications like firefox will load in the second x screen. However most will only load in the primary x screen. I have tried using separate x screens for each monitor and the same issue occurs. 

So far I have tested the following applications:
calc
archive manager
TSclient
opening home folder from menu

All of these load only in the primary.

Firefox and open office do load in the secondary x screen from the menu.

i can confirm... most of the applications open only on screen one; firefox and office work fine

---

### Post by Psykotik on 2009-04-27
[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-180/+bug/339783](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-180/+bug/339783)

---

### Post by Davidux on 2009-04-28
> **Psykotik said:**
> [https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-180/+bug/339783](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-180/+bug/339783)

Thanks, I'll start following the bug thread from now on. I did not find it before.

---

### Post by luceat on 2009-04-30
I noticed setting my TV's resolution to the same as the desktop solved both "black border" overlapping and the unability to move the mouse between the windows.

I set the screens both in nvidia-settings and gnome-display-preferences. gnome-display-stetings first, which didn't seem  to do anything.

Damn annoying bug, I wanna play EVE on my TV in HD-resolution :<

---

### Post by gupi-gupi on 2009-05-03
I'm in the same situation, the bug affects only with compiz running, I noticed in intrepid that the bug started with version 177 of NVIDIA driver, while 173 is not affected, bu I could not install the 173 in jaunty so far :( (tried from repo, but it's not working, even though I have to say I'm an an intrepid upgrade to jaunty, and not on a fresh install) and aslo tried the version 173 downloaded from nvidia site, but it's not compiling. Only driver working so far is 180 from nvidia site.

---

### Post by Davidux on 2009-05-04
> **gupi-gupi said:**
> I'm in the same situation, the bug affects only with compiz running, I noticed in intrepid that the bug started with version 177 of NVIDIA driver, while 173 is not affected, bu I could not install the 173 in jaunty so far :( (tried from repo, but it's not working, even though I have to say I'm an an intrepid upgrade to jaunty, and not on a fresh install) and aslo tried the version 173 downloaded from nvidia site, but it's not compiling. Only driver working so far is 180 from nvidia site.

With a fresh install you can choose between v180 and v173 driver in the hardware drivers application

---

### Post by Davidux on 2009-05-04
> **luceat said:**
> I noticed setting my TV's resolution to the same as the desktop solved both "black border" overlapping and the unability to move the mouse between the windows.

I set the screens both in nvidia-settings and gnome-display-preferences. gnome-display-stetings first, which didn't seem  to do anything.

Damn annoying bug, I wanna play EVE on my TV in HD-resolution :<

good to know. maybe you should report it in the relative bug (if there is one open) - sorry but at the moment i don't have time to look for it...
unfortunately for me, one of my screens is 4:3 and the other one is 16:9 :(

---

### Post by dotelpenguin on 2009-05-05
I can confirm this bug, I have the same problem.  With the addition of random mouse restraints.   Both monitors will show up, but applications will only open on one.  If I move one to other monitor, my mouse will be confined to a smaller area of my primary monitor, no longer able to move to second screen if I drop to console and kill app My mouse will return to normal.

01:00.0 VGA compatible controller: nVidia Corporation GeForce 7100 GS (rev a1)
8.04 -> 9.04 upgrade. 
Nvidia v180.

---

### Post by Davidux on 2009-05-06
guys, keep an eye on this bug on bugzilla

[Bug 580103 – Terminal starts on Display :0.0 when started on :0.1 in Dual screen conf]("http://bugzilla.gnome.org/show_bug.cgi?id=580103")

---

### Post by adei222 on 2009-05-06
> **fooman said:**
> for point #3...open a terminal on the secondary screen and start the app from there.  

if you cannot get to a terminal on that screen, try installing "nautilus-open-terminal"...that will give you the ability to right-click on the secondary screen's desktop (or anywhere in nautilus) and choose "open in terminal" from the context menu.  

to install it....open a terminal on the main screen and run this command:

```
sudo apt-get install nautilus-open-terminal
```after it installs,  log-out and back in again.  when you get back to the desktops,  you should be able to right-click on screen 2,  choose "open in terminal" and open the app from there...it should then open on screen 2.

hope that helps.

partially solved this; thanks XD

---

### Post by tomski on 2009-05-06
OFF TOPIC QUESTION:
Why use two seperate X screens?
What are the benifits of this over twinview?

appologies for this davidux
please feel free to prv msg me the answer rather than post here

---

### Post by Davidux on 2009-05-07
OFF TOPIC ANSWER :)

> **tomski said:**
> OFF TOPIC QUESTION:
Why use two separate X screens?
What are the benefits of this over twinview?

apologies for this davidux
please feel free to prv msg me the answer rather than post here

From what I understood, with twin view you have a bigger squared desktop, but if the monitors have different resolutions you cannot cover it completely and the result is a bit ugly (this is my opinion of course). I like more to have two different x sessions, one for each monitor, and each one in the native resolution; consider that I use this configuration at home and the second screen is a big lcd tv to watch movies. I think also that you can configure the two x session separately if you need it for some reason. Not sure 100% though, I've never tried.

---

### Post by ctrlER on 2009-05-07
I use the same config. I solved the third problem by executing an aplication with DISPLAY=:0.<x> <application> in a terminal. The value of <x> is 0 or 1. That way I can chose the screen where I want to run the app.

---

### Post by Bubazio on 2009-05-13
I have the same problem...
Fixed using envyng and installing driver version 173 instead of 180.

---

### Post by gupi-gupi on 2009-05-13
how did you install them? from repo or from NVIDIA site ? because I tried both and could not manage to install them. Did you follow some guide?

edit:
I tried 173 from repo via the restricted driver applet, did not work, hanged at log in prompt, no way to access the ctrl f2 shell

tried 185 beta from NVIDIA site, they compiled but did not resolve the bugs, so I guess we will have the same stuff going on on  the 185.xx new driver

tried the 173 driver from Nvidia site, NVIDIA-Linux-x86-173.08-pkg1.run did not even start the compile, a checksum error, the NVIDIA-Linux-x86-173.14.18-pkg1.run started to compile, but after disinstallation of previous driver failed the installation, > nvidia-installer log file '/var/log/nvidia-installer.log'
creation time: Wed May 13 12:31:21 2009

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
-> There appears to already be a driver installed on your system (version: 185.
   18.08).  As part of installing this driver (version: 173.08), the existing d
   river will be uninstalled.  Are you sure you want to continue? ('no' will ab
   ort installation) (Answer: Yes)
-> No precompiled kernel interface was found to match your kernel; would you li
   ke the installer to attempt to download a kernel interface for your kernel f
   rom the NVIDIA ftp site ([ftp://download.nvidia.com)?](ftp://download.nvidia.com)?) (Answer: No)
-> No precompiled kernel interface was found to match your kernel; this means
   that the installer will need to compile a new kernel interface.
-> Performing CC sanity check with CC="cc".
-> Performing CC version check with CC="cc".
-> Kernel source path: '/lib/modules/2.6.28-11-generic/build'
-> Kernel output path: '/lib/modules/2.6.28-11-generic/build'
ERROR: If you are using a Linux 2.4 kernel, please make sure
       you either have configured kernel sources matching your
       kernel or the correct set of kernel headers installed
       on your system.
       
       If you are using a Linux 2.6 kernel, please make sure
       you have configured kernel sources matching your kernel
       installed on your system. If you specified a separate
       output directory using either the "KBUILD_OUTPUT" or
       the "O" KBUILD parameter, make sure to specify this
       directory with the SYSOUT environment variable or with
       the equivalent nvidia-installer command line option.
       
       Depending on where and how the kernel sources (or the
       kernel headers) were installed, you may need to specify
       their location with the SYSSRC environment variable or
       the equivalent nvidia-installer command line option.
ERROR: Installation has failed.  Please see the file
       '/var/log/nvidia-installer.log' for details.  You may find suggestions
       on fixing installation problems in the README available on the Linux
       driver download page at [www.nvidia.com](www.nvidia.com). 

only working one for me is 180 from repo

---

### Post by minijoe on 2009-05-18
> **Bubazio said:**
> I have the same problem...
Fixed using envyng and installing driver version 173 instead of 180.

Thanks Bubazio for mentioning the driver roll-back solution. This did solve my problem as mentioned in this thread. However I did it from "Hardware Drivers Manager" to Remove 180 then Active 173.

It seems there's some compatibility issue between Jaunty/Gnome and Nvidia V.180 driver.

I have a sony notebook with nvidia chip when using 180 driver watching hulu.com it lagged a bit after roll-back to 173 driver all went well.

---

### Post by phirana on 2009-05-26
Hi there,

My problem is kind of the same. I have 3 monitors. Two on dual screen and the other on seperate X.

The dual screen works perfectly, but the other monitor launches most programs in the dual screen monitors. Also, compize fusion runs extremely slow and therefore have to disable it.

This all worked perfectly on 8.10. I have tried the solutions but to no avail - any more ideas?

thanks

---

### Post by theShaggy on 2009-06-01
The dual-screen Gnome bug from a page back appears to have a patch to GLib2.0 attached.  Anybody tried/does it work/how would I go about patching the lib if it does?

---

### Post by NT4usB on 2009-06-03
more info, if anyone's listening.
I recently upgraded from Hardy to Jaunty. Formatted and installed / but kept /home.
Way back when, I created a keybord shortcut to launch terminal. It still works to launch a terminal in whatever screen I'm in.
Otherwise, apps all launch in screen0.

---

### Post by Tristan Schmelcher on 2009-06-07
theShaggy: I tried the patch and it does work. The howto at [http://www.cyberciti.biz/faq/rebuilding-ubuntu-debian-linux-binary-package/](http://www.cyberciti.biz/faq/rebuilding-ubuntu-debian-linux-binary-package/) describes how to build your own version of the package (for "foo", you want "libglib2.0-0"). To incorporate the patch file, use the "patch" command before the dpkg-buildpackage step.

---

### Post by Tristan Schmelcher on 2009-06-07
Hey, I'm running in a separate X screen config and I have another problem: my main mouse (Synaptics Touchpad) cannot move to the secondary screen. Only my external mouse can (Logitech MX Revolution). Which is really bizarre considering that they share the same pointer on screen. If I'm using the external mouse, I can move between screens freely. But if I'm using the touchpad then I'm confined to the primary screen! And the even crazier thing is that if I use the external mouse to move the pointer to the secondary screen, then the touchpad _will_ work on that screen, but if I move it back to the primary screen then it's stuck there again.

Anyone else have this problem? I noticed that someone else said it happens when the monitor resolutions don't match, and mine don't; the primary is 1920x1200 and the secondary is 1920x1080. But I can't make them match because they're different aspect ratios.

---

### Post by Ullrotta on 2009-06-08
I have the exact same problems

* Applications opening on primary only - now even Firefox won't open on secondary
* Pointer stuck on each side of dual screen
* Mousepad will not move pointer from primary to secondary, only from secondary to primary
* Black banner across lower part of secondary screen

I can't believe how long it has taken to sort this bug out. I'm moving back to 8.10 until this is fixed.

Peas!


Edit:  I downgraded to nvidia driver 173, and that took care of the black banner and Firefox opening on the wrong screen. For some of the other stuff I need on the secondary screen I've added (thanks to some other forum thread) bash -c to the command line of the panel icon. That seems to work ok.

---

### Post by misja on 2009-06-10
I'm having the same problem. I upgraded from 8.04 and now I have the problem that my mouse pointer is sometimes confined to one monitor.
I'm using 2 monitors and both have the same resolution.

I tried reverting to Nvidia's 1.73 driver from the Hardware Drivers dialog but got an error dialog without any message every time ..

---

### Post by foxprobe on 2009-06-11
> **misja said:**
> I tried reverting to Nvidia's 1.73 driver from the Hardware Drivers dialog but got an error dialog without any message every time ..
 
This dual screen bug (i have the same) is not due to the driver. I have trying the 173, 180, 185 with the same result (and with some other bugs in addition, for the 185 driver).
 
It seem to be a gnome bug [http://bugzilla.gnome.org/show_bug.cgi?id=580103](http://bugzilla.gnome.org/show_bug.cgi?id=580103)
and was marked as *invalid->triaged* on the lauchpad. [https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-180/+bug/339783](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-180/+bug/339783)

---

### Post by Jukums on 2009-07-13
On the mouse problem:

Using dual screens (nVidia/separate screens ... 0 - laptop's 1 - external), mouse gets stuck on screen 1, but can't move it back unless I do it with usb mouse, in that case it works all good, but not if I use laptop's touch-pad, then mouse get's stuck on external screen

---

### Post by Tristan Schmelcher on 2009-07-13
Jukums:

I've got the same problem, except it gets stuck on the primary screen for me. I think I'm gonna file a bug.

---

### Post by tenjin1 on 2009-09-21
> **Davidux said:**
> Hello, I've just installed Jaunty and I have a couple of problems in setting up the dual monitor with separate x screens. I have a nvidia 8800gt card and i'm using the 64-bit version of linux. 

1) mouse cursor persisting on screen when moving from one screen to the other (it seems that there is already an open bug on this)
2) with 180 drivers and compiz on, there is a black vertical band on the right of secondary screen that cover the desktop; with the old drivers 173 this doesn't happen
3) this is the most annoying: when i open an application on the secondary screen it opens on the primary one, and of course it's not possible to move it since the desktop session are separated.

Before I used Ubuntu 8.04 and I never had these problems...
Does somebody have a solution, at least for point 3)?

Well I had the same problem-
Opening an app on Screen1 would launch it on Screen0, whether compiz was activated or not. Thats the only problem I was having was windows were opening on Screen0 instead of Screen1. No problems with black borders or anything,Downgraded to Nvidia driver 173 from 180 with no effect. So it turns out it is a bug in Gnome I believe. I followed the directions at [https://answers.launchpad.net/ubuntu/+source/glib2.0/+question/77380]("https://answers.launchpad.net/ubuntu/+source/glib2.0/+question/77380") and used the patched libglib 2.0-0. It works now! But... if Compiz is activated it does not, so I'm using the Compiz-Fusion icon to turn on and off when I need to. Also I'm still on nvidia driver 173, will update to 180 to see if still working or not.

---

### Post by cromos on 2009-10-26
hi,:) i'm new ubuntu user and i've a problem :(with double monitor becouse i cant' use  the dell 2408 wfp, i posted the screen of nvidia x server, can you help me to solve this problem? Tankyou very much.

[[IMG]http://www.uptiki.com/images/11ajcefz0w8gkgki8ure.png[/IMG]]("http://www.uptiki.com/")

[[IMG]http://www.uptiki.com/images/rgj30ya5z0nv1vmh198l.png[/IMG]]("http://www.uptiki.com/")

---

### Post by acreech on 2009-10-27
Was you wanting this to be a "twin view" so that you can have the left side of the desktop on the left monitor and the right side of the desktop on the right monitor?

I would click on the "configure" button and change it to "Twin View". Then below the resolution you should have a new box there that says "position". Set that to the left. then hit the apply button that is below there. 

That is how I would do it, is that what you are after?

---

