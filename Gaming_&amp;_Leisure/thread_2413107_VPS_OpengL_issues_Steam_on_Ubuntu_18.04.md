---
title: "VPS OpengL issues Steam on Ubuntu 18.04"
date: 2019-02-21
forum: Gaming &amp; Leisure
---

### Post by ToulCit on 2019-02-21
Hi, good people of the Ubuntu forums,

It has been a while since I posted anything. I am experimenting with installing steam on a ubuntu VPS 18.04
I have installed the video drivers using the guide on google cloud: [https://cloud.google.com/compute/docs/gpus/add-gpus#install-driver-script](https://cloud.google.com/compute/docs/gpus/add-gpus#install-driver-script)
I have installed the grid drivers since this is a Nvidia P4 virtual workstation GPU.
And drivers are installed properly and lspci shows the right video adapter.
When I access my server via vnc and install and open steam I get: "OpenGL glx extension not supported by display"
I also can not open glxgears.

I also tried another GPU the K80 with Tesla drivers, same issue. Can someone help me with this?

Thank you!

---

### Post by oldrocker99 on 2019-02-21
The very best way to install nVidia drivers is to use the PPA (Personal Private Archive), but first you'll need to purge the old drivers.```
sudo apt remove --purge nvidia*
```
That will, hopefully, get rid of an apparently bad driver installation. Then, do this:
```
sudo add-apt-repository ppa:graphics-drivers/ppa
sudo apt update
sudo apt install nvidia-410
reboot
```
That, hopefully, will set you up.

---

### Post by wsmith198729 on 2019-02-26
> **oldrocker99 said:**
> The very best way to install nVidia drivers is to use the PPA (Personal Private Archive), but first you'll need to purge the old drivers.```
sudo apt remove --purge nvidia*
```
That will, hopefully, get rid of an apparently bad driver installation. Then, do this:
```
sudo add-apt-repository ppa:graphics-drivers/ppa
sudo apt update
sudo apt install nvidia-410
reboot
```
That, hopefully, will set you up.
Thank you, it helps me alot :D

---

### Post by oldrocker99 on 2019-02-26
It's good manners to add [SOLVED] to the header of the thread you started.

Glad I was able to help.

---

