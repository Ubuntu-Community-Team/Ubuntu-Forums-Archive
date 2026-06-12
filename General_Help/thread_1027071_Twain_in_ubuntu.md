---
title: "Twain in ubuntu?"
date: 2008-12-31
forum: General Help
---

### Post by xaephod on 2008-12-31
The one reason I have not migrated to Linux full time is because I can not get my twain scanner to work. Is there some way to run a twain scanner in Ubuntu?

If I can get that to work...and run World of Warcraft perfectly, I would definitely use it more often. Any advice?

Thanks
Xaephod

---

### Post by pmooney78 on 2008-12-31
More details, please ... what kind of scanner are you using? How is it connected to your computer? What are you trying to do to scan (what programs are you using, etc.)?

But here's a couple of things to try:

1. Try installing (if you don't have it already) the GIMP and using that to scan (through your favorite package manager, or "sudo apt-get install gimp-2.4" in a terminal, without the quotes) and seeing whether you can scan by using the entries in the "Acquire" menu.

2. Try installing one of the SANE libraries, if you haven't already. I use xsane, but there are other options.

But if you don't provide more information about your setup, what you're doing, and what happens, then it's hard to provide suggestions. :)

---

### Post by albinootje on 2008-12-31
> **xaephod said:**
> The one reason I have not migrated to Linux full time is because I can not get my twain scanner to work. Is there some way to run a twain scanner in Ubuntu?


Here you can check whether your scanner is (gonna be) supported in Linux or not :
[http://www.sane-project.org/sane-supported-devices.html](http://www.sane-project.org/sane-supported-devices.html)

Years ago I already noticed twain support in Wine being mentioned.
But after a search-engine search it's not clear to me how much is integrated, how it works, and how well it works.
Here is one page where it is mentioned :
[http://www.winehq.org/wwn/313#GPhoto](http://www.winehq.org/wwn/313#GPhoto) / TWAIN Integration

From this page I get the impression that twain support is included in Wine.
[http://packages.debian.org/etch-backports/libwine-twain](http://packages.debian.org/etch-backports/libwine-twain)

Why don't you just try your scanner software with Wine, 
and see how that goes ?

Wine can be a bit cumbersome to work with from time to time, but not so long ago it reaches version 1.0 (Out of beta let's say) after 15 years of development (!!).

Here's the Wine application database :
[http://appdb.winehq.org/](http://appdb.winehq.org/)

> 
If I can get that to work...and run World of Warcraft perfectly, I would definitely use it more often.

No idea about that.

There's Cedega and CrossOverGames as commercial windows game "platforms" in Linux.
Here's an entry from the Wine app database :
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=9429](http://appdb.winehq.org/objectManager.php?sClass=version&iId=9429)

PlayOnLinux is a free "games-install-wrapper" for Wine :
[http://www.playonlinux.com/en/](http://www.playonlinux.com/en/)

Here's an example for PlayOnLinux for another game :
[http://www.playonlinux.com/en/topic-2125.html](http://www.playonlinux.com/en/topic-2125.html)

---

### Post by gsocker on 2009-01-02
TWAIN,although it exists for Linux, is pretty much non-existent.
It's not a standard for scanner hardware, it's a software programming interface (API). 
In other words:the manufacturer writes a driver that talks to the scanner. The driver presents a TWAIN interface to applications.This lets application developers write one set of code  and have it work with anything that supports TWAIN.
In Windows it goes scanner driver-twain-program

The standard for Linux is to use the SANE libraries.
Almost all Linux programs which support scanners use SANE; it's become the Linux equivalent of TWAIN.

The supported scanner list is at:
[http://www.sane-project.org/sane-supported-devices.html](http://www.sane-project.org/sane-supported-devices.html)

If your scanner is not in the list, it probably isn't going to be usable in Linux.

---

### Post by xaephod on 2009-01-03
It is listed as unsupported...funny you figure Xerox would be on top of such things.

Ok, so here's another question. I guess I can install a virtual machine like VM ware and run windows from within linux. But, will a USB scanner work with vmware from within linux? :)

Hey its a good question. So if I got to scan something I can pop up the VM and scan then just close it out.

Thanks again for the help. I do not have Ubuntu currently installed, cause if that issue I had last time. But I have a spare box I'm gonna reinstall it on.
thanks again...

---

### Post by albinootje on 2009-01-03
> **xaephod said:**
> I guess I can install a virtual machine like VM ware and run windows from within linux. But, will a USB scanner work with vmware from within linux? :) 

Last time I checked with VirtualBox it was basically like this :
* usb-sticks and usb-disks should be no problem
* don't hold your breath about usb-printers and usb-scanners

---

### Post by gsocker on 2009-01-03
You might see if Vuescan ([www.hamrick.com](www.hamrick.com)) will work with your scanner. Depending on what you are trying to scan, the quality may be better as well - it's excellent for scanning film.

It's not free, but does have a free trial so you could find out if it will work.

---

### Post by xaephod on 2009-01-03
Nope..wont work with my scanner :(

Oh well.

---

### Post by eriqjaffe on 2009-01-03
> **albinootje said:**
> Last time I checked with VirtualBox it was basically like this :
* usb-sticks and usb-disks should be no problem
* don't hold your breath about usb-printers and usb-scannersIt is possible, I do it myself.  It was a bit tricky getting Ubuntu to pass the USB port(s) directly to VirtualBox (there are plenty of forum threads about that), but once it's set up, it works fine.  I can boot up Ubuntu, launch VirtualBox (I just save the state instead of "booting" it) and be scanning quicker than if I had just booted into Windows in the first place.

---

### Post by albinootje on 2009-01-04
Good to hear about this.
What scanner was that with ?

---

### Post by loshadsivaja on 2009-03-12
Twain is yet for Ubuntu too!
see
[http://scantwain.wiki.sourceforge.net]("http://scantwain.wiki.sourceforge.net")

---

### Post by albinootje on 2009-03-12
> **loshadsivaja said:**
> Twain is yet for Ubuntu too!
see
[http://scantwain.wiki.sourceforge.net]("http://scantwain.wiki.sourceforge.net")

Thanks for that link! :)

---

### Post by cartoontycoon on 2012-09-24
How do you install Scantwain?

---

### Post by overdrank on 2012-09-24
[IMG]http://img147.imageshack.us/img147/5451/necromancing.jpg[/IMG]
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

