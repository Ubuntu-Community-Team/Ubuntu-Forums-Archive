---
title: "Xubuntu: How to import photos from camera?"
date: 2007-04-22
forum: Desktop Environments
---

### Post by Jonathan Métillon on 2007-04-22
Hi,

I'm used to Ubuntu Edgy and auto importation of photos from camera with GThumb.

With Feisty I switched to Xubuntu. I connected my camera and nothing happened. Then I opened GQview and I did see any import from camera option.

How am I supposed to import photos from my camera with Xubuntu Feisty? Thanks!

---

### Post by mojoman on 2007-04-23
I played around a bit with this yesterday, also on Xubuntu Feist. I installed gtkam, it's fairly small and didn't have any heavy dependencies. I then found my camera with the menu under Camera --> Add Camera. Once the camera was added it shows up in the left field and by clicking it I could save the pictures on the HD. It took some tries for the program to find the camera and then to find the pictures on the camera but nothing serious, I not used to the program yet.

/mojoman

---

### Post by Jonathan Métillon on 2007-04-23
Hi Mojoman! Thank you for your quick answer.

I installed gtkam. It had 3 dependencies: *libexif-gtk5*, *libgphoto2-2* and *libgphoto2-port0*.

I run gtkam and scan for my camera but it does not appear. I rescaned a few times but it does not show up. 

I have this output from *dmesg* after connecting the camera with USB cable:

```
[ 4196.052000] usb 5-3.4: new full speed USB device using ehci_hcd and address 9
[ 4196.236000] usb 5-3.4: configuration #1 chosen from 1 choice
```It is a [Kodak C330]("http://www.kodak.com/eknec/PageQuerier.jhtml?pq-path=7087&pq-locale=en_US").

---

### Post by Jonathan Métillon on 2007-04-23
Well, I've been able to manually add the camera using the "Add camera..." option.

This software is not very ergonomic. I had to browse through the camera's folders, then highlight the pictures folder and use File > Save Photo All.

Then I chose a folder to export to, on my hard drive. And it said that their's nothing to save. I had to select "Save photos" and "Save EXIF data". This is not obvious. Good default could have been set here.

Anyway, I got my photos exported. Thanks Mojoman!

Note: I just discovered that the photos in the camera can be seen before exporting. I selected "View thumbnails" but it showed nothing. Actually, I had to stretch the window enough and drag the window separator so I can see the preview panel. By default the app window is very small and the preview panel is hidden!

Also, I have to delete the photos after exporting. I did not see any options to remove the photos as they are exported.

---

