---
title: "update killed nvidia"
date: 2009-03-29
forum: General Help
---

### Post by Sin@Sin-Sacrifice on 2009-03-29
I thought to mark the thread as SOLVED I had to go to thread tools but its not there... this is SOLVED though

I saw an update for the headers for 2.6.24-24-rc and figured i might as well get'er done after 3 days of postponement and go figure.... it killed the nvidia drivers, Running an on-board 6150 nforce 430 chipset on an m2n board (stock m8000n box...filthy HPs) and hardy studio. I assume the nforce 430 are my realtek hardware because I now have no sound too. I tried reconfiguring xorg.conf... Are there any drivers out there that might work better with this configuration? Or am I just being a dumb stoner and not seeing something here? Also... probably another dumb stoner mistake but I also get "sudo: unable to resolve host Purgatory" after just about every command using sudo on this thing. I dont remember changing anything having to do with a host name... my computer name is purgatory but isnt that "localhost"??!! Weird... I probably messed with something and ****** that up but I'm not sure how to get rid of that. Any ideas?

---

### Post by norwoods on 2009-03-29
the video driver problem is typical of drivers installed some way other than apt or synaptic; updates to the kernel kill the installed drivers.  i update to the latest nvidia proprietary prereleases for 64 bit Ubuntu 8.10 and nvidia 9600GT, 180.41 currently, from [www.avenard.org](www.avenard.org) (third party software source "deb [http://www.avenard.org/files/ubuntu-repos](http://www.avenard.org/files/ubuntu-repos) release/")using System-->Administration-->Synaptic Package Manager.  i am not sure which programs are needed so i install all six provided:
nvidia-180-libvdpau
nvidia-180-libvdpau-dev
nvidia-180-modaliases
nvidia-180-kernel-source
nvidia-glx-180
nvidia-glx-180-dev

---

### Post by Sin@Sin-Sacrifice on 2009-03-29
I installed the drivers originally with apt-get but I'ma try anything at this point 'cuz I miss my eye-candy. I was going to install it through synaptic last night but I got tired. After this movie I'ma try a few things and see what I come up with. Thanks for the reply.

---

