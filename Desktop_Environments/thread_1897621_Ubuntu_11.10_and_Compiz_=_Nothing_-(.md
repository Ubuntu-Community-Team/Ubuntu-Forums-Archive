---
title: "Ubuntu 11.10 and Compiz = Nothing :-("
date: 2011-12-19
forum: Desktop Environments
---

### Post by bicster on 2011-12-19
Hey everyone,

So I'm relatively new to Linux and Ubuntu and am trying to get Compiz configured.

I've managed to install it although when I make changes to the settings in CCSM nothing happens. I don't see any changes to my desktop environment - even if I disable the Unity plugin, nothing happens. It's still there in all its glory.

I know this is a long shot - but does anyone have any ideas what might be going wrong, or what I can do to start investigating the problem?

Many thanks,

Chris

PS I'm running Ubuntu on my Dell Latitude E6420.

---

### Post by BC59 on 2011-12-19
Did you install the proprietary drivers for your Graphic card?

---

### Post by bicster on 2011-12-19
Yeah, I have the drivers installed - screen shot attached.

---

### Post by BC59 on 2011-12-19
Try to reset Unity

```
unity --reset
```

---

### Post by bicster on 2011-12-19
OK, so when I run unity --reset I get the following....

```

chris@chris-Latitude-E6420:~$ unity --reset
Checking if settings need to be migrated ...no
Checking if internal files need to be migrated ...no
Backend     : gconf
Integration : true
Profile     : unity
Adding plugins
Skipping upgrade com.canonical.unity.unity.01.upgrade
Skipping upgrade com.canonical.unity.unity.02.upgrade
Initializing core options...done
Initializing bailer options...done
Initializing detection options...done
Initializing composite options...done
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Compiz (opengl) - Fatal: glXCreateContext failed
Compiz (bailer) - Info: Ensuring a shell for your session
chris@chris-Latitude-E6420:~$ 
(metacity:2130): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(metacity:2130): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(metacity:2130): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(metacity:2130): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",
chris@chris-Latitude-E6420:~$ 
```

Any ideas?

---

### Post by BC59 on 2011-12-19
Then reinstall Unity

```
sudo apt-get purge unity && sudo apt-get install unity
```

---

### Post by sibleytr on 2011-12-19
When Using 10.04 I had a similar problem.

1 - I actually had to restart the system to get Compiz to work
2 - Make sure not to edit your Desktops Visual Effects settings afterward

In regards to #2 - When VNC Remote is used to access the machine sometimes the visual responses do not show up of the client. Looks like your in observe mode instead of control. The resolution is to set the Desktops Visual Effects from Normal to None. Unfortunately this also disable my Compiz.


Never know - always hope for the simple answers.

---

### Post by bicster on 2011-12-19
Ok, so I uninstalled and reinstalled Unity, the output of the command is below...

[FONT="Lucida Console"][B]chris@chris-Latitude-E6420:~$ sudo apt-get purge unity && sudo apt-get install unity
[sudo] password for chris: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  ubuntu-desktop* unity*
0 upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
After this operation, 2,597 kB disk space will be freed.
Do you want to continue [Y/n]? 
(Reading database ... 166944 files and directories currently installed.)
Removing ubuntu-desktop ...
Removing unity ...
Processing triggers for man-db ...
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  unity
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/906 kB of archives.
After this operation, 2,535 kB of additional disk space will be used.
Selecting previously deselected package unity.
(Reading database ... 166920 files and directories currently installed.)
Unpacking unity (from .../unity_4.24.0-0ubuntu2b1_i386.deb) ...
Processing triggers for man-db ...
Setting up unity (4.24.0-0ubuntu2b1) ...
[/B][/FONT]

However, after a reboot, the symptoms are the same?

Is there a similar command to uninstall and reinstall Compiz?

Thanks,

Chris

---

### Post by wildmanne39 on 2011-12-19
Hi, you can not disable the unity plugin and leave it disabled or you will not have the unity desktop, please refer to the second link in my signature for a guide to setting up compiz.
Thanks

---

### Post by bicster on 2011-12-19
Ok, so I'm working through the link and when I get to the....

*"1. Right click on the background, then click on "change desktop background" in the window that opens. Click on "visual effects" then choose "extra" and it will attempt to activate desktop effects."*

...bit, when I click on the Change Desktop Background I get a window open that doesn't have anything resembling 'Visual Effects' (see attached image).

Any ideas?

Chris

---

### Post by wildmanne39 on 2011-12-19
Hi, that part of the guide is for earlier versions of ubuntu, go further down the page and follow the directions for 11.10.
Thanks

---

### Post by ingeva on 2011-12-20
> **wildmanne39 said:**
> Hi, that part of the guide is for earlier versions of ubuntu, go further down the page and follow the directions for 11.10.
Thanks
The configuration settings only work for Unity 3D.

---

### Post by BC59 on 2011-12-20
to reset Compiz:
```
gconftool-2 --recursive-unset /apps/compiz-1 && gconftool-2 --type=list --list-type=string --set /apps/compiz-1/general/screen0/options/active_plugins [core,bailer,detection,composite,opengl,compiztoolbox,decor,grid,move,resize,mousepoll,regex,snap,gnomecompat,place,imgpng,vpswitch,animation,wall,workarounds,fade,session,expo,ezoom,unityshell] && compiz --replace & disown
```
sometimes after running you may still have problems and you need to run this command again
```
compiz --replace & disown
```

---

### Post by wildmanne39 on 2011-12-20
Hi, if you want to know if the settings work for gnome3 no they do not.

I am going to look into what it will take to get effects working in gnome soon.
Thanks

---

### Post by stinkeye on 2011-12-20
> **bicster said:**
>  - even if I *disable* the Unity plugin, nothing happens. It's *still there* in all its glory.


Anyone notice his part of the first post.


What is the output of
```
echo $DESKTOP_SESSION
``` 
and
```
/usr/lib/nux/unity_support_test -p
```

---

### Post by bicster on 2011-12-20
Ok, so the output of those two commands is below....


[B]
chris@chris-Latitude-E6420:~$ echo $DESKTOP_SESSION
ubuntu-2d
chris@chris-Latitude-E6420:~$ /usr/lib/nux/unity_support_test -p
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Segmentation fault
[/B]

Methinks I could have a GLX problem - whatever that is!?!?!

Has anyone seen this before?

---

### Post by stinkeye on 2011-12-20
> **bicster said:**
> Ok, so the output of those two commands is below....


[B]
chris@chris-Latitude-E6420:~$ echo $DESKTOP_SESSION
ubuntu-2d
chris@chris-Latitude-E6420:~$ /usr/lib/nux/unity_support_test -p
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Segmentation fault
[/B]

Methinks I could have a GLX problem - whatever that is!?!?!

Has anyone seen this before?
Not really adept at solving gfx issues but the output of this command 
may be helpful to others.
```
lspci -k | grep -A3 VGA
```

Also did a quick search on Latitude-E6420 and did you know you can download a Dell-Ubuntu 10.10 iso from dell.
 [**_[COLOR="DarkRed"]ubuntu-10.10-i386-dell_A00.iso[/COLOR]_**]("http://www.dell.com/support/drivers/us/en/04/DriverDetails/DriverFileFormats?DriverId=YFYVX&FileId=2731097728")

---

### Post by wildmanne39 on 2011-12-20
Posted in wrong thread.

---

### Post by wildmanne39 on 2011-12-20
Hi, it appears the error messages are caused by a driver issue here is a link for it.
[http://ubuntuforums.org/showthread.php?t=1741783](http://ubuntuforums.org/showthread.php?t=1741783)

You can also google the message and add ubuntu like I did and get many more results and some fixes for it, but you might try reinstalling your video card driver first.
Thanks

---

### Post by bicster on 2011-12-21
OK, so I think we're on to something with the driver issue - although it could be because I have two graphics cards (which was news to me!).

I discovered this by running the command provided earlier....

[B]chris@chris-Latitude-E6420:~$ sudo lspci -k | grep -A3 VGA
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
    Subsystem: Dell Device 0493
    Kernel driver in use: i915
    Kernel modules: i915
--
01:00.0 VGA compatible controller: nVidia Corporation GF108 [Quadro NVS 4200M] (rev a1)
    Subsystem: Dell Device 1493
    Kernel driver in use: nvidia
    Kernel modules: nouveau, nvidiafb[/B]

...so I think this is what's causing the problem, how can I disable the Intel one?

Thanks,

Chris

---

### Post by wildmanne39 on 2011-12-21
Hi, before we disable intel open additional drivers and deactivate the nouveau driver and install the nvidia driver for your card, it will require a reboot.
Thanks

---

### Post by bicster on 2011-12-21
A reboot is fine, but how do we do the above??

---

### Post by wildmanne39 on 2011-12-21
Hi, open dash type additional drivers deactivate nouveau, there should be a nvidia driver in additional drivers if so activate it if not let me know.

According to the information I read the nouveau driver does not have 3d support yet.
Thanks

---

### Post by BlastXng on 2012-01-17
> **bicster said:**
> OK, so I think we're on to something with the driver issue - although it could be because I have two graphics cards (which was news to me!).

I discovered this by running the command provided earlier....

[B]chris@chris-Latitude-E6420:~$ sudo lspci -k | grep -A3 VGA
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
    Subsystem: Dell Device 0493
    Kernel driver in use: i915
    Kernel modules: i915
--
01:00.0 VGA compatible controller: nVidia Corporation GF108 [Quadro NVS 4200M] (rev a1)
    Subsystem: Dell Device 1493
    Kernel driver in use: nvidia
    Kernel modules: nouveau, nvidiafb[/B]

...so I think this is what's causing the problem, how can I disable the Intel one?

Thanks,

Chris

You can disable the Intel Graphics cards in BIOS boot.. I have a Dell E6420 also.. It's a bit of a pain with Ubuntu due to the dual graphics set-up.. 

Boot the laptop, then hit F12 to go into BIOS set-up. In "Video" in BIOS Set-up turn off "Optimus" and this will have your laptop only use the NVIDIA 4200.

---

### Post by bicster on 2012-01-17
Yep, that's what I did, although I still can't get the cube to work....I don't really get any symptoms it just doesn't work!

Have you managed to sort it out?

Chris

---

### Post by wildmanne39 on 2012-01-17
Hi, did you do what I suggested in my last post? also post the results of:
```
lspci | grep VGA
```
```
/usr/lib/nux/unity_support_test -p
```
are you logging into unity 3d or is it 2d? 
or are you using gnome shell?
Thanks

---

### Post by tarkaran on 2012-04-03
I have the same problem. This is the output of those commands:


hector@hector-N53SN:~$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
01:00.0 VGA compatible controller: nVidia Corporation Device 0df6 (rev a1)
hector@hector-N53SN:~$ 
hector@hector-N53SN:~$ /usr/lib/nux/unity_support_test -p
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Segmentation fault

I have an ASUS N53S with the NVIDIA Geforce GT 550M Cuda

It's weird. It tells me that I'm running Unity 2d, but I see some of the icons and features from Unity. Compiz is installed but it's not running. <super>S is working but different, <super>w is not working.

---

