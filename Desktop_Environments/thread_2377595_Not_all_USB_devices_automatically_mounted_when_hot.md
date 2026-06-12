---
title: "Not all USB devices automatically mounted when hot-plugged Ubuntu 17.10"
date: 2017-11-15
forum: Desktop Environments
---

### Post by alwin-bakker on 2017-11-15
I'm running Ubuntu 17.10 and my iPhone and Kobo tablet (neither PTP nor MTP) won't be automatically mounted and shown in Nautilus when I plug them in. I can only mount and open these manually. All other devices, including usb sticks, a GoPro and a external hard drive do mount and open with Nautilus automatically when hot-plugged.

In Setting -> Devices -> Removable Media all settings are set. And also when I go to /org/gnome/desktop/media-handling with Dconf-editor all settings should be fine.

The story is, I updated from Ubuntu 16.04 to 17.10 and connected my iPhone to transfer some pictures, that's all I usually did. It still did work, but it didn't show all the pictures any more (this turned out to be an iPhone setting). But before I realised that, I started messing around with the libimobiledevice. Ended up deleting it, to attempt to reinstall, but automatically got a lot more deleted and couldn't get in the Ubuntu desktop environment anymore. Ended up reinstalling ubuntu-desktop, first nothing worked with both iPhone/ Kobo, but now it only works manually.

- iPhone 4s with iOS 9.3.5
- Kobo tablet with Android 4.2.2
- Laptop is an Acer Aspire V3-571

---

