---
title: "Suspending on Dell M1210"
date: 2007-08-13
forum: Dell  Ubuntu Support
---

### Post by Thucydides411 on 2007-08-13
I just set up my M1210 laptop to dual-boot Vista and Ubuntu 7.04. Everything is working fine, with the exception of suspending and hibernating.

When I suspend or hibernate, the screen goes black as expected and the power lamp turns off. I then tap the power button to wake it up, and the backlight turns back on and the mouse appears, but nothing else happens. Sometimes, a small striped box appears on the screen where the mouse began. When I press enter, the mouse temporarily turns into the "busy" wheel. I've tried typing my username, pressing enter, and typing my password and pressing enter, but to no avail. I've also tried typing just my password and pressing enter, but that doesn't work either.

I'm using the restricted "NVIDIA accelerated graphics driver" and the "Intel(R) PRO/Wireless 3945 Network Connection driver for Linux," and have wobbly windows and the cube activated.

Getting suspend and hibernate to work is a priority for me, as it would allow me to get more use out of the Ubuntu side of my laptop when I'm not 5 feet from a power outlet.

Thanks in advance for the help.

---

### Post by SeanHodges on 2007-08-13
Does the suspend/hibernate work with the desktop effects (wobbly windows/cube) turned off? Or with the Nvidia driver disabled in the Restricted Drivers Manager?

If so it sounds like the proprietory Nvidia driver you are using is having problems with suspend/hibernate. I'm not sure how to fix this problem, although someone else might. The immediate solution would be to turn off the desktop effects for now. You try upgrading to the latest Nvidia driver (search the Ubuntu wiki, i've seen it there somewhere). The problem with issues 

If turning off the desktop effects and Nvidia driver do not fix the hibernate/suspend problem you might be onto a bug for your Laptop model, it might be worth looking in Launchpad for any similar reported bugs.

---

### Post by beren.olvar on 2007-08-13
take a look here

[http://blog.paulbetts.org/index.php/2007/02/11/fixing-software-suspend-hibernate-with-uswsusp-in-ubuntu-feisty-and-edgy/]("http://blog.paulbetts.org/index.php/2007/02/11/fixing-software-suspend-hibernate-with-uswsusp-in-ubuntu-feisty-and-edgy/")

gl

---

