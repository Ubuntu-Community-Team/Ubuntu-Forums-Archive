---
title: "Can't enable proprietary nVidia drivers"
date: 2013-03-11
forum: Gaming &amp; Leisure
---

### Post by Number3124 on 2013-03-11
Hello,

I've recently tried to install Steam to give gaming on Linux a shot. I'm running Ubuntu 12.10 with MATE 1.4.2 with the Linux 3.5.0-25-generic kernel on an unmodified Samsung RC512. It has an interlaced Intel i7 2630QM clocked at 2.00 GHz, an nVidia GT 525M, and 6 GB of DDR3 RAM. The problem I've been running into is that I'm unable to enable third party nVidia drivers for my GT 525M. I've run:

```
sudo apt-add-repository ppa:xorg-edgers/ppa

sudo apt-get update

sudo apt-get install nvidia-current nvidia-settings
```

to attempt to set up the proprietary drivers. Unfortunately, they don't show up in the, "Additional Drivers," section in Software Sources. When I attempt to start Steam and Marathon (which I've enabled all of the advanced options) in the terminal it returns the following:

```
RC512:~$ steam
Running Steam on ubuntu 12.10 64-bit
STEAM_RUNTIME is enabled automatically
Installing breakpad exception handler for appid(steam)/version(1361807486_client)
Xlib:  extension "GLX" missing on display ":0.0".
Installing breakpad exception handler for appid(steam)/version(1361807486_client)
Installing breakpad exception handler for appid(steam)/version(1361807486_client)
unlinked 0 orphaned pipes
Xlib:  extension "GLX" missing on display ":0.0".
OpenGL GLX extension not supported by displayRC512
```

```
RC512:~$ steam steam
Running Steam on ubuntu 12.10 64-bit
STEAM_RUNTIME is enabled automatically
Installing breakpad exception handler for appid(steam)/version(1361807486_client)
Xlib:  extension "GLX" missing on display ":0.0".
Installing breakpad exception handler for appid(steam)/version(1361807486_client)
Installing breakpad exception handler for appid(steam)/version(1361807486_client)
unlinked 0 orphaned pipes
removing stale semaphore last operated on by process 3302 with name 0eBlobRegistryMutex_C77663B442E7EE0C79F501D8533673E5
removing stale semaphore last operated on by process 3302 with name 0eBlobRegistrySignal_C77663B442E7EE0C79F501D8533673E5
removing stale semaphore last operated on by process 3302 with name 0emSteamEngineInstance
removing stale semaphore last operated on by process 3302 with name 0eSteamEngineLock
Xlib:  extension "GLX" missing on display ":0.0".
OpenGL GLX extension not supported by displayRC512
```

```
RC512:~$ marathon
Aleph One Linux 2012-01-28 1.0.1
http://marathon.sourceforge.net/

Original code by Bungie Software <http://www.bungie.com/>
Additional work by Loren Petrich, Chris Pruett, Rhys Hill et al.
TCP/IP networking by Woody Zenfell
Expat XML library by James Clark
SDL port by Christian Bauer <Christian.Bauer@uni-mainz.de>

This is free software with ABSOLUTELY NO WARRANTY.
You are welcome to redistribute it under certain conditions.
For details, see the file COPYING.

Built with network play enabled.

Built with Lua scripting enabled.
Can't open video display (Couldn't find matching GLX visual)
WARNING: Failed to initialize OpenGL with 24 bit colour
WARNING: Retrying with 16 bit colour
Can't open video display (Couldn't find matching GLX visual)

```

I hope someone can help me figure out how to enable the proprietary nVidia drivers which support OpenGL and 3D. Thanks in advance.

---

### Post by ZarathustraDK on 2013-03-12
Have you tried installing the driver manually from [http://www.nvidia.co.uk/Download/Find.aspx?lang=en-uk](http://www.nvidia.co.uk/Download/Find.aspx?lang=en-uk) ?


1. Download the driver
2. CTRL-ALT+F3 to drop to a command line. Print this post, or have another pc running with it, because you wont be able to switch back before the driver is installed again.
3. ```
sudo service lightdm stop
``` The above stops your current graphical session, allowing you to install the blob
4. ```
sudo apt-get purge nvidia*
``` The above gets rid of all the nvidia-stuff you've installed so far
5. ```
sudo apt-get install build-essential linux-headers-`uname -r`
``` The above installs the necessary components to run the blob succesfully
6. Change directory to the place where you downloaded the driver to, usually /home/yourname/Downloads or just /home/yourname/ ("cd" and "ls" are your friends here)
7. Run ```
chmod -x NameOfTheDriverYouDownloaded
``` The above makes it executable. Remember if you write part of the name correctly and press TAB it'll autocomplete the name.
8. Run ```
./NameOfTheDriverYouDownloaded
``` The above will run it
9. Follow the onscreen instructions, say yes/accept to everything EXCEPT the part mentioning KMS, it doesn't work and may bork your system, so say no to that part. It concerns auto-updating the driver when you update your kernel, so you'll have to do this all over again if you upgrade the kernel, which is a good reason to always have your nvidia-driver downloaded (in case you forget it, upgrade the kernel and reboot into a commandprompt).
10. After it's done do: ```
sudo service lightdm start
``` and you're rolling, probably in a strange resolution but that can be changed.

I saw a script for all this somewhere, but can't remember where I found it :-/
Again, it's a VERY healthy excercise to memorize this procedure. Kernel-upgrades WILL happen, and you'll be stuck at the commandprompt. So ALWAYS keep an Nvidia-driver in some folder you know how to get to with the CLI.

NB. if someone has a workaround for the KMS-thing I'd be interested :)

---

