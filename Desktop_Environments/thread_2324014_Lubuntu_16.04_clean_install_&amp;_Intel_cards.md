---
title: "Lubuntu 16.04 clean install &amp; Intel cards"
date: 2016-05-10
forum: Desktop Environments
---

### Post by vasa1 on 2016-05-10
[From Lubuntu's dev]("https://plus.google.com/114536168681668531284/posts/AcTu9Kmep3o"):


> Julien Lavergne 
17:27 (55 minutes ago)
to lubuntu-devel 
Hi,
Looks like we may have a problem with Intel users after all.
I checked the difference between xubuntu and lubuntu ISO, and this
package is missing :
xserver-xorg-video-intel
Intel cards was supposed to work without this package, but according
to the package description, it is only the case for new cards.
[B]If you have people affected by black screen, or no X starting, or no
lightdm starting, with Intel card, could you advise them to install
this package, reboot, and see if it's working (and report back)[/B] ?
This should affect only fresh install, upgrade should be fine (as this
package was included in previous releases).
Thanks in advance for your reports.
Regards,
Julien Lavergne&#65279;

---

### Post by QDR06VV9 on 2016-05-10
> **vasa1 said:**
> [From Lubuntu's dev]("https://plus.google.com/114536168681668531284/posts/AcTu9Kmep3o"):
Nice find vasa 1 and thanks for the share.:)

---

### Post by sudodus on 2016-05-11
Yes, Lubuntu works better with Intel graphics after you install **xserver-xorg-video-intel** :-)

```
sudo apt-get install xserver-xorg-video-intel
```

See this link: [Re: Lubuntu 16.04 flashing cursor with certain Intel video drivers](http://ubuntuforums.org/showthread.php?t=2321734&p=13486996#post13486996) concerning old Intel graphics chips, like **945** series.

-o-

I have also good experiences using this intel package in an old IBM Thinkcentre 8187-73G (with a Pentium 4 CPU and) with Intel 82865G graphics.

I needed nomodeset for the graphics to work with Lubuntu 16.04 LTS, but now it works without any tweaks. The /etc/X11/xorg.conf file with the UXA tweak was renamed by the installation (and hence made inactive).

So **xserver-xorg-video-intel** works with Intel **82865G** graphics too.

---

