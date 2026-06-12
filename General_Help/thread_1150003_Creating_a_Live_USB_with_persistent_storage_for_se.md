---
title: "Creating a Live USB with persistent storage for settings and documents"
date: 2009-05-05
forum: General Help
---

### Post by LambdaCalculus379 on 2009-05-05
Hi all, I'm having an issue creating a Live USB stick with persistent storage.

The basis is an Ubuntu 9.04 system. Installed are Skype, CrossOver, Adobe AIR, MS Office 2003 (via CrossOver), Google Desktop, and most of the default apps. All of this appears in the Live USB, no problem. The problem is when I want to customise the settings from within the Live USB itself.

I had customised the menus, added icons to the desktop, changed the wallpaper, and added some extensions in Firefox. When I shut down and restart the live USB, it returns to default settings again. Needless to say, this isn't what I want.

Now, I need settings to be saved and restored each time the session is shut down and restarted. These Live USBs are to be used in a small office environment by interns, and it would be extremely annoying to have to reset each and every single time. What bothers me is that another live USB I made based on 8.10 does save its settings, so why doesn't this one?

For the record, I used remastersys to create the Live CD from which I built the USBs, and the default USB Startup Disk Creator util in Ubuntu 9.04 to make the live USB sticks; this was also done for 8.10.

Can someone give me any ideas on how to keep a persistent storage system for these new Live USBs? We're due to hand them out soon.

---

### Post by dcstar on 2009-05-05
> **LambdaCalculus379 said:**
> Hi all, I'm having an issue creating a Live USB stick with persistent storage.

The basis is an Ubuntu 9.04 system. Installed are Skype, CrossOver, Adobe AIR, MS Office 2003 (via CrossOver), Google Desktop, and most of the default apps. All of this appears in the Live USB, no problem. The problem is when I want to customise the settings from within the Live USB itself.

I had customised the menus, added icons to the desktop, changed the wallpaper, and added some extensions in Firefox. When I shut down and restart the live USB, it returns to default settings again. Needless to say, this isn't what I want.

Now, I need settings to be saved and restored each time the session is shut down and restarted. These Live USBs are to be used in a small office environment by interns, and it would be extremely annoying to have to reset each and every single time. What bothers me is that another live USB I made based on 8.10 does save its settings, so why doesn't this one?

For the record, I used remastersys to create the Live CD from which I built the USBs, and the default USB Startup Disk Creator util in Ubuntu 9.04 to make the live USB sticks; this was also done for 8.10.

Can someone give me any ideas on how to keep a persistent storage system for these new Live USBs? We're due to hand them out soon.

Create a new EXT2 partition on the USB labelled "casper-rw", and check that the "persistent" option is on the boot command line.

---

### Post by aaronej on 2009-05-07
There isn't an easier way?  Everything was going great and the only thing I was worried about was that when I keep looking at the system monitor,  the remaining free disk space did not change as I downloaded new software.  Then when I restarted, I was back to square one.  I wish I had tested that earlier.

---

