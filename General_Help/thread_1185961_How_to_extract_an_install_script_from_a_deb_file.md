---
title: "How to extract an install script from a deb file?"
date: 2009-06-12
forum: General Help
---

### Post by shaggy999 on 2009-06-12
I ran into a problem installing Ubuntu for a friend that had a laptop w/ a broadcom wireless card. I needed to install the fwcutter package, which automatically fetches and installs the necessary files from the internet. However, without a working wireless card I was unable to do that and I had no idea what files I needed to grab or where to put them. Eventually I was able to get physical access to a router w/ an ethernet cable and was able to install fwcutter and fetch the files. But it would be nice to be able to extract and see the install script so that if I have to do things manually I can place the necessary files where they go. So I am wondering how I can open up a .deb file and extract the script that fetches and installs the files and does all the post-processing setup?

---

### Post by ronz0o on 2009-06-12
There is actually a program called deb2tar, if my memory serves me correct. You shouldn't need to manually do it, though. Ubuntu does a pretty effective job through the Restricted Drivers Manager.

---

### Post by shaggy999 on 2009-06-12
> **ronz0o said:**
> There is actually a program called deb2tar, if my memory serves me correct. You shouldn't need to manually do it, though. Ubuntu does a pretty effective job through the Restricted Drivers Manager.

The install scripts download broadcom firmware, which Ubuntu cannot distribute, when you install the package. But if there's no internet the package will install, but the firmware will not download so you can't create an internet connection. It's a chicken and egg scenario. That's why I need to download the files seperately and then look at the install scripts to see where it puts the files and what commands it runs afterwards.

But anyway, I'll try deb2tar.

---

### Post by shaggy999 on 2009-06-13
I couldn't find deb2tar, but I did more searching and found this command:

dpkg-deb -x {deb-package name} {target directory}

Here's the script I wanted:

```

#!/bin/sh

set -e

dir=$(mktemp -d)
cd "$dir"
wget http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o
wget http://mirror2.openwrt.org/sources/broadcom-wl-4.150.10.5.tar.bz2
b43-fwcutter -w /lib/firmware wl_apsta-3.130.20.0.o
tar xfvj broadcom-wl-4.150.10.5.tar.bz2
b43-fwcutter --unsupported -w /lib/firmware broadcom-wl-4.150.10.5/driver/wl_apsta_mimo.o
rm -rf "$dir"
chmod o+rx /lib/firmware/b43 /lib/firmware/b43legacy

```

See? So now I know what files to get using a seperate machine then I can transfer the files via usb to the computer in question and set up the wireless card manually.

---

