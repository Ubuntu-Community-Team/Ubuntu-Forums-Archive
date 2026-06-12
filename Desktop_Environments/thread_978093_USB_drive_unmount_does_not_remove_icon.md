---
title: "USB drive unmount does not remove icon"
date: 2008-11-10
forum: Desktop Environments
---

### Post by GourdCaptain on 2008-11-10
When I use USB storage device such as a 30GB black iPod video, 2 GB PNY
memory stick, or Sony PSP-1000 are connected, they mount well.
However, upon right-clicking on the disk and hitting "Eject device", it
does not remove the icon from the XFCE desktop or Thunar. Instead, it
remains, now either able to be unmounted (which removes the icon, but
not in Thunar if removed from the desktop or vice-versa) or remounted.
If the USB device is removed prior to removing the device, the icon
cannot be removed unless the USB device is reinserted, instead saying
that /dev/sdf/ cannot be found.

On further insertions of the same USB device (before a reboot), two
mount icons are spawned on the desktop and in Thunar, one of which is
mounted, the other not. The mounted one works like the above account of
the first one, and after it is removed from the desktop the other one
can be unmounted.

Any ideas?

---

### Post by kernelhaxor on 2008-11-10
I saw another thread regarding the same problem ... Looks like a bug to me .. you might wanna file a bug in Launchpad

---

### Post by randcoop on 2008-11-11
It is indeed a known problem.  You might want to consider adding the mount/unmount item to your panel.  That works correctly.  

My understanding is that the problem with the Eject function is that it is trying to do more than simply unmount the device.  I'm using Xubuntu 8.04, so I don't know if the problem was fixed in 8.10.  But, as I said, the mount/unmount item that's available to be added to the panel does work correctly.

---

### Post by GourdCaptain on 2008-11-11
Deleting the thunar-volman config file seems to have alleviated the problem somewhat - now there's no extra icon (after the file was automatically recreated.) However, it still keeps an icon on the desktop and in thunar until I take extra actions after unmounting, and they still exist independent of each other.

I posted a launchpad bug at [https://bugs.launchpad.net/bugs/296269](https://bugs.launchpad.net/bugs/296269) . Anyone with similar symptoms, could you please confirm it or something?

BTW, I am using Xubuntu 8.10 Intrepid Ibex.

---

