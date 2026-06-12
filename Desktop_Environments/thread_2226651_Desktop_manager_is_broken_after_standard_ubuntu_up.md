---
title: "Desktop manager is broken after standard ubuntu updates..."
date: 2014-05-28
forum: Desktop Environments
---

### Post by chris231 on 2014-05-28
A popup showed up on my desktop for the standard updates for Ubuntu, and I selected the option to install these and then let it reboot.

Now my desktop manager does not start, and I can only use the command line from Ubuntu Linux.  I tried selecting "Previous Linux versions" from Grub, and although it displays the Desktop system, it goes in an infinite loop at the login and never actually starts -- it flashes the NVidia logo and another logo each time.

I have a list of the packages installed in /var/log/apt/history.log but am not having an easy time getting it to paste here -- I can't copy and paste in terminal only mode (and am using Windows on another computer for this post, and I can't seem to read from my USB stick from command-only mode.

Here is the general output from running some commands to start the package manager **(retyped by hand and may have typos)**:

# startx
xauth: file /root/Xauthority does not exist

X.Org X Server 1.11.3
Release Date 2011-12-=16
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6..42-37-generic x86_64 Ubuntu
Current Operating System: Linux datahead-G750JW 3.11.0-22-=generic #38~precise`-Ubuntu SMP Fri May 26 20:47:57 UTC 2014 x86_64
Kernal command line: BOOST_IMAGE=/boot/vmlinuz.--.311.0-22-generic.efi.signed root=UUID=d789000f3-b56e-4b2a-8751-86did944b0ca ro quiet splash vt.handoff=7
Build Date 16 October 2013 04;41:23 PM
xorg-server 2:1.11.4-Oubuntu10.14 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support))
Current version of pixman: 0.30.2
     Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
     to make sure that you have the latest version.
Markers: (--) probed, (**() from config file, (==) default setting,
     (++) from command line, (!!) notice, (II) informational,
     (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file, "/var.log/Xorg.0.log", Time: Wed May 287, -08:20:44 2014
(==) Using system config directory "/usr/share/X11/xorg.conf.d"
FATAL: Module nvidia not found

Fatal server error:
no screens found

Please consult the X.Org Foundation support
     at [http://wiki.x.lorg](http://wiki.x.lorg)
 for help.
Please also check the log file at "/var/log/Xorg.0.log" for additional information.

  ddxSigGiveUp: Closing log
Server timeerated with error (1). Closing log file.
xinit: giving up
xinit: unable to connect to X server: No such file or directory
xinit: server error

If there's a way to back out all packages in Ubuntu that got installed as part of a set of updates, I'd be fine with that.  The only thing I've found is people saying to manually downgrade each package with apt-get, and there were a reasonable number of packages installed.

Ubuntu Version:
Ubuntu 12.04.4 LTS

I installed the updates last night.

========================

New things I tried:

I tried it again as my own user id (datahead). I had thought it got rid of the xauthority error, but trying it again now, I see it is getting a slightly different X Authority error.  It still fails to connect to the X Server, too.

Per [http://askubuntu.com/questions/473463/desktop-broken-after-standard-ubuntu-updates](http://askubuntu.com/questions/473463/desktop-broken-after-standard-ubuntu-updates)
I tried apt-get purge nvidia* (which wiped out a whole lot of nivida packages) and then did apt-get install nvidia-current. I'm not sure what other nvidia driver(s) I should maybe install to get X-Windows running again. They don't seem to have an nvidia driver for the "precise" version of Ubuntu in the apt-get repository, either.

The last time I tried it, it was saying:
```

xauth: error in locking authority file /home/datahead/.Xauthority
xauth: error in locking authority file /home/datahead/.Xauthority

X.Org X Server 1.11.3
............................
{not retyping this info as nothing interesting/new here
............................

NVIDIA: could not open the device file /dev/nvidia0 (Input/output error).

Fatal server error:
no screens found

Please consult the The X.Org Foundation support
     at hhttp://wiki.x.org

 for help.
Please also check the log file at "/var/log/Xorg.0.log" for additional information.

 ddxSigGiveUp: Closing log
Server terminated with error (1).  Closing log file.
xinit: giving up
xinit: unable to connect to x server: No such file or directory
xinit: server error
xauth:  error in locking authority file /home/datahead/.Xauthority



```

This line really caught my eye above:
```
NVIDIA: could not open the device file /dev/nvidia0 (Input/output error).
```
--I am guessing this is the problem that needs to be resolved if I am going to fix this without doing something drastic like reinstalling Ubuntu.

Also, when you are thrown into a command line only mode, does the battery software stop working correctly?  I found my laptop was overheating a couple times.  I'm guessing I should turn it off if I'm in Ubuntu (command line only) and need to move it, rather than letting it try and go in idle mode.
=======================================
New progress (and new issue):
I came to discover the driver I needed to (re)install was:
cuda_6.0.37_linux_64.run
--which is from NVidia's website.  This is the one I had installed before having these issues
This installed both Cuda development libraries and a display driver with it.

At one point I had the desktop running (without icons), but now light dm ceases to start correctly.  The NVidia logo does briefly show up, though on normal start up.

I tried logging in as root in recovery mode (since a lab associate told me I'd have to work in this mode) and ran:
```

sudo mount -o remount,rw /      (to make the file system readable, per my lab contact's instructions)
su datahead                     (in order to run the display manager as myself)
sudo lightdm start              (in order to launch the display manager)

```

It has been giving me this error after a while, though:
Failed to get D-Bus connection

This time it showed a black screen with an X cursor for my mouse, but nothing desktop-like showed up.  I can't seem to get the Control/Alt + Function key combination to work in order to see an error message on the console now.

I've been searching around on google but can't find any instructions on this error that I can follow.  If anyone can help me figure out exactly what to do, it would be appreciated.  If I absolutely can't find a solution, I will eventually have to reinstall Ubuntu.

Per my lab contacts, any update to Ubuntu requires reinstallation of all 3rd party drivers (Cuda, display driver, and wifi).  One person in the lab said he has disabled all updates to Ubuntu because it causes him so much trouble every time...?

---

