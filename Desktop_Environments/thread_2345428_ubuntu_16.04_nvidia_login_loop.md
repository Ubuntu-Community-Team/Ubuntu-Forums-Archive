---
title: "ubuntu 16.04 nvidia login loop"
date: 2016-12-04
forum: Desktop Environments
---

### Post by Gijsbert_Wiesenekk on 2016-12-04
Yesterday I installed a GTX 1050 graphics card in my server for CUDA purposes, so it is not connected to any displays. Whatever I did (install the driver from Nvidia, install with and without DKMS, install the driver from ppa:graphics-drivers/ppa, disable nouveau) I always got stuck in the login loop. As I have it working now I noticed something that might have caused this. I have two displays connected to the built-in Intel HD Graphics adapter, and the rotation of the second display is configured counter-clockwise. As I could not get it working I installed 16.04.1 from scratch, installed the 375 Nvidia driver from ppa:graphics-drivers/ppa, rebooted and I could login, except that I could no longer configure the rotation of the second display. So it might be (but I can no longer check this as I reinstalled) that I should have first configured the rotation of the second display to normal before installing the Nvidia driver. Using nvidia-settings you can select the Intel GPU (I don't know why that is needed as there are no displays connected to the Nvidia graphics card) and then you can configure the rotation of the second display again.

Gijsbert

---

