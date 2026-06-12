---
title: "X: cannot stat /etc/X11/X (No such file or directory), aborting."
date: 2008-02-27
forum: Desktop Environments
---

### Post by slim99 on 2008-02-27
Hi all,
recently installed ubuntu 7.10 Server edition in a virtual machine in VMWare.
All was going well but when installing an application that requires configuration via a GUI I started seeing errors implying X Windows were not installed. 
I'm not really sure which packages are required for a GUI to run but heres some info:

[B]root@baersys:/etc/init.d# apt-get install x11-common
...
x11-common is already the newest version.  [/B]

**and **

r[B]oot@baersys:/etc/init.d# apt-get install xserver-xorg
Reading package lists... Done
Building dependency tree
Reading state information... Done
Package xserver-xorg is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  xserver-xorg-video-unichrome xserver-xorg-input-void xserver-xorg-input-vmmouse xserver-xorg-input-ur98
  xserver-xorg-input-tek4957 xserver-xorg-input-summa xserver-xorg-input-spaceorb xserver-xorg-input-penmount
  xserver-xorg-input-palmax xserver-xorg-input-mutouch xserver-xorg-input-microtouch xserver-xorg-input-magictouch
  xserver-xorg-input-magellan xserver-xorg-input-joystick xserver-xorg-input-jamstudio xserver-xorg-input-hyperpen
  xserver-xorg-input-fpit xserver-xorg-input-elo2300 xserver-xorg-input-dynapro xserver-xorg-input-dmc
  xserver-xorg-input-digitaledge xserver-xorg-input-citron xserver-xorg-input-calcomp xserver-xorg-input-aiptek
  xserver-xorg-input-acecad xserver-xorg-video-intel xserver-xorg-core
E: Package xserver-xorg has no installation candidate
[/B]
**and **

[B]root@baersys:/etc/init.d# xinit
X: cannot stat /etc/X11/X (No such file or directory), aborting.
xinit:  Server error.
root@baersys:/etc/init.d#[/B]

Can somebody tell me what packages I need? I have looked at :
[http://packages.ubuntu.com/gutsy/x11/](http://packages.ubuntu.com/gutsy/x11/)
but the sheer number available confuses me.

I am familiar with AIX but new to Linux, and am accustomed to command line in AIX rather than KDE etc.

Should I be trying to install Gnome ro KDE? Is that what it is required?
Any pointers appreciated.
Thanks, Slim

---

### Post by renzokuken on 2008-02-27
instaling gnome or KDE would certainly install all the X components for you. I'm not sure if you can install X without an actual Desktop Environment though, but then i'm kind of wondering what the point would be anyway.

anyways, should you choose to install a full desktop use the following for:



**Gnome**```
sudo apt-get install ubuntu-desktop
```
**KDE**```
sudo apt-get install kubuntu-desktop
```
**XFCE**```
sudo apt-get install xubuntu-desktop
```

---

### Post by slim99 on 2008-02-28
Thanks for that renzokuken, but no luck:

root@baersys:~# apt-get install kubuntu-desktop
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package kubuntu-desktop

then tried kde:
 
root@baersys:~# apt-get install kde
Reading package lists... Done
Building dependency tree
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  kde: Depends: kde-core (>= 5:47) but it is not installable
       Depends: kde-amusements (>= 5:47) but it is not going to be installed
       Depends: kdeaccessibility (>= 4:3.4.3) but it is not installable
       Depends: kdeaddons (>= 4:3.4.3) but it is not installable
       Depends: kdeadmin (>= 4:3.4.3) but it is not going to be installed
       Depends: kdeartwork (>= 4:3.4.3) but it is not installable
       Depends: kdegraphics (>= 4:3.4.3) but it is not going to be installed
       Depends: kdemultimedia (>= 4:3.4.3) but it is not going to be installed
       Depends: kdenetwork (>= 4:3.4.3) but it is not going to be installed
       Depends: kdepim (>= 4:3.4.3) but it is not going to be installed
       Depends: kdeutils (>= 4:3.4.3) but it is not going to be installed
       Depends: kdewebdev (>= 4:3.4.3) but it is not installable
E: Broken packages

Any ideas as to how to proceed? 
Thanks,  Bernie.

---

### Post by slim99 on 2008-02-28
Then read this:
[http://www.psychocats.net/ubuntu/kde](http://www.psychocats.net/ubuntu/kde)

so tried this:

# sudo aptitude update && sudo aptitude install kubuntu-desktop

but same result:

...
...
Get:18 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) gutsy-updates/multiverse Packages [9942B]
Get:19 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) gutsy-updates/multiverse Sources [1883B]
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) gutsy/universe Packages
Fetched 577kB in 1m16s (7591B/s)
Reading package lists... Done
Reading package lists... Done
Building dependency tree
Reading state information... Done
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done
**Couldn't find any package whose name or description matched "kubuntu-desktop"**
No packages will be installed, upgraded, or removed.
...
...

---

### Post by slim99 on 2008-02-28
I'm guessing I just need to update my repositories so will try this:

[http://ubuntuguide.org/wiki/Ubuntu:Gutsy#Manual_Method_for_Adding_Repositories](http://ubuntuguide.org/wiki/Ubuntu:Gutsy#Manual_Method_for_Adding_Repositories)

---

### Post by slim99 on 2008-02-28
Nope......... after following that procedure to update repositories tried the install again:

.....
....
etc...
.....
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) gutsy-backports/multiverse Sources
Fetched 193B in 2m34s (1B/s)
Reading package lists... Done
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
**Couldn't find any package whose name or description matched "kubuntu-desktop"**
The following packages have been kept back:
  ntfs-3g
0 packages upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
....
....

---

### Post by slim99 on 2008-02-28
Tries apt-get instead of aptitude:

**_sudo apt-get update && sudo apt-get install kubuntu-desktop_**

and so far it appears to be working (lots of downloading happening).........
will update with results later.

---

### Post by slim99 on 2008-02-28
After 480MB of downloads in 2hrs 40 mins I have kubuntu desktop installed...... hooray!

---

### Post by kerry_s on 2008-02-28
you didn't have to install a whole DE, you could have gone light.

sudo apt-get install xorg gdm synaptic (a-wm) (whatever-else)
example:
sudo apt-get install xorg gdm synaptic fluxbox rox-filer leafpad
or maybe icewm is your thing:
sudo apt-get install xorg gdm synaptic icewm rox-filer leafpad
i'm jwm:
sudo apt-get install xorg gdm synaptic jwm rox-filer leafpad

there are many choices if you don't need everything from a desktop install
main thing is "xorg" is X, you need that, everything else is optional.

---

### Post by slim99 on 2008-02-28
Thanks Kerry.
Yeah, as soon as I saw the extent of the downloads I figured I could have done it better, but as I was unaware of the actual packages required to do the minimal install I let it go. Oh well, I'm slowly learning.

---

