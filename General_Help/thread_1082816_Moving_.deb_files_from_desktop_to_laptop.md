---
title: "Moving .deb files from desktop to laptop"
date: 2009-02-28
forum: General Help
---

### Post by tuope on 2009-02-28
Hi, all!

I have a desktop machine (running Ubuntu 8.10) that is connected to Internet, and a laptop machine (running Ubuntu 8.10) not connected to the net. I use this laptop for offline tasks, but never the less I would like to install some additional software that wasn't part of the default install but that is available through apt-get. I have already installed this software on my desktop machine.

I have noticed that Ubuntu package management system stores .deb files into /var/cache/apt/archives. Would it mess up the package management system on my laptop if I simply copied these .deb files into a USB stick and then run (on this laptop) 'dpkg --install' (or some such command) on them?

Bottom line, since I have downloaded all the software I want and all security updates once already, I would like to install all this software on my laptop AND, if possible, save some bandwidth. I just dont know how that can be done. Any help and/or tips are appreciated!

Tuomas

---

### Post by taurus on 2009-02-28
You can use the APTonCD, [http://en.wikipedia.org/wiki/APTonCD](http://en.wikipedia.org/wiki/APTonCD).

---

### Post by tuope on 2009-02-28
Thank you for the quick reply! I will check that out.

Tuomas

---

### Post by tuope on 2009-02-28
I used APTonCD to create an .iso file, then burned it on a DVD. I switched on the laptop, restored the media as instructed in APTonCD user guide. So I have all the files in /var/cache/apt/archives. Now the question is how do I install them?

'sudo dpkg -i *.deb' maybe?

Tuomas

---

### Post by taurus on 2009-02-28
If you want to run that command, then make sure you are in /var/cache/apt/archives directory first or it will complain about no *.deb files found.

---

### Post by tuope on 2009-02-28
I will. :) Thanks again, Taurus. I appreciate your help.

---

