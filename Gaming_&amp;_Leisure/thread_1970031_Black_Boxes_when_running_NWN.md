---
title: "Black Boxes when running NWN"
date: 2012-04-30
forum: Gaming &amp; Leisure
---

### Post by Kazyyk on 2012-04-30
I've successfully installed NWN Diamond Edition without any problems. Thing is, there are splotches of black boxes all throughout the display. Some flicker. Some don't. All in all, I can't figure out what's causing them or how to remove them.

Currently using Ubuntu 12.04 Precise Pangolin (64bit) on a MacbookPro 7,1
Any help would be greatly appreciated.

EDIT: Solution is at the end of this thread.

---

### Post by Kazyyk on 2012-04-30
Installed some nVidia drivers for 64bit Ubuntu to see if it'd help, but it seems to have only made things worse. For the mean time, nouveau is disable, however it might be better to re-enable it. (yet I'm unsure how. Simply removing the file in the etc/modprobe.d folder causes a very low resolution to occur on bootup)

With the nVidia drivers in place, and nouveau disable, I get this error when trying to run the game via ./nwn command.

```
./nwmain: error while loading shared libraries: libGL.so.1: wrong ELF class: ELFCLASS64

```

EDIT: After doing everything mentioned in the thread, I've fixed this error by simply installing the nvidia current package from the Software center. A new error presented itself:

```
 ./nwmain: error while loading shared libraries: libmss.so.6: cannot open shared object file: No such file or directory

```

I'm hopeful that this one will be much easier to fix!
I'm sure that libGL somehow relates to nouveau, but I'm currently at an impass. Any help would be greatly appreciated.

---

### Post by regor210 on 2012-04-30
Just for kicks try starting NWN using linux32, forcing the game to think its on a 32bit OS.

$ linux32 ./nwmain
 
If still no luck run these  

$ sudo apt-get install mesa-utils

# video driver 3D test FPS
$ glxgears

#video card and driver information
$ lspci -vmk | grep -A 8 -B 2 VGA

And post what you get.

---

### Post by Kazyyk on 2012-04-30
Slowly but surely I believe I'm making progress. This information could be useful. It's apparent that several lib related files are missing. Just posting data for any future individual who stumbles across this thread.

```
	linux-gate.so.1 =>  (0xf7745000)
	libm.so.6 => /lib/i386-linux-gnu/libm.so.6 (0xf76fe000)
	libpthread.so.0 => /lib/i386-linux-gnu/libpthread.so.0 (0xf76e3000)
	libGL.so.1 => not found
	libGLU.so.1 => /usr/lib/i386-linux-gnu/libGLU.so.1 (0xf766d000)
	libmss.so.6 => not found
	libSDL-1.2.so.0 => /usr/lib/i386-linux-gnu/libSDL-1.2.so.0 (0xf75d2000)
	libc.so.6 => /lib/i386-linux-gnu/libc.so.6 (0xf742d000)
	/lib/ld-linux.so.2 (0xf7746000)
	libGL.so.1 => not found
	libstdc++.so.6 => /usr/lib/i386-linux-gnu/libstdc++.so.6 (0xf7347000)
	#Everything from this point on had a valid directory.

```

---

### Post by Kazyyk on 2012-04-30
> **regor210 said:**
> 
$ linux32 ./nwmain

No luck here, same error.
> **regor210 said:**
> 
$ sudo apt-get install mesa-utils

It's already installed, newest version, it seems.
> **regor210 said:**
> 
# video driver 3D test FPS
$ glxgears


The gears are spinning steadily. Here's the first three lines that appear as a result.

```
16929 frames in 5.0 seconds = 3385.702 FPS
18128 frames in 5.0 seconds = 3625.517 FPS
16577 frames in 5.0 seconds = 3315.350 FPS

```

> **regor210 said:**
> 
$ lspci -vmk | grep -A 8 -B 2 VGA


This is what it gave me.

```
Device:	04:00.0
Class:	VGA compatible controller
Vendor:	NVIDIA Corporation
Device:	Device 08a0
SVendor:	Apple Inc.
SDevice:	Device 00c2
Rev:	a2
Driver:	nvidia
Module:	nvidia
Module:	nouveau

```

