---
title: "Screen resolution in Virtual Box"
date: 2010-01-22
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Dr. McKay on 2010-01-22
Yesterday, I installed Ubuntu 9.10 on a 15" Dell Inspiron, not booting natively however, but using VirtualBox 3.1.2. 
For the display, I'm stuck in 16-bit mode at 800x600. No higher resolution available (only 640x480).

Any idea how to rectify this ?

---

### Post by squaregoldfish on 2010-01-22
Have you installed the VirtualBox Extensions in the Ubuntu setup? I believe that once you've done this (there's a menu option for it somewhere, but I don't have my copy to hand), you should find that things work a little better.

Steve.

---

### Post by blackened on 2010-01-22
You need the Guest Additions. A simple guide can be found here -> [http://digitizor.com/2009/05/26/how-to-install-virtualbox-guest-additions-for-a-linux-guest/]("http://digitizor.com/2009/05/26/how-to-install-virtualbox-guest-additions-for-a-linux-guest/").

It's a bit old, but all the information should apply to the current version.

---

### Post by Dr. McKay on 2010-01-22
The guide speaks of 1024x768. I need the native resolution of the Inspiron which is a 16:10 resolution. Is that possible?

---

### Post by blackened on 2010-01-22
> **Dr. McKay said:**
> The guide speaks of 1024x768. I need the native resolution of the Inspiron which is a 16:10 resolution. Is that possible?

Enable the Guest Additions and the resolution of the virtual OS will resize dynamically as you resize the virtualbox window. If you choose Machine->Full Screen Mode from the menu, then the virtual OS will take on the same resolution as the host OS.

---

### Post by jcoles on 2010-12-04
> **blackened said:**
> Enable the Guest Additions and the resolution of the virtual OS will resize dynamically as you resize the virtualbox window. If you choose Machine->Full Screen Mode from the menu, then the virtual OS will take on the same resolution as the host OS.

This is NOT true. You can resize the virtualbox window, but the size of the guest screen remains the same. Switching to full screen doesn't change the guest screen area size either. 

Like several other users here, I find the Guest Additions make no difference to the available resolutions of the Guest OS. There's obviously some missing information concerning exactly how to do this installation/configuration, as some people have success and others do not.

---

