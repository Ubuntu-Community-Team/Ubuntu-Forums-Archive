---
title: "Vista/Ubuntu Dualboot on Dell XPS M1730?"
date: 2008-08-25
forum: Dell Ubuntu Support (CLOSED)
---

### Post by alexgamerz on 2008-08-25
So I got my new Dell XPS M1730 and i really want to try ubuntu, I have tried putting it on, and failed. I think i know the reason for that, but I have heard that the little "house" button near the power button launches a light weight windows xp for media purposes only. I heard that this can be disrupted and even stop your computer from booting at all. I need help from someone who has a xps like mine or knows what i am talking about

---

### Post by trashjunkid on 2008-08-25
alexgamerz-

I have an xps m1530 laptop. My harddrive crashed, and I got by using a fedora 9 liveusb, following the instructions here: [http://lifehacker.com/391067/fedora-9-puts-your-desktop-on-a-usb-drive]("http://lifehacker.com/391067/fedora-9-puts-your-desktop-on-a-usb-drive"). 

It installed without a hitch and with the persistent overlay it kept all the personalization settings. It was super easy and super fast and I loved it. I then began looking into using linux to revitalize some the old computers laying around the house and struck upon Ubuntu (and sometimes xubuntu) as the better distributions in those cases.

In anycase, because the boot to usb option plus the Fedora 9 LiveUsb works so well for me, I have left that configuration alone. Here are instructions to try out an Ubuntu LiveUsb: [https://wiki.ubuntu.com/LiveUsbPendrivePersistent]("https://wiki.ubuntu.com/LiveUsbPendrivePersistent").

The four partitions installed on the windows xps by default are a very small diagnostics partition, an OS reinstall partition, the dell mediadirect partition, and finally the windows partition itself.

In a laptop, having that diagnostics partition seems helpful, as is the os reinstall partition- the mediadirect partition is debatable however. I've had the laptop for half a year and haven't used it at all. I think nuking it would be perfectly fine and would open a primary partition. However, as I understand it, if you change your mind and want to get that partition back, it is difficult or perhaps impossible to get the mediadirect partition back and playing well on your dell.

Not quite the answer you were looking for (nuke the mediadirect partition, or use a liveusb), but that's my view for what it is worth,

Trashjunkid

---

### Post by TimDaniels on 2008-08-25
Forget the "little house" button.  It's a major pain in the butt, and it could wipe out your Vista partition.  At the very least, it will take you days or weeks to find out how to make it boot Linux, but even then, if you have to add/remove partitions, you'll have to diddle with reinstalling MediaDirect and resetting the settings for the "little house" button.  Search these archives for MediaDirect, and you'll see all the tales of woe.

As for dual-booting Vista with Ubuntu, with Ubuntu installed last, it's easy if you let Grub (the Linux boot manager) control which OS is loaded.  It's a little harder if you want to have Vista's boot manager direct the loading.  Let us know what you want to do.

*TimDaniels*

---

