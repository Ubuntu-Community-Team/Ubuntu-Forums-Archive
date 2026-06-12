---
title: "GDM fails to start, doesn't start with keyboard/mouse support"
date: 2009-10-30
forum: Desktop Environments
---

### Post by Wicaeed on 2009-10-30
I'm currently running Ubuntu Jaunty at work and recently my machine locked up and forced me to do a hard reset, now whenever I start it up, GDM acts as if it is going to start (loading bar) but right when it would go to the login screen, I am shown a prompt. If I hit Ctrl Alt F1 to take me to the first console there is a message there waiting that says:

Boot from (hd0,0) ext3 614e3968-315c-4839-b631-5605dbb383ed
Starting Up...
[     1.281496] ACPI: Expecting a [Reference] package element, found type 0
Loading, please wait...
usplash: Setting mode 1152x864 failed
19+0 records in
19+0 records out
kinit: name_to_dev_t(/dev/disk/by-uuid/dc4f0b71-95c1-45e7-9eea-e9b4142a114) = dev(8,21)
kinit: trying to resume from /dev/disk/by-uuid/dc4f0b71-95c1-45e7-9eea-e9b4142a114
kinit: No resume image, doing normal boot...
usplash: Using mode 1024x768

I've searched other threads and this error in itself means nothing, simply that ubuntu tried to load a hibernated file and couldn't find it.

I can go to any of the 6 other consoles, but ctrl alt f7 doesn't bring me to the GDM login screen, in fact GDM is not even running, and neither is X. I can start them manually, but then things get strange. GDM takes me to the regular login screen, but neither my keyboard or mouse will work at all, I cant even get back to the other consoles, I either have to restart or ssh in and manually kill gdm to be able to input any commands locally. I've taken a look at 'tail -f /var/log/Xorg.0.log' in an ssh session while I start GDM manually, and nothing is written to the file.

Any help/advice towards resolving this issue is greatly appreciated.

---

