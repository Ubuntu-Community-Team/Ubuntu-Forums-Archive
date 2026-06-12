---
title: "Nvida and Wifi Help"
date: 2009-03-20
forum: General Help
---

### Post by 0per4t0r on 2009-03-20
I'm having a little trouble with ubuntu.

First, I can't really get the wireless to work with my AT&t 2wire gateway, and the only way it works is if I plug in the ethernet cable from the gateway to the laptop. When I try to connect, it rejects my WEP code, and it can't establish a secure connection I'm a dual-booter, so I have Windows if that helps. (It works fine with windows)

Also, my nvida graphics driver won't work even if I try to enable it. (Again, works on windows)

Otherwise, ubuntu is awesome!

Specs:
Compaq PC
Ubuntu 8
Windows Vista (Came with the laptop, sadly.)

---

### Post by 0per4t0r on 2009-03-23
Bump!

---

### Post by norwoods on 2009-03-23
i update to the latest nvidia proprietary prereleases for 64 bit Ubuntu 8.10 and nvidia 9600GT, 180.41 currently, from [www.avenard.org](www.avenard.org) (third party software source "deb [http://www.avenard.org/files/ubuntu-repos](http://www.avenard.org/files/ubuntu-repos) release/")using synaptic package manager.  i am not sure which programs are needed so i install all six provided:
nvidia-180-libvdpau
nvidia-180-libvdpau-dev
nvidia-180-modaliases
nvidia-180-kernel-source
nvidia-glx-180
nvidia-glx-180-dev

---

### Post by 0per4t0r on 2009-03-30
> **norwoods said:**
> i update to the latest nvidia proprietary prereleases for 64 bit Ubuntu 8.10 and nvidia 9600GT, 180.41 currently, from [www.avenard.org]("http://www.avenard.org") (third party software source "deb [http://www.avenard.org/files/ubuntu-repos](http://www.avenard.org/files/ubuntu-repos) release/")using synaptic package manager.  i am not sure which programs are needed so i install all six provided:
nvidia-180-libvdpau
nvidia-180-libvdpau-dev
nvidia-180-modaliases
nvidia-180-kernel-source
nvidia-glx-180
nvidia-glx-180-dev


That fixed it!
I fixed the wifi problem myself, so thanks!

---

