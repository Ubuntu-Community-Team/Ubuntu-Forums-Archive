---
title: "Is the XPS M1330 completely linux friendly?"
date: 2008-07-30
forum: Dell Ubuntu Support (CLOSED)
---

### Post by duffman25 on 2008-07-30
Hi

I'm thinking about buying the dell XPS M1330 (with ubuntu) and my question is, if I buy the one with intel graphics and bluetooth chip inside will it run ANY linux distro (fedora or debian)? i.e. Does it need some propietary drivers or binary only firmware? (the wifi card, camera, etc)

I'm tired of buying machines which need some kind of binary/propietary driver.

Thanks

---

### Post by crasherkid on 2008-07-30
Hi, I self installed Ubuntu 8.04 just a week ago on my XPS M1330, and while I've been sorting a few things out, the installer automatically recognised my wireless card, and installed with a breeze! The inbuilt graphics card (I have the default one) is easily enough to do any eyecandy flashy stuff, I've been quite impressed.

If you're installing with Vista preloaded I'd recommend partitioning from Windows first, as the drive fills up quick (some space is reserved for something >100GiB on my machine, don't know why) so you can accurately know how much space you have to work with. This is where experts jump in...

If not then you'll be fine absolutely no problems!

Hope that was helpful

---

### Post by sultanoswing on 2008-07-31
8.04 64-bit runs just fine on my 1330 - wireless (4965), graphics (8400M), webcam, microphone and sound all work pretty much out of the box, give or take a couple of tweaks. 

The powersaving tips are worthwhile, as is the tweak to keep the NVIDIA card at full speed while on AC power, both of these tweaks can be found on this Dell Ubuntu forum. 

As far as proprietary drivers go, I do confess to using the NVIDIA package from the NVIDIA site, so can't comment on the open source alternative. If you purchase the machine with the X3100, then I'm not sure what the situation is. One issue is that the HDMI port will output video but not sound. Apparently NVIDIA is working on a fix in upcoming drivers, but this hasn't seen the light of day, as far as I know. Again, I'm not sure about the X3100's use of the HDMI output.

I wiped Vista after it's first boot, and repartitioned the entire drive - thankfully Dell is no longer hiding the media partition, so the mediadirect button is now rendered harmless (it used to helpfully overwrite your established partition table).

I don't bother with suspend etc, but I understand that works OK too.

I briefly tried Fedora 9 on it, and it installed fine, but I didn't keep it around long enough to see if everything worked (the inability to change the default login screen was just the first of a number of annoying features of F9). I also compiled my own Ubuntu kernel and was up and running OK (having copied the lib>firmware drivers from the default install into the new kernel's folder). I don't doubt that my new distro of choice, Arch, would also run fine.

Good luck - it's a great laptop and about as linux-friendly as they come!

