---
title: "USB mount problems"
date: 2008-10-31
forum: Desktop Environments
---

### Post by brint on 2008-10-31
Hi all. I installed Ubuntu eee edition 8.04 on my asus eee last week, and I am having problems using my usb pen drives. 
When I plug one of them in a USB port, I get a warning saying that I have to be superuser to mount drive. 
This happens even if I try to do a sudo -su command in the terminal. What am I doing wrong? Please not that I only have used Ubuntu for about a week.

regards brint

---

### Post by Mark_in_Hollywood on 2008-10-31
I had the same problem and found it easier to reformat the drives in XP or even 98SE. 

Once they were reformatted and plugged into the usb ports, ubuntu found them and they worked like a charm.

If you MUST have them in linux-os, load a LiveCD or GParted LiveCD, set disklabel to msdos, format the drives to ext 2 or 3 and you should be good to go without all the permissions, sudo and such.

---

### Post by brint on 2008-10-31
Hi, thanks for the quick reply. I did a reformat in Vista, and I still get the warning "mount: must be superuser to use mount"
What to do?

---

### Post by Huitogi59 on 2008-10-31
&#12288;&#12288;A Jewish guy rings his mother. She picks up the phone and says 'Hello'. &#12288;&#12288;He says 'Hi, how are you?' &#12288;&#12288;'Fine', she says. &#12288;&#12288;'Sorry', he says, 'I must have the wrong number'. cheap wow power leveling (World of warcraft Power Leveling):**buy [WoW Power Leveling](http://www.igsstar.com),  cheap [world of warcraft power leveling](http://www.igsstar.com/wow-powerleveling-us/) , 1-80 level [wow Power Leveling](http://www.wowgoldweb.com),[maple story mesos](http://www.buymsmesos.com),       [wedding invitations](http://www.vponsale.com/invitations/)**

---

### Post by brint on 2008-11-01
bump

---

### Post by Mark_in_Hollywood on 2008-11-01
Try making them (or it) work under Ubuntu LiveCD or d/l a GParted LiveCD.
Put the CD in the drive and boot to it. In Ubuntu open System/Admin/Partition Editor. Once GParted loads, on the top right, open the devices "button". Find your device. Right click in the device, select format and go from there.

---

