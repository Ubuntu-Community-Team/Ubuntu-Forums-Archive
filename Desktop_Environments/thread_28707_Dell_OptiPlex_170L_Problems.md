---
title: "Dell OptiPlex 170L Problems"
date: 2005-04-21
forum: Desktop Environments
---

### Post by Ubuntu Warrior on 2005-04-21
After having huge success with Warty I decided to install Hoary onto our new Dell OptiPlex 170L desktops at work to test. After this experience it seems that there are serious flaws with this version.

Firstly I could not specify a proxy server when installing so had to abort attempt number one and scan the net for a solution. Right! Press F2 and force the install - this worked ok.

Second I can not get the system to update from the repositories - apt-get just complains about 403 errors and a load of stat problems. No fix for that yet!!!

Third, it seems that xorg doesn't properly support the Intel Extreme Graphics 2 stuff (have a Dell E153FP 15in flat panel). Locks the system in 640x480 mode which cannot be changed.

Have just reverted back to Warty...

---

### Post by Ubuntu Warrior on 2005-04-26
Installing Warty and then upgrading to Hoary with

apt-get update
apt-get dist-upgrade

on the Dell OptiPlex 170L system seems to work great!  :-)  Typing this response with a new Hoary foundation for my system. Hopefully the Hoary install ISO can be improved/fixed for future users - just still shows that Linux is STILL not for the average user. Sigh! :-(

Had some initial troubles with the corporate proxy but then sorted that by setting the env variables http_proxy, HTTP_PROXY and FTP_PROXY. Hope that stays fixed.

---

### Post by shakin on 2005-04-26
I installed Hoary on a Dell Optiplex GX280 with integrated Intel 915 graphics and an E17FP 17" LCD display. Xorg defaulted to vesa graphics, but correctly chose the resolution. I did a how-to for using the i810 driver for i810 and higher integraged video chipsets, including fixing the resolution problem that you might be experiencing if you use the i810 driver. In fact, I almost guarantee that if you are not experiencing problems getting your resolution higher than 640x480 then you are using a vesa driver.

---

### Post by fabio_mazzarino on 2005-12-27
Although most problems solved, Optiplex 170L here doen't seem to work completely.

 Basically I have some difficulties in configuring 1024x768 video. I can configure it but screen seems to be smaller than the selected resolution, so I always need to scroll desktop.

  Basically it only happens when using xorg. When using xfree it doesnt' seems to have any problem.

 No solution yet.

 Fabio.

---

