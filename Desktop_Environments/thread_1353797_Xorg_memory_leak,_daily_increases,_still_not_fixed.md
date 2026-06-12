---
title: "Xorg memory leak, daily increases, still not fixed?"
date: 2009-12-13
forum: Desktop Environments
---

### Post by fixitdude on 2009-12-13
Not much is happening on this problem, which has transversed several versions now.

I can easily make it do this using Firefox. It's repeatable.

First, take note of your current memory use.

Go to [http://maps.google.com/](http://maps.google.com/) pick your city, then hit "Satellite" view, zoom in a little then hold down the mouse and pan around your town (making it load new sections of the map).

Watch your memory get gobbled up. Now quit Firefox and watch as the memory usage doesn't go down very much, and never returns to what it was.

I'm really tired of this, I thought upgrading this time would fix it since this bug is so old.

I think it's what people have been saying, it's a "pixmap" problem. One way to cut down on the problem is to never use "Satellite" with google maps. Others have reported that pdf viewers eat memory the same way.

You can read some of the bug reports, but it seems this problem is hard to track down.
[https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/98783](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/98783)

I'm running 2.6.24-25-generic (Ubuntu 8.04.3 LTS Hardy). VGA compatible controller: nVidia Corporation C51G [GeForce 6100] (rev a2) (nvidia drivers are disabled)

To get your Kernel info type "uname -a", for the Ubuntu version "cat /etc/lsb-release" and for a list of devices "lspci".

To see your Xorg memory usage "top -bn1 | grep Xorg".

---

### Post by Physical Hook on 2009-12-13
Running 9.10 and everything seems to be just fine. +80Mb ( opened ) / - 80Mb ( closed ) ..

---

### Post by falconindy on 2009-12-13
Oh it's been fixed. On other distros.

All you need to do is convince Canonical to apply the patch that's been available for a few months or to ship xorg-server 1.7.3.901.

---

### Post by ert45 on 2010-04-15
Hello,

The solution proposed in [https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/186354](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/186354) worked for me: disable xinerama.

On ubuntu 9.04, I added this at the bottom of my /etc/X11/xorg.conf and then had no more problem after restarting the X server:

Section "Serverflags"
    Option "Xinerama" "false"
Endsection

---

### Post by alecz20 on 2010-05-19
For what it's worth, I am running SUSE Linux Enterprise Server 10 SP1 at work in a virtual machine in VMWare player under Window$ Vista.
Xorg is using **only 25 MB of memory**.
Total system memory usage is almost always under 300 MB, even if I open several applications.

The system has been up for over a day, I have been doing a lot of browsing in Firefox, and other things.
I have Firefox open with two tabs, two terminals, system monitor, and nautilus.

The assigned memory for this machine is 768 MB.


EXTRA INFO:
What is worth mentioning is that this release of SUSE is a commercial release, and it is supposed to be rock-solid (also it's the most expensive OS offered by Novell - $800 with one year subscription).

For this reason alot of packages are very old, but very stable.
For example it uses:

Xorg 6.9.0
Firefox 2.0.0.
No compiz, or other desktop effects.

The take-home message, I think, is that Ubuntu is more of a "cutting-edge" distro, always using the latest versions of most of the packages which are not fully tested by the users (i.e. YOU).

Companies such as Red Hat and Novell, offer their distro in two flavors: free open-source and paid open-source.
The free versions are cutting-edge, and used for testing by the community (i.e. YOU), while the paid versions are older, more stable and used mostly by companies.

The idea is that if you want features, the free versions (Ubuntu, openSUSE, Fedora) will offer that but they might have bugs.
If you want stability and reliability, then you might be better off with a commercial version (or a free rebuild of one), however you will not have all the latest bells and whistles.

---

