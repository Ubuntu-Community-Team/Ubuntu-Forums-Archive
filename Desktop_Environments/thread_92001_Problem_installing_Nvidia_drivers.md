---
title: "Problem installing Nvidia drivers:"
date: 2005-11-18
forum: Desktop Environments
---

### Post by Bobbywhiskey on 2005-11-18
I tryed to install my 6600 GT drivers and it tells me that:
  ERROR: Unable to find the system utility `ld`; please make sure you have the
         package 'binutils' installed.  If you do have binutils installed,
         then please check that `ld` is in your PATH.

what do i have to do? im a complete noob

---

### Post by kosmic on 2005-11-18
did you try to install the Nvidia drivers from Synaptic (APT) or by source code from the Nvidia page ?
 
 
The easy way is to fire Synaptic and search for Nvidia, and install the driver

---

### Post by Kyral on 2005-11-18
Fastest way is to pop open a terminal and

```
sudo apt-get install nvidia-glx
```
To install the modules

Then

```
sudo nvidia-glx-config enable
```
To alter your XOrg.conf to use it

Then hit CTRL+ALT+Backspace to restart X. You know it worked if the NVidia logo shows up

---

### Post by 23meg on 2005-11-18
[QUOTE=Kyral]
```
sudo apt-get install nvidia-glx
```
To install the modules
[/QUOTE]
I've never installed the driver from the repositories so I'm not sure about this: does the nvidia-glx package install the kernel module as well? Last time I checked it was in the linux-restricted-modules packages.

---

### Post by Kyral on 2005-11-18
It should, but like I said it has been known to screw up.

---

### Post by Bobbywhiskey on 2005-11-19
[QUOTE=kosmic]did you try to install the Nvidia drivers from Synaptic (APT) or by source code from the Nvidia page ?
 
 
The easy way is to fire Synaptic and search for Nvidia, and install the driver[/QUOTE]
How does Synaptic work?
I tryed to install the drivers from Nvidia web page

[QUOTE=Kyral]  

Fastest way is to pop open a terminal and

Code:

sudo apt-get install nvidia-glx

To install the modules

Then

Code:

sudo nvidia-glx-config enable

To alter your XOrg.conf to use it

Then hit CTRL+ALT+Backspace to restart X. You know it worked if the NVidia logo shows up
[/QUOTE]

I just have to type this? nothing to download? if yes, where do i put it?
I told you , im a complete noob in linux....

---

### Post by Bobbywhiskey on 2005-11-19
okay thanks Everyone i installed it!!
I installed it with sudo apt-get install nvidia-glx
But could you tell me from where it got the drivers?? internet or harddrive? is it the lastest driver?

---

### Post by Breepee on 2005-11-20
Does anyone know this? What version of the nvidia drivers are in the repos?

---

### Post by astoltz on 2005-11-20
the nvidia drivers in breezy are 7667. 

As far as questions about Synaptic and apt-get (synaptic is a GUI front end for the command line apt-get).  This is THE way to install programs in a debian based system.  Search around the forums and the wiki and you'll find some better HOWTOs than I can do here.

---

### Post by Drain on 2005-11-20
The wonderful thing about Ubuntu (okay, one of the many wonderful things about Ubuntu, but common to all forms of linux built around Debian's model) is the "apt-get" commands. 

BobbyWhiskey, the files you get from using "apt-get" come from a file repository on the internet - specifically, Ubuntu's file repository. "Synaptic" (or "Adept" if you're using Kubuntu and KDE), are graphical front-ends to apt-get. To keep your distrobution up to date, you can type "sudo apt-get update && sudo apt-get upgrade" at the command line, and both Synaptic and Adept have their three-clicks-and-you're-done methods too. :-) 

Here's what I get when I checked the version of nvidia's drivers (slightly edited):

```
$ sudo apt-cache show nvidia-glx
Package: nvidia-glx
Priority: optional
Section: restricted/x11
Installed-Size: 10036
Maintainer: Adam Conrad <adconrad@ubuntu.com>
Architecture: i386
Source: linux-restricted-modules-2.6.12 (2.6.12.4-11)
**Version: 1.0.7667-0ubuntu25**
Replaces: nvidia-glx-src
Depends: nvidia-kernel-1.0.7667, xserver-common (>= 4.0.3),
libglu1-mesa | libglu1, libc6 (>= 2.3.4-1), libx11-6, libxext6
Suggests: nvidia-settings, nvidia-kernel-source (>= 1.0.7667)
Conflicts: nvidia-glx-src
Size: 3084736
Description: NVIDIA binary XFree86 4.x/X.Org driver
Origin: Ubuntu
```

I would recommend taking a look over [http://www.ubuntuguide.org]("http://www.ubuntuguide.org"), for a lot of great step-by-step ways to get things running on Ubuntu. (Just be forewarned that it was written for the Hoary version, not Breezy, so some steps may be a little different now - but it will definately get you rolling with the basics).

---

### Post by Vlammend on 2005-11-26
After being unable to install the Nvidia drivers in Hoary and Warty I am gonna try again in Breezy. I am gonna try this:
[http://www.ubuntuguide.org/#installnvidiadriver]("ubuntuguide#installnvidiadriver")

However when I look at the proporties of nvidia-glx in Synaptic then it recommends also:
*nvidia-kernel-source*
and
nvidia-settings

nvidia-settings I can find, but nvidia-kernel-source seams unavailable.
Is this bad? where can I find it? :confused: 

I have a Geforce FX 5700 Ultra. If the method displayed in the guide works, I will place that here.
edit: :-( Did not work :-(, screen goes into standbye, so it doesn't get a signal

---

### Post by stalefries on 2005-11-26
In a terminal, type
```
sudo apt-get install binutils
```

Then try to install the drivers again.

---

### Post by Vlammend on 2005-11-26
These where already installed. I am now trying to solve this issue in this thread:
[http://www.ubuntuforums.org/showthread.php?t=75074&highlight=nvidia+breezy]("http://www.ubuntuforums.org/showthread.php?t=75074&highlight=nvidia+breezy")

---

