---
title: "Screen resolution?"
date: 2005-10-21
forum: Desktop Environments
---

### Post by hitman012 on 2005-10-21
Hi all,

I decided to install Ubuntu on my old P3 machine today to delve into the world of Linux. Slapped an extra 256MB of RAM into it and replaced the old card with a newer (relatively speaking, anyway:p ) GF4 MX440. Installation was lengthy, but once I got into the UI, I realised it was worth the wait.

I'm still exploring, and I'm impressed, but there's one niggling problem - screen resolution. I'm sure that this card is capable of 1280x1024 (the native res of my LCD) and I've installed the nvidia-gtx thing in the Synapse Package Manager, but I cannot select a resolution of above 1024x768.

Is this my fault (likely) or some limitation of my graphics card/OS?

Thanks very much in advance,
Jack

---

### Post by migueljacq on 2005-10-21
You just need to reconfigure your resolution settings. It's just a configuration thing and not your fault.

Type **sudo dpkg-reconfigure xserver-xorg** into your terminal and carefully follow the steps

---

### Post by jonesy on 2005-10-21
One possibility is that your monitor is not identifying properly what resolutions it is capable of.  This is usually done with the EDID tags that the drivers should pull from the monitor, though they are not always accurate.  The /etc/X11/xorg.conf file allows you to manually specify these ranges which you can usually find on the manufacturer's web page.

---

### Post by hitman012 on 2005-10-21
Thanks for the prompt replies. I'll give those a try.

---

### Post by hitman012 on 2005-10-21
Excellent - I tried the console command and it worked just great. Now enjoying Ubuntu in crisp 1280x1024 - thanks guys :)

---

