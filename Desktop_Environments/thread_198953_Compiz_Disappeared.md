---
title: "Compiz Disappeared"
date: 2006-06-18
forum: Desktop Environments
---

### Post by krs1ars on 2006-06-18
Hey guys. Sorry for another Compiz/XGL related support post. Anyway, I installed XGL/Compiz, and it worked great. A few login's later, it the effects went away. Don't know why/how. Didn't do anything that should've changed anything.

I have a Nvidia GeForce 5200FX.

My install went like this:
[LIST]
[*]Open up universe repositories in Synaptic, and add xgl.compiz.info
[*]apt-get install nvidia-kernel-common nvidia-xgl xserver-xgl compiz compiz-gnome
[*]change xorg.conf
modules:
```
Section "Module"
     Load "i2c"
     Load "bitmap"
     Load "ddc"
#   Load "dri"
     Load "extmod"
     Load "freetype"
     Load "glx"
     Load "int10"
     Load "type1"
     Load "vbe"
EndSection
```
```

Section "Device"
    Identifier "NVIDIA Corporation NV34 [GeForce FX 5200]"
    Driver     "nvidia"
    BusID     "PCI:1:0:0"
    Option    "RenderAccel"  "true"
EndSection

```
```

Section "Extensions"
    Option  "Composite" "Enable"
EndSection

```
[*] Write ~/.Xsession
```

    #!/bin/sh
    # Start up Xgl, compiz, and GNOME

    # Run Xgl server on :1, on top of normal X
    Xgl :1 -fullscreen -ac -accel xv:fdo -accel glx:pbuffer &

    # Tell subsequent X programs to access the Xgl server at :1
    DISPLAY=:1

    # Start Compiz window manager
    gnome-window-decorator &
    compiz gconf decoration wobbly fade minimize cube rotate zoom scale move resize place menu switcher &

    # Start GNOME
    exec gnome-session


```
and call
```

chmod +x ~/.Xsession

```
[/LIST]

So that's the long and short of it. When it boots now, I log on, see the checkerboard X screen, the quick blue backround and then its just logs on as normal. No cool wiggly windows or 3D workspaces.

Any help would be great. Thanks.

---

### Post by reclusivemonkey on 2006-06-18
[QUOTE=krs1ars]
[*] Write ~/.Xsession
[/QUOTE]

That should be .xsession I believe. I am using the "thefuture" method myself, which has been reliable.

---

### Post by hotani on 2006-06-21
Same thing here, everything just stopped working this morning for no apparent reason. This was after about 2 weeks of working fine.

I'm using aiglx, and followed the howto on this board regarding aiglx+compiz.

It's like compiz just fails to load at the last second - I have lost the menu item as well.

---

### Post by suxab on 2006-06-21
just a tip: look at your "Default session type" in the login manager / GDM/

---

### Post by hotani on 2006-06-22
When I got it running, I had used [this howto](http://www.ubuntuforums.org/showthread.php?t=145068) here on the board.

For some reason, i'm getting errors all over the place when I try to do anything with the proper compiz packages. What happened? Is this because of a recent update maybe?

```

shell> sudo aptitude purge compiz-aiglx compiz-aiglx-gnome
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
The following packages have been kept back:
  gnome-session libwnck18
0 packages upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
dpkg: ../../src/packages.c:191: process_queue: Assertion `dependtry <= 4' failed.
E: Sub-process /usr/bin/dpkg exited unexpectedly
A package failed to install.  Trying to recover:
dpkg: ../../src/packages.c:191: process_queue: Assertion `dependtry <= 4' failed.

```

and when I try to install the sw:
```

shell > sudo apt-get install compiz-vanilla-aiglx compiz-vanilla compiz-vanilla-gnome
Reading package lists... Done
Building dependency tree... Done
compiz-vanilla is already the newest version.
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  compiz-vanilla-gnome: Depends: libpango1.0-0 (>= 1.12.3) but 1.12.2-0ubuntu3 is to be installed
E: Broken packages

```

Here is what 'dist-upgrade' gives me:
```

shell> sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree... Done
Calculating upgrade... Done
The following packages have been kept back:
  gnome-session libwnck18
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]?
dpkg: ../../src/packages.c:191: process_queue: Assertion `dependtry <= 4' failed.
E: Sub-process /usr/bin/dpkg exited unexpectedly

```

**libpango**?? Why is this broken? And spontaneously broken at that!


Ah, the joys of linux! We live for this, right guys? Right? ..... Guys? *crickets*

---

### Post by hotani on 2006-06-22
This is just turning into a log of me fixing this problem.... I found a [page mentioning these forums](http://techxplorer.wordpress.com/2006/05/21/resolving-an-odd-dpkg-error-in-ubuntu/) regarding the very problem i've been having. Here is what happend when I ran the first command:

```

shell>  sudo dpkg -l | grep -v ^ii
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-files/Unpacked/Failed-config/Half-installed
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name                                   Version                               Description
+++-======================================-=====================================-================================================
rc  compiz-vanilla-aiglx                   0.0.13-0ubuntu1                       OpenGL composition manager
iU  python-subversion                      1.3.1-3ubuntu1                        python modules for interfacing with Subversion (
rc  rmail                                  8.13.5-3ubuntu1                       MTA->UUCP remote mail handler
rc  sensible-mda                           8.13.5-3ubuntu1                       Mail Delivery Agent wrapper

```

after removing all of those, I tried again:
```

> sudo apt-get install compiz-vanilla-aiglx compiz-vanilla compiz-vanilla-gnome
Reading package lists... Done
Building dependency tree... Done
compiz-vanilla is already the newest version.
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  compiz-vanilla-gnome: Depends: libpango1.0-0 (>= 1.12.3) but 1.12.2-0ubuntu3 is to be installed
E: Broken packages

```

Guess not.

This seems to be the problem of the day (from Synaptic):
```

compiz-vanilla-gnome:
  Depends: libpango1.0-0 (>=1.12.3) but 1.12.2-0ubuntu3 is to be installed
```

and yet more error goodness:
```

http://us.archive.ubuntu.com/ubuntu/dists/dapper/restricted/binary-i386/Packages.bz2: Could not open file /var/lib/apt/lists/partial/us.archive.ubuntu.com_ubuntu_dists_dapper_restricted_binary-i386_Packages - open (2 No such file or directory)
http://us.archive.ubuntu.com/ubuntu/dists/dapper/restricted/binary-i386/Packages.bz2: Could not open file /var/lib/apt/lists/partial/us.archive.ubuntu.com_ubuntu_dists_dapper_restricted_binary-i386_Packages - open (2 No such file or directory)

```

Small success! I got the compiz packages to install in spite of the above error. I'm going thru some updates now but will then reboot and see if my wiggly windows are back.

---

### Post by hotani on 2006-07-10
Welp, it did it again. On BOTH my Dells - laptop and Desktop. No Compiz. Just gone. WTF? I would just let it go but now I feel like I should do battle with it and establish who wears the pants in this love/hate relationship.

---

