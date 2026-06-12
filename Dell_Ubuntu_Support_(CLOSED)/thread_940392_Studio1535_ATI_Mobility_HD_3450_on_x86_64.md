---
title: "Studio1535 ATI Mobility HD 3450 on x86_64"
date: 2008-10-07
forum: Dell Ubuntu Support (CLOSED)
---

### Post by strm on 2008-10-07
Hi,
I am attempting to get everything working on my Dell Studio 1535 laptop after a recent installation of Ubuntu x86_64. I am currently in the process of fixing the video card driver on the laptop. The video card is the 256MB ATI Radeon Mobility HD 3450.

I've downloaded the Linux x86_64 - Radeon - ATI Radeon 3xxx series driver from < [http://ati.amd.com/support/driver.html](http://ati.amd.com/support/driver.html) >, and installed it and before realizing I needed the Mobility driver (which actually doesn't exist on that page). I've added a 1280x800 display mode to /etc/X11/xorg.conf so my display looks fine. However, when I go to System > Administration > Hardware Drivers there is an "ATI accelerated graphics driver" that is not enabled but is in use. When I try to enable it, I get the following error:
```

W: Failed to fetch
http://security.ubuntu.com/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.24/xorg-driver-fglrx_7.1.0-8-3+2.6.24.13-18.41_amd64.deb
 404 Not Found

```
I am wondering if there is Radeon Mobility driver out there for linux x86_64 or if I should just live with the driver I installed.

Thanks.

---

### Post by wdaim on 2008-10-12
i have the machine with the same card, i installed the x86 version only (the one abve the one you installed on the list) all works fine for me, getting 1280x800 resolution and have compiz effects and hardware drivers installed.

---

### Post by strm on 2008-10-13
I've reinstalled Ubuntu after several days of fighting with the problem, and did a clean install of the proprietary driver (both Linux and Linux 64 on the AMD site actually point to the same x86_64 driver). Added the 1280x800 mode to my xorg.conf and had no problems for about half an hour. Then I ran a package upgrade (i.e. apt-get upgrade, apt-get update). After rebooting I was no longer able to even login with X running. After typing my username/password I just got a tan blank screen with a cursor.

My attempts to restart X (/etc/gdm stop/start) as well as reconfigure X (dpkg-reconfigure -phigh xserver-xorg) did not do any good.

Any and all ideas would be appreciated

---

