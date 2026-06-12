---
title: "Blank screen after enabling Restricted Drivers"
date: 2007-08-19
forum: Desktop Effects &amp; Customization
---

### Post by jimburt372 on 2007-08-19
I am a newbie deluxe, so please assist with my ignorance.  I searched for this problem, but did not find any results, so forgive me if this is posted elsewhere.

I was going to attempt and setup Beryl and/or Compiz on my Feisty system with an ATI x1300 512 MB PCIe card.

I got as far as enabling the Restricted Drivers.  When I rebooted I lost video once X started.  I can reboot into Recovery mode, but I do not know what to type, or what file to edit, or whatever, to disable the restricted mode driver from the command line.

I am posting this from my other system, so that I can still access the desktop and internet, etc...

Any help will be GREATLY appreciated.

Thanks,

JimmyB

---

### Post by jimburt372 on 2007-08-19
I finally found something that has me back online again.

dpkg-reconfigure xserver-xorg

let me reconfigure the settings that I needed.

Thanks,

JimmyB

---

