---
title: "dconf-tools question"
date: 2015-11-10
forum: Desktop Environments
---

### Post by chriso0258 on 2015-11-10
Hello,

I installed dconf-tools on my Ubuntu desktop 14.04 pc. I then went to org->gnome->desktop->media-handling. I unchecked both automount and automount-open yet when I put in a flash drive it still shows up in the file system. I don't want any media mounted when inserted into a usb port. What am I doing wrong? Does dconf-tools not work with desktop 14.04?

Thanks for your help.
Chris

---

### Post by deadflowr on 2015-11-10
Sure it'll show in the File manager (I assume you mean it shows in the file manager panel), 
but is it actually mounted?

---

### Post by xsnake_ on 2015-11-10
You can tell if the device is actually mounted by looking into /media/<username>/ and looking if a UUID folder was created for the flash drive. Or even simpler, is the small "Eject" button showing up on the device in Nautilus?

With the settings you mentioned above, the device should not be mounted, but these settings will not prevent it from showing up in Nautilus. To do so you might have to blacklist the usb device-id (get it with lsusb).

---

### Post by chriso0258 on 2015-11-10
Thanks for both your replies. When first looked at in Nautilus, there is no "Eject" button. However, if I click on the device, then the eject button appears. I guess it is doing what dconf-tools configured by not "auto mounting". However, I don't want any media to mount when placed in the usb port. I'll take carl42 advice and black list it.

Thanks again.

---

### Post by ajgreeny on 2015-11-10
> **chriso0258 said:**
> However, I don't want any media to mount when placed in the usb port. I'll take carl42 advice and black list it.

Thanks again.
But it is not mounting!
It is simply showing in nautilus as one of the "Places" available to mount; when you click the icon the system mounts it.

If blacklisted, assuming that works as carl42 suggests, it will be much more difficult to get it mounted when you want it, as there will be no icon for it anywhere in nautilus for you to click.

---

### Post by Dennis N on 2015-11-10
> But it is not mounting!
It is simply showing in nautilus as one of the "Places" available to mount; when you click the icon the system mounts it.

Yes, exactly. I see it work like so: When inserted, it is connected to the universal serial bus, and shows in the file manager side pane. Then, when mounted, the mounted symbol appears next to it. When you unmount it, that symbol disappears. When ejected (or "safely removed"), it is disconnected from the universal serial bus and the icon goes away. You can pull it out safely.

---

