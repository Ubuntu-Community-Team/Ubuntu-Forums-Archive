---
title: "canon SD500 digital camera problems"
date: 2005-10-19
forum: Desktop Environments
---

### Post by Heretic09 on 2005-10-19
After apt-getting the latest packages I can finally plug in my usb thumb drive and have it mount properly. Everythings fine on that end I can copy to and from that particular device.

The problem is with my canon sd500 camera. When I plug it in, the camera shows up fine on the desktop and opens up to show a folder where the pics are kept. When I try to access that folder I get an error "unable to write to./" Any on have any idea what that means?

digikam cannot connect to it at all.

---

### Post by seattlegaucho on 2005-10-19
[QUOTE=Heretic09]The problem is with my canon sd500 camera. When I plug it in, the camera shows up fine on the desktop and opens up to show a folder where the pics are kept. When I try to access that folder I get an error "unable to write to./" Any on have any idea what that means?[/QUOTE]

There may be 2 reasons:

1. Most obvious one: If you are using SD or xD cards, they have a slide switch to **write protect** them. You can visually check the card ;) . Otherwise, once you cp'd your files, try to delete a couple of pictures using the camera menus. If you can, then the 2nd option may be happening ...

2. Some cameras appear to the OS as read-only media.

My $.02
G

---

### Post by Heretic09 on 2005-10-20
The card switch is not in the "lock" position so that can't be it. The camera does work under windows to view photos off it. 

The weird thing is it actually mounts it and you can see the folder under the camera that stores the pics its when you access the pics  you get the error "Unable to read ./". Doesn't matter if its root or a normal user.

I finally broke down and plugged in a card reader. Ubuntu mounted and opened up the pics just fine.

---

### Post by fassan on 2005-10-23
I have an SD300 and it works fine- opens okay in digikam.  I added it to digikam using the camera-add_camera menu in digikam.  It connects in PHP mode.  I am sad to hear your SD 500 not working - the digital cmera was one of the few things that I didn't have to tweak to work in linux.  They should be installed already, but double check for libgphoto with adept or apt-get.  Good Luck.

---

### Post by Heretic09 on 2005-10-24
yeah I already have libgphoto. I tried it with a couple of live cds, none of them were able to get pics from the camera itself.

---

### Post by outdooricon on 2005-12-02
[QUOTE=Heretic09]yeah I already have libgphoto. I tried it with a couple of live cds, none of them were able to get pics from the camera itself.[/QUOTE]

Just so you know, I'm sitting in the same boat as you. My sd500 doesn't work through usb connection anymore since I started using Breezy (It worked great in Hoary). It's pretty frustrating, I can only hope dapper will fix the problem that everyone seems to be having with USB stuff.

---

