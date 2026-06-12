---
title: "Epic Problems with Desktop Computer"
date: 2008-09-20
forum: Desktop Environments
---

### Post by iandotcom on 2008-09-20
I've been having problems getting my computer set up with Ubuntu properly.

I'm using a Dell Dimension 9150 that I got a couple of years ago, I've tried to put Ubuntu 8.04 on, and I've managed to get it working to some extent but not without some features not working correctly.

One of my main problems was getting ALSA to work with my Creative X-fi soundcard. I got that working through making a custom kernel, but I've needed to manually install the Nvidia GeForce 6800 drivers from their website, and custom compile ndiswrapper for my wireless internet adapter.

Three of my main problems are these, and I'm wondering if anyone can help me out with them:

* The startup sound doesn't play.
* When I try to use my USB DVB device, it crashes.
* Theres this dodgy problem with titlebars.

On the case of the USB DVB device, I copied a file called "dvb-usb-avertv-a800-02.fw" into /lib/firmware/2.6.24.3-custom, which corresponds to the type of TV tuner I have. I found that there was an error loading the firmware before that by looking in the System Log, but placing that file into that folder switched on the device.

On the case of the titlebar, I've tried a lot of suggestions for editing /etc/X11/xorg.conf that I've found with Google, but none of them seem to work. I've included a link to a screenshot that shows whats up..

[[IMG]http://img513.imageshack.us/img513/6489/screenshotqe2.th.png[/IMG]](http://img513.imageshack.us/my.php?image=screenshotqe2.png)[[IMG]http://img513.imageshack.us/images/thpix.gif[/IMG]](http://g.imageshack.us/thpix.php)

It worked fine with the nvidia drivers that you get with Ubuntu, but these don't work because of the custom kernel.

Any help would be much appreciated with any of these problems, thanks a bundle..

-- Ian.

---

