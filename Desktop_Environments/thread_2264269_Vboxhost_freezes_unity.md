---
title: "Vboxhost freezes unity"
date: 2015-02-06
forum: Desktop Environments
---

### Post by Hamburgian on 2015-02-06
I recently tried to install Virtual Box Manager in 14.04 (64 bit), but for some reason (which I can't remember) it wouldn't install and I was pointed to reinstalling the program (virtualbox-4.3_4.3.20-96996~Ubuntu~raring_amd64.deb) directly from [https://www.virtualbox.org/wiki/Linux_Downloads](https://www.virtualbox.org/wiki/Linux_Downloads). Before that I was using the version from synaptic. Everything worked, well kind of!, until a recent update. Now unity freezes as soon as I log in. 
If I remove the Nvidia drivers using > sudo apt-get remove --purge nvidia* (nvidia-304) Unity works OK, but it looks like Win95...very bad screen resolution [1024x768 (4.3)] and my fan on video card whirs like mad.

Previous to removing nvidia
> dkms status returns 
> nvidia-304, 304.125, 3.13.0-45-generic, 86_64
vboxhost, 4.3.20, 3.13.0-45-generic, 86_64

I tried to install virtual box from synaptic but received the following error

> The following packages have unmet dependencies: 

virtualbox-qt: Depends: libgcc1 (>= 1:4.1.1) but 1:4.9.1-0ubuntu1 is to be installed 
               Depends: libqt4-network (>= 4:4.5.3) but 4:4.8.5+git192-g085f851+dfsg-2ubuntu4 is to be installed 
               Depends: libqt4-opengl (>= 4:4.7.2) but 4:4.8.5+git192-g085f851+dfsg-2ubuntu4 is to be installed 
               Depends: libqtcore4 (>= 4:4.8.0) but 4:4.8.5+git192-g085f851+dfsg-2ubuntu4 is to be installed 
               Depends: libqtgui4 (>= 4:4.8.0) but 4:4.8.5+git192-g085f851+dfsg-2ubuntu4 is to be installed 
               Depends: libstdc++6 (>= 4.6) but 4.8.2-19ubuntu1 is to be installed 
               Depends: virtualbox (= 4.3.10-dfsg-1ubuntu2) but 4.3.10-dfsg-1ubuntu2 is to be installed



I'm writing this from a 32 bit 14.04 installation. 
> dkms status returns
> nvidia-173, 173.14.39, 3.13.0-34-generic, i686: installed
nvidia-173, 173.14.39, 3.13.0-35-generic, i686: installed
nvidia-173, 173.14.39, 3.13.0-36-generic, i686: installed
nvidia-173, 173.14.39, 3.13.0-37-generic, i686: installed
nvidia-173, 173.14.39, 3.13.0-39-generic, i686: installed
nvidia-173, 173.14.39, 3.13.0-40-generic, i686: installed
nvidia-173, 173.14.39, 3.13.0-41-generic, i686: installed
nvidia-173, 173.14.39, 3.13.0-43-generic, i686: installed
nvidia-173, 173.14.39, 3.13.0-45-generic, i686: installed
nvidia-173, 173.14.39, 3.2.0-23-generic-pae, i686: installed
nvidia-173, 173.14.39, 3.2.0-60-generic-pae, i686: installed
nvidia-173, 173.14.39, 3.2.0-61-generic-pae, i686: installed
nvidia-173, 173.14.39, 3.2.0-63-generic-pae, i686: installed
nvidia-173, 173.14.39, 3.2.0-64-generic-pae, i686: installed
nvidia-173, 173.14.39, 3.2.0-65-generic-pae, i686: installed
nvidia-173, 173.14.39, 3.2.0-67-generic-pae, i686: installed
nvidia-304, 304.125, 3.13.0-40-generic, i686: installed
nvidia-304, 304.125, 3.13.0-41-generic, i686: installed
nvidia-304, 304.125, 3.13.0-43-generic, i686: installed
nvidia-304, 304.125, 3.13.0-45-generic, i686: installed
virtualbox, 4.3.10, 3.13.0-43-generic, i686: installed
virtualbox, 4.3.10, 3.13.0-45-generic, i686: installed

So instead of vboxhost I have virtualbox 3.4.10...a version installed from synaptic.

I guess the vboxhost is the culprit here. Is there a work-a-round? Or should I remove Vboxhost? If so can anyone point to how to do this from terminal, because it doesn't seem possible using synaptic. or should I uninstall Virtual machine manager?

---

