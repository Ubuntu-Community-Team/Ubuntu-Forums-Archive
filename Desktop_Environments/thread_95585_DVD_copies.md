---
title: "DVD copies"
date: 2005-11-26
forum: Desktop Environments
---

### Post by montes.c on 2005-11-26
How do I make a copy of a DVD using Gnome in Ubuntu? What tools do I use and the steps? For example to back up the movies I bought, I scratch them up easily so I want to use a copy for normal use and stuff the original in my closet to keep it safe and not have to buy another?

---

### Post by mcmuffy on 2005-11-26
I think there is a program called k9copy but if not this like will show you how to get dvdshrink and dvdecrypter working in linux.

[http://www.mrbass.org/linux/ubuntu/dvdshrink/](http://www.mrbass.org/linux/ubuntu/dvdshrink/)

---

### Post by teaker1s on 2005-11-26
well I use dvddecrypter and dvd shrink running through 'wine'
then I grab the autorun.inf file off the dvd and burn it as a data dvd in gnomebaker

note k3b and gnomebaker are great cd/dvd burning programs-nero in wine was unstable and nerolinux is crap feature wise don't bother

---

### Post by montes.c on 2005-11-27
Is there nothing completely linux with open source tools? Wine and DVD shrink are windows stuff. I dont want to use that, I want open source please.

---

### Post by bb002 on 2005-11-27
teaker1s mentioned k3b and gnomebaker; they are both open source. You'll just have to install them first. I personally like gnomebaker.

type or paste the command into a terminal window.
you can install gnomebaker with > sudo apt-get install gnomebaker
you can install k3b with > sudo apt-get install k3b
apt-get will most likely tell you that it needs to install a few more packages so the programs will work. Say yes to install the extra packages or no to cancel the install.

---

### Post by SickTwist on 2005-11-27
[Thoggen]("http://thoggen.net/") is a DVD backup program built on GTK2 and gstreamer. It has not been around long and is still under heavy development but you may want to try it out.

EDIT: I noticed on the [thoggen-devel mailing list]("http://news.gmane.org/gmane.comp.video.thoggen.devel") that some were reporting problems with Breezy and Thoggen. One person claimed that running Thoggen as root solves this issue so keep that in mind if you try it out.

---

### Post by montes.c on 2005-11-27
Thanks alot for the help! I'll test them out and get back to you people.

---

### Post by Original Brownster on 2005-11-27
[QUOTE=montes.c]Is there nothing completely linux with open source tools? Wine and DVD shrink are windows stuff. I dont want to use that, I want open source please.[/QUOTE]
Hi,

For native Linux tools I use lxdvdrip and xdvdshrink

---

### Post by montes.c on 2005-11-29
[QUOTE=Original Brownster]Hi,

For native Linux tools I use lxdvdrip and xdvdshrink[/QUOTE]

xochiyotl# apt-get install lxdvdrip
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  lxdvdrip: Depends: dvdwizard but it is not going to be installed
E: Broken packages

---

### Post by Original Brownster on 2005-11-29
Hi,
did you follow my howto available [here ]("https://wiki.ubuntu.com/lxdvdripOnBreezyHowto?highlight=%28lxdvdrip%29")?

Regards

---

### Post by doitashimashite on 2005-11-30
You might find this useful:
[http://www.mrbass.org/linux/ubuntu/dvdshrink/](http://www.mrbass.org/linux/ubuntu/dvdshrink/)

It helped me a lot!

[IMG]http://www.xs4all.nl/~acben/screenshot.jpg[/IMG]

---

### Post by JimS on 2006-01-14
...
Another great guide is at:
[http://media.fastclick.net/w/get.media?sid=9388&m=5&url=http%3A//home.comcast.net/%7Ebbmayo/backup%2520with%2520Decrypter%26Shrink.pdf](http://media.fastclick.net/w/get.media?sid=9388&m=5&url=http%3A//home.comcast.net/%7Ebbmayo/backup%2520with%2520Decrypter%26Shrink.pdf)
It is a pdf file showing how to use DVD-Decrypter and DVDShrink
with lots of pictures for us semi-illiterate ones.  ;) 

DVD-Decrypter is no longer available from AfterDawn.  :(   
See details at:
http://www.afterdawn.com/software/video_software/dvd_rippers/dvd_decrypter.cfm[/url]
But it is still at:
[http://www.free-codecs.com/download/DVD_Decrypter.htm](http://www.free-codecs.com/download/DVD_Decrypter.htm)
and/or
[http://www.videohelp.com/tools?tool=DVD_Decrypter](http://www.videohelp.com/tools?tool=DVD_Decrypter)

JimS
Prostate Cancer Aware
...

---

