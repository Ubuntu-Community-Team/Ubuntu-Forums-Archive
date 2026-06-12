---
title: "Ubuntu is running in low-graphics mode"
date: 2009-03-27
forum: General Help
---

### Post by rmjohnson144 on 2009-03-27
I am trying to get the nvidia drivers installed so I can do some folding at home.  I download the latest 180.29 from nvidia's main download page and run the sudo sh NVIDIA*.run command and it installs fine.  I even opted for the xconfig setup.  I even manually ran nvidia-xconfig in a terminal and I can't seem to get it to work.

I get a NVIDIA X Server Settings menu in my Applications-->System Tools.  When I bring it up it says I do not appear to be using the NVIDIA X driver.

I have had this working before with a beta 180.17 driver, but haven't been able to get any of the newer versions running.  I have been following the guide over at overclocking.net with no luck either.

[http://www.overclock.net/overclock-net-folding-home-team/436453-how-gpu2-folding-linux.html](http://www.overclock.net/overclock-net-folding-home-team/436453-how-gpu2-folding-linux.html)

I'm hoping there is an alternate way to install this as I'm at my wits end.

Any help will be greatly appreciated.
-=Mark=-

---

### Post by norwoods on 2009-03-27
i update to the latest nvidia proprietary prereleases for 64 bit Ubuntu 8.10 and nvidia 9600GT, 180.41 currently, from [www.avenard.org](www.avenard.org) (third party software source "deb [http://www.avenard.org/files/ubuntu-repos](http://www.avenard.org/files/ubuntu-repos) release/")using System-->Administration-->Synaptic Package Manager.  i am not sure which programs are needed so i install all six provided:
nvidia-180-libvdpau
nvidia-180-libvdpau-dev
nvidia-180-modaliases
nvidia-180-kernel-source
nvidia-glx-180
nvidia-glx-180-dev

you will probably need to uninstall the nvidia drivers that you  have installed

---

### Post by rmjohnson144 on 2009-03-28
It was recommend I run:

sudo apt-get purge nvidia-*

then reinstall again.

I did the purge and rebooted to clear everything out and noticed the nvidia logo during boot and then I got full screen and then when I went to nvidia control panel it says everything was fine.

I then setup folding @ home without any additional installs/setups.

Thanks for the link.  Maybe I'll try those later as they are newer than nvidia's website of 180.29.  Maybe those are beta drivers?

Thanks for the help
-=Mark=-

---

