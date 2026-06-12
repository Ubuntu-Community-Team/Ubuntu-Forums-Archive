---
title: "Is it possible to install tarball without build-essential?"
date: 2006-04-04
forum: Desktop Environments
---

### Post by whoa_551 on 2006-04-04
Hi.  I am trying to install a modem-driver tarball (configure, make, install required) and (obviously) without a internet connection, I can't download "build-essential".  My question: Is there an alternate way of 1.)Installing the tarball ***or*** 2.)getting the "build-essential" pkg including dependencies, etc., manually...(I currently use dial-up in windows :( )

---

### Post by Qrk on 2006-04-04
You do need build-essential.

Download (from windows) all of the packages listed here:

[http://packages.ubuntu.com/breezy/devel/build-essential](http://packages.ubuntu.com/breezy/devel/build-essential)

And copy them to your desktop on ubuntu (either from a usb drive or from your windows partition)

```
cd ~/Desktop
sudo dpkg -i *.deb
```

---

### Post by vloris on 2006-04-04
[QUOTE=Qrk]Download (from windows) all of the packages listed here:

[http://packages.ubuntu.com/breezy/devel/build-essential](http://packages.ubuntu.com/breezy/devel/build-essential)
[/QUOTE]
You need to recursively get all the dependent packages. For example, the mentioned package dpkg-dev itself needs binutils, make, patch etc. to be installed. I think you are busy quite a while before you have all of them...

---

### Post by whoa_551 on 2006-04-04
[QUOTE=Qrk]You do need build-essential.

Download (from windows) all of the packages listed here:

[http://packages.ubuntu.com/breezy/devel/build-essential](http://packages.ubuntu.com/breezy/devel/build-essential)

And copy them to your desktop on ubuntu (either from a usb drive or from your windows partition)

```
cd ~/Desktop
sudo dpkg -i *.deb
```[/QUOTE]

So, will all these packages then have dependencies they need (and those dependencies have dependencies, and so on), or is everything I need already in Breezy and these packages...

---

### Post by whoa_551 on 2006-04-04
> You need to recursively get all the dependent packages. For example, the mentioned package dpkg-dev itself needs binutils, make, patch etc. to be installed. I think you are busy quite a while before you have all of them...

So, it sounds like if I don't get some sort of internet connection going natively, I'm pretty much screwed

---

### Post by aysiu on 2006-04-04
It might take a while to download over dial-up, but you can get an unoffical add-on CD that includes *build-essential* and a bunch of other stuff:

[http://www.tikal26.net/ubuntu/](http://www.tikal26.net/ubuntu/)

Full list of packages is [here](http://www.ubuntuforums.org/showpost.php?p=813538&postcount=115).

---

### Post by whoa_551 on 2006-04-04
[QUOTE=aysiu]It might take a while to download over dial-up, but you can get an unoffical add-on CD that includes *build-essential* and a bunch of other stuff:

[http://www.tikal26.net/ubuntu/](http://www.tikal26.net/ubuntu/)

Full list of packages is [here](http://www.ubuntuforums.org/showpost.php?p=813538&postcount=115).[/QUOTE]

Yeah, there is no way that .iso will come through unscathed...Is there any CD-ROM that can be ordered over the internet?

---

### Post by aysiu on 2006-04-04
[QUOTE=whoa_551]Yeah, there is no way that .iso will come through unscathed...Is there any CD-ROM that can be ordered over the internet?[/QUOTE] Not that I know of.

I think someone has the add-on CD in a torrent:
[http://www.ubuntuforums.org/showpost.php?p=812666&postcount=114](http://www.ubuntuforums.org/showpost.php?p=812666&postcount=114)

If I'm not mistaken, downloading through bittorrent is more likely to leave you with an uncorrupted .ISO.

If that doesn't work, honestly, Ubuntu may not be for you. It's heavily internet-dependent--unlike some other distros that have multiple CDs (Debian and Mandriva, for example).

---

### Post by whoa_551 on 2006-04-04
[QUOTE=aysiu]Not that I know of.

I think someone has the add-on CD in a torrent:
[http://www.ubuntuforums.org/showpost.php?p=812666&postcount=114](http://www.ubuntuforums.org/showpost.php?p=812666&postcount=114)

If I'm not mistaken, downloading through bittorrent is more likely to leave you with an uncorrupted .ISO.

If that doesn't work, honestly, Ubuntu may not be for you. It's heavily internet-dependent--unlike some other distros that have multiple CDs (Debian and Mandriva, for example).[/QUOTE]

Last Question--How do the Debian .deb's install on Ubuntu?  Do they tend to work or not?

---

### Post by aysiu on 2006-04-04
[QUOTE=whoa_551]Last Question--How do the Debian .deb's install on Ubuntu?  Do they tend to work or not?[/QUOTE] Based on my limited experience and what I've read, this is my understanding of the situation: if you install one or two individual Debian .debs on Ubuntu, everything should be fine.

If you consistently use Debian .debs or mix Debian and Ubuntu repositories, you'll end up with a broken system and a lot of unmet or unresolvable dependencies.

---

### Post by Qrk on 2006-04-04
They do work, but its always a little hit and miss. 

You should try to use the ubuntu debs if possible, but some programs only put out one set.

---

### Post by aysiu on 2006-04-11
Okay. I did a fresh Breezy install on my test machine.

I moved all the old packages from /var/cache/apt/archives to a new temporary directory (essentially emptying out the archives).

Then I installed only *build-essential* via apt-get.

These are the additional .debs that popped into /var/cache/apt/archives:

binutils_2.16.1-2ubuntu6_i386.deb
build-essential_11.1_i386.deb
dpkg-dev_1.13.10ubuntu4_all.deb
g++_4%3a4.0.1-3_i385.deb
g++-4.0_4.0.1-4ubuntu9_i386.deb
gcc_4%3a4.0.1-3_i386.deb
gcc-4.0_4.0.1-4ubuntu9_i386.deb
libc6-dev_2.3.5-1ubuntu12.5.10.1_i386.deb
libstdc++6-4.0-dev_4.0.1-4ubuntu9_i386.deb
linux-kernel-headers_2.6.11.2-0ubuntu13_i386.deb
make_3.80-9_i386.deb

So, theoretically, if you download all of those files (about 9.8 MB) on one computer, move them to your Ubuntu desktop and then ```
cd ~/Desktop
sudo dpkg -i *.deb
``` you should have *build-essential*.

---

### Post by kronicred on 2006-06-17
Thank you for that list of requirements.  I was having the same chicken and egg problem.  I was trying to install ndiswrapper.tar.gz to get a wireless usb adapter to work, but found out I needed build-essential to compile it.  But of course you need a dozen other things to even install build-essential...  I was about to give up until I found this list.  What a crazy process.  I am a total n00b to Linux.  It's a bit difficult, but it is going to feel so damn good when (crossed fingers) I get that wireless adapter to work.

---

### Post by aysiu on 2006-06-17
Well, since then I've learned that the *build-essential* package is *included* on the Dapper Desktop and Alternate CDs, even though it's not *installed*.

---

