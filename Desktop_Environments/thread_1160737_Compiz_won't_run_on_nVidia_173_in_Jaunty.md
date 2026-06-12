---
title: "Compiz won't run on nVidia 173 in Jaunty"
date: 2009-05-15
forum: Desktop Environments
---

### Post by eath on 2009-05-15
system.chassis.type Mini Tower system.chassis.manufacturer Hewlett-Packard system.board.product P4G-LA system.board.version REV 1.xx system.board.vendor ASUSTeK Computer INC. system.board.serial MB-1234567890 [B] 

NV34 [GeForce FX 5200] [/B]

PropertyValueinfo.subsystem pci info.product NV34 [GeForce FX 5200] info.vendor nVidia Corporation info.parent /org/freedesktop/Hal/devices/pci_8086_244e info.linux.driver nvidia info.udi /org/freedesktop/Hal/devices/pci_10de_322 pci.product NV34 [GeForce FX 5200] pci.vendor_id 4318 pci.vendor nVidia Corporation pci.product_id 802 pci.device_protocol 0 pci.device_subclass 0 pci.subsys_vendor_id 0 pci.device_class 3 pci.subsys_product_id 0 pci.linux.sysfs_path /sys/devices/pci0000:00/0000:00:1e.0/0000:01:0b.0 linux.hotplug_type 2 linux.subsystem pci linux.sysfs_path /sys/devices/pci0000:00/0000:00:1e.0/0000:01:0b.0 

This is my hardware.  I just upgraded to Jaunty off the full install (was using Hardy)  Compiz loaded right up in Hardy but in Jaunty it keeps say it cannot enable visual effects.  I am using nvidia driver 173 (recommended).  The other option was 96.  It add/remove offers 71 but when I install it, I don't know how to activate it.  173 and 96 don't work with compiz even though it says they are what I need for visual effects.  Is compiz broken in Jaunty?  I see a lot of complaints on the web and all the fixes lock up my terminal when I type "compiz".  It says something about being blacklisted.  I went to the compiz web site and it had black listed two ATI and one Intel video card but not a nVidia card.  Where do I go from here?

---

### Post by andrea000 on 2009-05-16
Do you have a internal video card that is turned on or 
blacklisted if so try turning that card off there are
fixes if it is blacklisted and interfering with compiz
?Try running compiz check from [here]("http://ubuntuforums.org/showthread.php?t=799070")
My internal card was blacklisted and turned off but my
nvidia wasn't the internal stopped compiz from working
on mine.
Sorry i can't be anymore help but i do not run 9.02

---

### Post by eath on 2009-07-05
Hello.  I am back.  I deleted compiz so I could get some work done and now am ready to tackle the problem again.  I tried to run the compiz check that Andrea suggested but it's response is ...
```
 More than one graphics chip detected -- sorry, the script can not handle that.
 Aborting.

```I have an onboard chip.  BIOS is ignoring it, why won't Jaunty.  Help me kill the horrible Intel video chip so I can use my nVidia 5200 in peace.

---

### Post by Mia1990 on 2009-07-05
what type of intel card is it?I have a integrated card and mine stoped compiz the driver was blacklisted i had to unblacklist it before compiz would work.Have you turned the integrated card off in the bios if not you need to.hp does not have a on/off for there's you just turn them down but compiz still picks them up.

---

### Post by eath on 2009-07-06
Ok, the blacklist skip did work.  The problem was figuring out how to turn of compositing in Metacity.  Now it is working.
```

gconftool-2 -s -t bool /apps/metacity/general/compositing_manager false
```

P.S. I don't know how to mark the thread solved.  I edited the first post.  Is that all I do?

---

