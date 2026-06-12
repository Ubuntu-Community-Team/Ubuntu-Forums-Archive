---
title: "Desktop Display Huge!"
date: 2009-04-26
forum: Desktop Environments
---

### Post by ricecrispys12 on 2009-04-26
I am having a problem with the size of my display screen, its huge and im somewhat new to linux so i was wondering if someone could help. I have restarted it and i believe its one of my drivers not being compatible with one of the updates, any ideas?

---

### Post by ricecrispys12 on 2009-04-26
Its almost compareable to safe mode....

---

### Post by ljerabek on 2009-04-26
Can you provide details about the video card you are using? Have you tried to goto System->Preferences->Display to set your resolution?

---

### Post by roachk71 on 2009-04-26
If you haven't already, try going into your System menu and running the Hardware Drivers manager. You probably have a video card or chipset in your machine which there may be proprietary drivers listed for.

Be sure to select the latest listed driver, since some desktop environments have rendering and other issues with earlier ones. KDM, KDE4's login manager, is especially picky. Once you have the driver you need selected, click the Activate button. Jockey (the restricted drivers manager) will then download, install and activate the driver you need, and you'll have to reboot your machine.

This is necessary, since the driver actually comes as both a kernel module, and a user-mode driver.

:!: If you're using **Kubuntu** and have a problem in which [***KDM unexpectedly exits***]("https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-180/+bug/355202"), just reply to this post about it, and I'll walk you through the steps needed to install and switch to GDM as your login manager. This bug was reported a few weeks ago, and it's being investigated by the package maintainers.

---