Ubuntu:
[https://wiki.ubuntu.com/InstallingUbuntuOnADellXPSM1330](https://wiki.ubuntu.com/InstallingUbuntuOnADellXPSM1330)

Gentoo:
[http://linux.manjos.com/dell/](http://linux.manjos.com/dell/)

Fedora 8:
[http://alumnus.caltech.edu/~hamkins/M1330_fedora_8.html](http://alumnus.caltech.edu/~hamkins/M1330_fedora_8.html)

OpenSuse 10.3:
[http://john.leidel.googlepages.com/opensuse10.3ondellxpsm1330](http://john.leidel.googlepages.com/opensuse10.3ondellxpsm1330)

Slackware:
[http://intr.overt.org/blog/?page_id=56](http://intr.overt.org/blog/?page_id=56)

---

### Post by duffman25 on 2008-07-31
Thanks everyone. I think I'll end up buying it.

---

### Post by Technoviking on 2008-07-31
I got one six months ago and it is the best Linux experience I have ever had. Be sure to get a Intel wireless card, much easier to config.

---

### Post by superm1 on 2008-07-31
> **duffman25 said:**
> Hi

I'm thinking about buying the dell XPS M1330 (with ubuntu) and my question is, if I buy the one with intel graphics and bluetooth chip inside will it run ANY linux distro (fedora or debian)? i.e. Does it need some propietary drivers or binary only firmware? (the wifi card, camera, etc)

I'm tired of buying machines which need some kind of binary/propietary driver.

Thanks
All changes are available upstream for all improvements made on the 1330.  This doesn't mean that other distros have picked them up yet however.  In other words, you will have a much much better experience if you use Ubuntu.  Also if you are with the broadcom card that ships in this, Ubuntu is the only one carrying the driver for it.

---

### Post by badrunner on 2008-07-31
Mine just arrived today (with vista business preinstalled, i need the license for various reasons). 

I did a hardy install, and also added the dell ppa and installed the linux-modules-backports package to get the wireless light working.

All in all the machine works great, very very easy setup, and beyond adding the dell extras i've done nothing at all from a default hardy install to have everything working well.

I do have the nvidia graphics option, rather than the intel graphics which i imagine would be even better supported with things like the xrandr 1.2 support.

This is easily the nicest laptop i have ever used (a title which i would have previously awarded the various macs). I've had a few hours playing with the vista install, and all i can say that is a complete train wreck of an operating system, but as a linux system this is absolutely great.

---

### Post by n00blar on 2008-07-31
Hmm, I have this same laptop and Ubuntu didn't recognize wireless and sound cards.
None of the top buttons don't lit up, the fan is noticeable loud and power savings doesn't work at all.

I wonder if I messed something up during the install, but I don't know what.

---

### Post by fsando on 2008-08-01
I just installed  8.04 on my new xps 1330. The only problem I've experienced so far was that it didn't see my wireless at all - It was easily fixed though, by turning it on with the switch on the right side of the laptop :redface:

But something really have me thinking now.

I have three laptops now all running Ubuntu: 
One is almost 5 years old, Core Solo 1.3 Ghz integrated Intel gma 950 graphics.
One is just about 2 years old Core Duo 2Ghz with ATI x1600.
and the last one: xps m1330 2.1 Ghz with integrated intel x3100.

They all run Compiz with a quite a few of the bells and whistles without problems. 

The 5 year old is a bit jumpy in the more demanding animations (such as the new sphere plugin) it looks a bit cheep but by no means unacceptable. When I stress it (like spinning the sphere around for some time) it doesn't get particular hot.

The 2 year old (the one with dedicated graphics) runs Compiz much smoother than the 5 year old but whenever I spin the cube/sphere or wobble a little with a window etc. both cores immediately go to max speed and the temperature goes towards 80-90 Celsius. The processors stays at top speed as long as I do any Compiz animation.

On the new xps Compiz animations are smoother than on the 2 year old, it barely notices that compiz is running even when I spin the cube/sphere or I wobble wildly with the windows.

So what gives???

My conclusion is (I'm no expert so this is pure guessing) that dedicated graphics cards are only good for dedicated applications specifically programmed for those graphics processors (like games). Other apps not programmed with dedicated graphics in mind are actually worse off. I'm even speculating that those high end cards may be emulating 2D features making them even worse for 2D apps (ie office and Internet etc).

So if you are going to buy a laptop you don't intend to use as a gaming machine I'd suggest you do a thorough research as to what advantages a dedicated graphics card actually brings to non-gaming applications.

In my experience the machine with the dedicated ati x1600 performs decidedly worse than the intel x3100 on a similarly specced machine and though it, of course, performs a lot better than the oldest one it gets screaming hot in the process.

One last note:

TheInq says don't buy any Nvidia card
[TheInq on Nvidia]("http://www.theinquirer.net/gb/inquirer/news/2008/07/09/nvidia-g84-g86-bad")

---

### Post by n00blar on 2008-08-01
Ahh, I just realized something...you guys have an Intel wireless card on your M1330s...I, on the other hand, have a Broadcom wireless card. That's what's causing Ubuntu not to find my wireless card.
It appears that broadcom drivers are not open source drivers, so I must do something else (which I'm still trying to figure out)

---

### Post by duffman25 on 2008-08-01
> **superm1 said:**
> All changes are available upstream for all improvements made on the 1330.  This doesn't mean that other distros have picked them up yet however.  In other words, you will have a much much better experience if you use Ubuntu.  Also if you are with the broadcom card that ships in this, Ubuntu is the only one carrying the driver for it.

I was thinking about buying it with ubuntu preinstalled, but I wanted to know if there was any non-free stuff (restricted drivers).

You mean a broadcom wireless card? The dell web page says it brings intel Pro Wireless 3945 802.11a/b/g. Is the broadcom driver free in ubuntu free?

thanks

---

### Post by sultanoswing on 2008-08-07
> **fsando said:**
> 

On the new xps Compiz animations are smoother than on the 2 year old, it barely notices that compiz is running even when I spin the cube/sphere or I wobble wildly with the windows.

So what gives???

My conclusion is (I'm no expert so this is pure guessing) that dedicated graphics cards are only good for dedicated applications specifically programmed for those graphics processors (like games). Other apps not programmed with dedicated graphics in mind are actually worse off. I'm even speculating that those high end cards may be emulating 2D features making them even worse for 2D apps (ie office and Internet etc).

So if you are going to buy a laptop you don't intend to use as a gaming machine I'd suggest you do a thorough research as to what advantages a dedicated graphics card actually brings to non-gaming applications.

In my experience the machine with the dedicated ati x1600 performs decidedly worse than the intel x3100 on a similarly specced machine and though it, of course, performs a lot better than the oldest one it gets screaming hot in the process.

One last note:

TheInq says don't buy any Nvidia card
[TheInq on Nvidia]("http://www.theinquirer.net/gb/inquirer/news/2008/07/09/nvidia-g84-g86-bad")

There's a post somewhere on the forums here, if I recall, which tells how to ensure your graphics card is running at full speed. Laptops often disable the card to 'power saving' modes to save on battery drain - and this state may persist even when under AC power.

My NVIDIA 8400M was also running compiz a bit stuttery until I implemented a few of the tweaks mentioned - now all is smooth as silk (at least with AC power!).

---

### Post by fsando on 2008-08-08
> **sultanoswing said:**
> There's a post somewhere on the forums here, if I recall, which tells how to ensure your graphics card is running at full speed. Laptops often disable the card to 'power saving' modes to save on battery drain - and this state may persist even when under AC power.

My NVIDIA 8400M was also running compiz a bit stuttery until I implemented a few of the tweaks mentioned - now all is smooth as silk (at least with AC power!).

Thanks - haven't found it yet. 
Anyway (this is my 2-year old laptop) it gets burning hot so either it is running full speed or if it isn't I don't dare think what happens when I tweak it to do. Normal running temparature is 57 Celsius, with Compiz 60 Celsius, with Compiz and doing various animations (turning the sphere, wobbling some windows y'know, impressing the gals in the local pub) it runs close to 90 Celsius within a couple of minutes.

But now I've got another problem with my xps 1330: 
Just discovered that the firewire doesn't work. 

I think it should work - I haven't found any reference to it not working, though there is one ref to another Dell laptop with a non-working firewire.

---

### Post by jbor7755 on 2008-08-24
I currently have almost everything up and running with kubuntu 8.04.1 64bit except for sound.

Has anyone found a tweak/fix for this problem?

---

### Post by sdennie on 2008-08-25
I would also highly recommend this laptop.  I have the Intel wireless and nvidia graphics combo and have been very, very pleased with the machine.  It should run fine out of the box with Ubuntu but, with some easy tweaks (some of which can be found in my signature), it runs even better.

My only complaint about the machine is that after 2300 hours of usage, the brushed metal is starting to flake off the palm rest a bit.  Hopefully no one from Dell is reading this thread because I intend to try to get a replacement chassis just before the warranty runs out.  ;)

---

### Post by rykel on 2010-10-08
My Dell XPS M1330 comes with the Intel PRO wifi adaptor and while Ubuntu Lucid can detect it and even use it to see my wifi network, it CANNOT connect to it.

I think the other thing NOT working is the card reader - not too sure about that!

---

