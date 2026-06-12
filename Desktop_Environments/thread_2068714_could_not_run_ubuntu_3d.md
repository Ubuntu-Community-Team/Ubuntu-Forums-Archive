---
title: "could not run ubuntu 3d"
date: 2012-10-09
forum: Desktop Environments
---

### Post by genIroh on 2012-10-09
Hello!

I'm having problem with running  ubuntu 12.04 in 3d. I was trying compiz, but I couldn't do anything and then, after checking, I found out that I was using Ubuntu in 2d. I checked and on Log On screen I chose Ubuntu , not Ubuntu 2d. To check if hardware is compatible with Ubuntu 3d, upon running ```
/usr/lib/nux/unity_support_test-*p
``` in terminal,I get: 
X Error of failed request: BadRequest (invalid request code or no such operation)
 Major Opcode of failed request: 154(GLX)
 Minor Opcode of failed request: 19 (X_GLXQuerryServerString)
 Serial number of failed request: 22
 Current serial number in output stream: 22

Could this problem be caused by AMD graphics card? I have AMD Radeon 7650M on HP ProBook 4540s. It won't install post-release updates of this driver, installation fails and even driver itself is removed. I'm less concerned about this graphics card problem, if it's possible to run in 3d using integrated graphics card Intel HD 3000, I will be very thankful.

Any ideas how can I run Ubuntu in 3D? I've been looking for hours now, but I was not able to find any solutions. I'm almost desperate. Any kind of help is appreciated.

Thanks in advance,

Saba.

---

### Post by DeceptiveHornet on 2012-10-10
Did you try installing propriatary ATI drivers? Check the Wiki / Installation instructions on the ATI / AMD website and follow those. That's how i got my AMD card working decently.

Edit:
[http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx)

---

### Post by genIroh on 2012-10-11
I have that driver installed from Additional Drivers. There also is one post-release update, but when I try to install it, installation fails and even this driver is removed.

---

