---
title: "New Dell Mini unable to upgrade / install packages"
date: 2009-11-19
forum: Dell Ubuntu Support (CLOSED)
---

### Post by T3knopath on 2009-11-19
Newbie:

Brand new Inspiron Mini netbook won't install or upgrade any packages.  I keep getting the following error message:

E: /var/cache/apt/archives/libsdl-net1.2_1.2.7-2_lpia.deb: files list file for package `libxcb-shape0' is missing final newline

also getting this error from the the terminal:


15 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
Need to get 0B/31.0MB of archives.
After this operation, 119kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... dpkg: error processing /var/cache/apt/archives/linux-image-2.6.24-22-lpia_2.6.24-22.45netbook9_lpia.deb (--unpack):
 files list file for package `libxcb-shape0' is missing final newline
Errors were encountered while processing:
 /var/cache/apt/archives/linux-image-2.6.24-22-lpia_2.6.24-22.45netbook9_lpia.deb
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)

:confused:
HELP!....

---

### Post by dvlchd3 on 2009-11-19
Try clearing out the apt cache and upgrading again:

```

sudo apt-get clean && sudo apt-get update && sudo apt-get upgrade

```

---

### Post by T3knopath on 2009-11-19
That seems to have done something, but failed on the last package.

Get: 15 [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/universe xorg-modules-xpsb 0.16+0038-0netbook1 [31.0kB]      
Fetched 31.0MB in 2min29s (207kB/s)                                                                                         
(Reading database ... dpkg: error processing /var/cache/apt/archives/linux-image-2.6.24-22-lpia_2.6.24-22.45netbook9_lpia.deb (--unpack):
 files list file for package `libxcb-shape0' is missing final newline
Errors were encountered while processing:
 /var/cache/apt/archives/linux-image-2.6.24-22-lpia_2.6.24-22.45netbook9_lpia.deb
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)

Also tried to install a small program afterwards using Synaptic and got the usual  missing final newline error. I'm a bit surprised at this as you'd think Dell would supply a fully functional OS!

E: /var/cache/apt/archives/libsdl-pango1_0.1.2-3_lpia.deb: files list file for package `libxcb-shape0' is missing final newline

---

### Post by snowpine on 2009-11-19
Hi, I wish I had a more directly helpful answer :) but "Ubuntu, Dell Remix" is not my favorite Linux release. It lasted about 10 minutes on my Dell Mini 9 before I gave up and installed "real" Ubuntu instead. Dell is a good hardware manufacturer, but I won't be relying on them for my operating system. This page is a good resource if you decide to go that route: [http://www.ubuntumini.com/](http://www.ubuntumini.com/)

---

### Post by T3knopath on 2009-11-19
Tried these commands from another post, look like everyone is having this problem:

sudo aptitude clean
sudo aptitude autoclean
cd /var/lib/dpkg/info
sudo rm libxcb-shape0.list
sudo apt-get update
sudo apt-get --reinstall install libxcb-shape0
sudo rm /var/lib/apt/lists/*
sudo mkdir /var/lib/apt/lists/partial
sudo dpkg --clear-avail
sudo dpkg --configure -a
sudo aptitude install -f
sudo aptitude update
sudo aptitude dist-upgrade


Followed this up with: sudo apt-get update  

(no errors)
Going to reboot and try to install something.  will let you know how if it works. :)

---

### Post by T3knopath on 2009-11-19
Sod it, I've had enough of this already, I'm going to try and install 9.1 Karmic Koala instead.

Thanks for your help guys, it seems Dell are selling Hardware with faulty OS.  

I should send it back but I hear Linux is great when it's running properly.  

Thanks again

T3knopath (newb)

---

### Post by snowpine on 2009-11-19
> **T3knopath said:**
> Sod it, I've had enough of this already, I'm going to try and install 9.1 Karmic Koala instead.

Thanks for your help guys, it seems Dell are selling Hardware with faulty OS.  

I should send it back but I hear Linux is great when it's running properly.  

Thanks again

T3knopath (newb)

Yes, please do not judge Linux based on Dell's version. :) The Dell Mini 9 is a great little piece of hardware, once it has a proper version of Linux installed. (Which Dell Mini do you have?)

---

### Post by T3knopath on 2009-11-19
I've got the 'Dell Inspiron Mini 10', nice bit of kit my only gripe is the touchpad is a little fiddly as there no separate buttons.

---

### Post by snowpine on 2009-11-19
Good luck with it... please be aware of one thing... the Mini 10 is a different creature than my Mini 9... tutorials like the one I linked to ( [www.ubuntumini.com](www.ubuntumini.com) ) won't necessarily work for you because you have a different graphics card.

---

### Post by T3knopath on 2009-11-19
Installed and working ok, hope i dont get any graphics issues.  

Thanks again guys!....  

*Dell should issues a warning before they sell Cononical OS*

---

### Post by rcbarrett88 on 2009-11-19
hi
[https://answers.launchpad.net/ubuntu/+question/78863](https://answers.launchpad.net/ubuntu/+question/78863)
follow this link it will have the answer you have been looking for

---

### Post by rcbarrett88 on 2009-11-19
hi
follow this link it may help you
[https://answers.launchpad.net/ubuntu/+question/78863](https://answers.launchpad.net/ubuntu/+question/78863)

---

