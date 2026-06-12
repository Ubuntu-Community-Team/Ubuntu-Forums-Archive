---
title: "No sound after suspend on a Vostro 1400? I've got your fix."
date: 2007-12-08
forum: Dell  Ubuntu Support
---

### Post by aldenhg on 2007-12-08
I'm assuming that you've got your sound already working. If you haven't, search the forums - the answer is out there! 
It turns out that simply recompiling the drivers does the trick. The only thing is you have to tell it to compile them with the intel-hda drivers. It's a lot easier than it sounds. First off, make sure you have build-essential installed. There might be some other necessary libraries, so you'll have to deal with those errors as they come. Just cut and paste these commands one by one.
```
sudo apt-get install build-essential
wget ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.15rc1.tar.bz2
tar zxvf alsa-driver-1.0.15rc1.tar.bz2
cd alsa-driver-1.0.15rc1
./configure --with-cards=hda-intel
make
sudo make install
sudo reboot
``` 
What you're doing here is installing build-essential, downloading the ALSA source, uncompressing the ALSA source, configuring the ALSA source, building the drivers, installing the drivers and then rebooting. It should all work, but if it doesn't you'll have to get help from someone smarter than me. I can never track down compile errors.
BTW, this is on 7.10 with the 2.6.22-14-generic kernel.

---

