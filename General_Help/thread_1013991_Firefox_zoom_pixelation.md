---
title: "Firefox zoom pixelation?"
date: 2008-12-17
forum: General Help
---

### Post by TommyBoy79 on 2008-12-17
I have a widescreen, 1680x1050 resolution, laptop that I run as a dual boot machine with Ibex and Vista (Don't hate me).  When I use the "Ctrl +" feature in firefox to zoom webpages to a usable size the images become pixelated.  This doesn't happen with firefox run in vista. I'm wondering if there is anything I can do about this.  I do not want to turn image zoom off.  I want my images to zoom and look good.  Any ideas?

---

### Post by gtsantos on 2009-03-01
I had this problem too.

Someone knows how we could correct it?

Thanks.

---

### Post by marty4k on 2009-04-14
Apply the following ppa, that will fix it. Hopefully it will be in 9.04 by default.

[https://launchpad.net/~firefox-smooth-scaling/+archive/ppa](https://launchpad.net/~firefox-smooth-scaling/+archive/ppa)

---

### Post by sammm on 2009-04-28
> **marty4k said:**
> Apply the following ppa, that will fix it. Hopefully it will be in 9.04 by default.

[https://launchpad.net/~firefox-smooth-scaling/+archive/ppa](https://launchpad.net/~firefox-smooth-scaling/+archive/ppa)

It seems it's not in 9.04. Could you please tell us what was the problem and how did you fix it?

Thx.

---

### Post by sfr33man on 2009-05-03
Goto [system], [administration], [software sources], enter your password, click on [third party software], [add],then select the version of ubuntu you have from the drop down [here]("https://launchpad.net/%7Efirefox-smooth-scaling/+archive/ppa?field.name_filter=&field.status_filter=published&field.series_filter=jaunty"). cut and paste each line separately starting with 'deb' into the the 'APT line" field.

after you have those, click on the "this repository is signed with" BLAH/BLAH. then click on the blah/_BLAH_, then cut and paste the ENTIRE key including -----BEGIN PGP PUBLIC KEY BLOCK-----, and ending with -----END PGP PUBLIC KEY BLOCK----- into a new file on your desktop. name it whatever.key.

then go back to your software sources window, and click on [authentication], click [import key file] and point it to whatever.key.

then refresh when it asks after your done.

then open a comm[]("http://www.convertecsolutions.com/")and line window and type:

[FONT=Courier New]sudo apt-get upgrade[/FONT]

that will install the packages that were [here]("https://launchpad.net/%7Efirefox-smooth-scaling/+archive/ppa?field.name_filter=&field.status_filter=published&field.series_filter=jaunty").

restart firefox, and viola!

hope that helped.

[convertec]("http://www.convertecsolutions.com")

---

### Post by simoncullen on 2009-05-23
Thank you!  This has been an annoyance for a long time.  

I'm not sure how these kinds of things slip through into major releases.  (Then again, the tracker deamon is still broken, with constant 100% CPU utilization --- a very serious and very common bug.)

---

### Post by tremtastic on 2009-07-14
> **sfr33man said:**
> BLAH/BLAH

Thanks dude. My Firefox now scales nice and shiny too.

:guitar:

---

### Post by simoncullen on 2009-10-18
Is this fix still working?  I've lost smooth image scaling.  I've also tried reinstalling the packages from PPA for firefox-smooth-scaling without any improvement.  Can anyone help?



> **tremtastic said:**
> Thanks dude. My Firefox now scales nice and shiny too.

:guitar:

---

### Post by oversky on 2009-11-02
The owner of that PPA said "I have deleted the xulrunner-1.9 packages.  Please upgrade to firefox-3.5." But the firefox 3.5.3 in Ubuntu 9.10 still have same problem. Any solution?

---

### Post by kswenson on 2009-11-02
Go back to that ppa site and click on "Technical details about this PPA"...
  this will show you the apt line.
I just did it and it works very nicely.

---

### Post by oversky on 2009-11-12
In my Synaptic software manager, it does show that that thjaeger2 patches have been applied. But still no smooth image in the swiftfox 3.5.3

---

### Post by Shlidor on 2010-02-27
This problem is driving me crazy.
I have a very high res screen so I have a defoult zoom in my FF of at least 110%, that meens that without smooth scaling I see ALL the images ALL the time pixelated.
Now every time FF gets updated smooth scaling is lost until I find an update to xulrunner.
any help with the last update (FF 3.5.8) will be appreciated.
BTW This is the only thing keeps me from upgrading to 3.6

---

