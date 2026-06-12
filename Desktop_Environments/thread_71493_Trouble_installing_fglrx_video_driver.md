---
title: "Trouble installing fglrx video driver"
date: 2005-10-03
forum: Desktop Environments
---

### Post by CastorTroy on 2005-10-03
Hi,

My X server won't start, so I went install fglrx:
sudo apt-get install xorg-driver-fglrx

and I got an error saying:
error processing: /var/cache/apt/archives/xorg-driver-fglrx_6.8.0-8.8-25_0ubuntu_amd64.deb

here is my log file

Does anyone know how I can fix this?

---

### Post by CastorTroy on 2005-10-04
bump...

Does anybody have any clue? I really need to get Linux running, so that I don't have to drive to campus to be able to do my homework!

---

### Post by floyd27 on 2005-10-04
if your stuck in a command prompt area you can do this to get back into a GUI enviro..

dpkg-reconfigure xserver-xorg

---

### Post by CastorTroy on 2005-10-04
I have tried that already. However, the problem is that my video card drivers aren't installed. And when I try to install them, I get the error I mentioned above.

---

### Post by floyd27 on 2005-10-05
when you are configuring the xserver as i wrote above..
dont select the "fglrx" for the driver ..
Use the ati one in the list.
This will use the mesa drivers, with no 3d..
It should get you going anyway.

---

### Post by psychicdragon on 2005-10-05
Strangely the fglrx driver seems to have been removed from the repos.

I did a quick google for the package name and found this: [http://mirror.stanford.edu/yum/pub/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.10/](http://mirror.stanford.edu/yum/pub/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.10/)
Seems like someone mirrored all the packages that were removed.

No guarantee that it'll work or anything but you should be able to download it and try at least.

---

### Post by CastorTroy on 2005-10-09
I have tried everything  you guys mentioned. I also just upgraded to 5.10 and I heard it was supposed to have the right drivers for me, but it didn't, I went through the same process and it doesn't work. It still says the Xserver won't start becauase "no screens found"

---

