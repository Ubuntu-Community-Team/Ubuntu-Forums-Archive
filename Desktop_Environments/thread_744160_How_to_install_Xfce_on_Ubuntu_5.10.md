---
title: "How to install Xfce on Ubuntu 5.10???"
date: 2008-04-03
forum: Desktop Environments
---

### Post by djole_nisam_ja on 2008-04-03
Hi people,

I use **Ubuntu 5.10** on my old laptop and I want to install **Xfce**.

I have tried Xubuntu 6.06 and it's working great but it doesn't see my USB Ethernet device.

Could you help me to install Xfce on Ubuntu 5.10 from Xubuntu CD or if you have some links where I could download Xubuntu 5.10.

Thanks

---

### Post by warp99 on 2008-04-03
Ubuntu 5.10 is deprecated and unsupported:

[http://www.ubuntu.com/news/Ubuntu-5.10-end-of-life](http://www.ubuntu.com/news/Ubuntu-5.10-end-of-life)

So basically you are running an **unpatched system**. You need to either install Xubuntu gutsy 7.10 or Hardy 8.04 beta:

[http://xubuntu.org/](http://xubuntu.org/)

---

### Post by djole_nisam_ja on 2008-04-03
It's impossible, cause this laptop is way too old for any Ubuntu except 5.10 or Xubuntu 6.06.

So help plz.

---

### Post by warp99 on 2008-04-03
You can install the newer version without a problem. You may need to turn off some services that are installed, but other then this extra step there is no reason the newer version will not run. 

If the laptop is **very** old with low specs then I would suggest not using **any** flavor of Ubuntu and install Puppy Linux instead:

[http://puppylinux.com/](http://puppylinux.com/)

BTW what are the specs on your computer?

Edit:

Here are the **recommended** requirements for the various installations:

[https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)

Remember these are not etched in stone, they're just "soft" guidelines. Look how low the specs for Xubuntu are:

[https://help.ubuntu.com/community/Installation/SystemRequirements#head-1e8a8a2a2221583a5ce5a57a242f72b623469815](https://help.ubuntu.com/community/Installation/SystemRequirements#head-1e8a8a2a2221583a5ce5a57a242f72b623469815)

---

### Post by djole_nisam_ja on 2008-04-03
I have tried Puppy Linux and I have some problems with booting cause I use PCMCIA on this old laptop. Same problem with Vector, DSL,...

The only OS that has no problem with that is (X)Ubuntu.

I also tried Xubuntu 7.10 and it's way too slow even if laptop fits minimum requirements.

I have tried Xubuntu 6.06 and it's working good, but this version doesn't see my cable TV internet modem (Scietnific Atlanta)

and Ubuntu 5.10 can see it with no problem.

So I wanted to install Ubuntu 5.10 and then to install Xfce and get Xubuntu 5.10.

Can anyone help me deal with it.

---

### Post by warp99 on 2008-04-03
Here are the problems with running Breezy (5.10). 

1) There are no updates available since all of the repositories have been removed, so when you install the operating system any exploit that has been known since it's release in October 2005 will be available to all the script kiddies throughout in the internet. 

2) Breezy is bug ridden compared to Gutsy (7.10) or even Dapper (6.06). It would be better to install Gutsy then turn off all of the unnecessary services to speed up the system. Here is a thread to show you how:

[http://ubuntuforums.org/showthread.php?t=89491](http://ubuntuforums.org/showthread.php?t=89491)

At the minimum you should install 6.06 LTS and get the cable modem working since 6.06 at least gives you updates until June 2009 The most likely cause of your problem with the cable modem is that you have to enable the roaming properties in the network manager so you can get an IP from your vendor.

You should also try fluxbuntu:

[http://fluxbuntu.org/](http://fluxbuntu.org/)

It's the current version of Ubuntu with the Fluxbox desktop, which is much faster then Xubuntu. At least you'll have a current patched version.

---

### Post by Nymrat on 2008-05-02
Hello warp99,

The way I installed Xfce4 on top of a normal Ubuntu installation
was to use the alternate install CD, feisty fox, if that's important, which has the desktop packages.

If you have the live CD it won't help you, because the desktop is installed onto the disk and does *not[I]*[/I] contain the packages you need.

The disk should be recognized as a CD repo and load Synaptic, then you just select xubuntu-desktop-meta and it should sort itself out from there.

In my case it had issues with the disk for some reason and I had to install it package by package. ;) (the packages are in /media/Xubuntu7.10/pool/)

Hope this is helpful!

---