---

### Post by Kazyyk on 2012-05-01
Excuse the multiple replies, but I thought this thread might be of use. I've been digging through Humble Bundle games myself to no avail, being unable to find a lib file within them. 

[http://goo.gl/cAXWs](http://goo.gl/cAXWs)

I've installed ia32-libs successfully, however. Which seems to not have made a difference at all.

---

### Post by regor210 on 2012-05-01
Your not the only one having issues with libs like linux-gate.so.1

I run NWN using wine. I had to rename the movies folder to movies1 to disable them but other than that NWN works fine.

---

### Post by Kazyyk on 2012-05-01
I'm really hoping to find a way to run it natively.
I'll keep digging for a few more days to see what I can come up with, but otherwise I'll resort to Wine. Thanks anyways!

EDIT: I've been digging around in trying to get the nVidia drivers properly installed. (As I suspect I may have done it incorrectly)
In the end, I only encountered more issues. I've had to fix Grub, as it doesn't appear. Once Grub is repaired, I'm going to try and run code that'll hopefully purge the old drivers and update them properly from a repository (of which I currently cannot recall at the moment.)

EDIT2: Grub successfully repaired. Still unable to uninstall the drivers, though, through recovery. Claims the directory does not exist when I attempt to run the install script with --uninstall appended to the end. Instead, opting to install drivers through the Software Center. I'll report back later.

---

### Post by Kazyyk on 2012-05-02
Issue solved!

After performing everything in this thread, and encountering the file not found error for libmss.so.6, I found that the solution for that error was quite simply.

Open up the 'nwn' file in the nwn directory (not nwn.ini) and remove ./lib from "export LD_LIBRARY_PATH=:./lib./miles:$LD_LIBRARY_PATH" and save.

NwN should now run, however, without sound.
With one problem out, a new one arises.
I'll see what I can find.

EDIT: Haha, it's my fault. I had the wrong output selected under sound settings. I'll compose a full guide for graphical error with nwn when I get home later today.

---

### Post by Kazyyk on 2012-05-02
Notice: What works for me, may not work for you.

Alright. If you experience graphical errors while running NwN on a Macbook (I assume this will work for most Macbooks) with an nVidia card, then this might help you.

Simply installed the nVidia current drivers from  the Software Center (Ubuntu 12.04) and let that install.
You may need to disable nouveau, if it hasn't done it itself, which you can do by placing a configuration file in /etc/modprobe.d which should have the following inside.

```
 blacklist nouveau
options nouveau modeset=0 
```

Afterwards, I reccomend grabbing ia32-libs.

```
 sudo apt-get install ia32-libs 
```

Once that's done, a reboot couldn't hurt.

Then simply navigate to your nwn installation folder, which would hopefully be in your home folder, and open the nwn file (not nwn.ini) and remove .lib from the library path. 

(Depending on how you installed it, it should already say within the file how to remove it. If not, here it is: )

```
# If you do not wish to use the SDL library included in the package, remove
# ./lib from LD_LIBRARY_PATH
export LD_LIBRARY_PATH=:[COLOR="Red"]./lib[/COLOR]./miles:$LD_LIBRARY_PATH

export LD_PRELOAD=./nwmovies.so
./nwmain $@
```

If you run into any problems after that, feel free to message me!
I can't guarantee an immediate solution, but I'd be glad to help.

---

### Post by oldrocker99 on 2012-05-03
As a long-time Linux NWN player, (who is quoted, in fact, in that Bioware forum above), may I say that you have performed quite the service to Linux gamers. I've been playing this terrific game since 2002, I've been playing the Linux version since 2008, and (as you may guess) I had my own problems getting it to properly run. Once you do get it running, be sure to back up your /home folder, since it will restore perfectly in case o'disaster. The free mods available on Neverwinter Vault, by the way are many, varied, and usually excellent.

One thing I have discovered that I'll also mention. In the hak directory, all .hak files (except, for some reason, the Kingmaker etc haks) MUST be in lower case; you'll get an error in the log file if it has any upper case letters.

Happy gaming!

---

