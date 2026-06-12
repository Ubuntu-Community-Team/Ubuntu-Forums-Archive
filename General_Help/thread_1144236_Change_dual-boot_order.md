---
title: "Change dual-boot order?"
date: 2009-04-30
forum: General Help
---

### Post by Ressurect on 2009-04-30
Hi, is there any way to change the order of the dual-boot? I have just installed Ubuntu 9.0.4 on my pc and have it dual-booting with my Windows XP Professional. However, in the windows BOOT.INI file it only shows 1 OS so I can't see a way to change it like that, is there a way I can change XP to boot as default from Ubuntu?

---

### Post by kanikilu on 2009-04-30
Checkout the **startup manager** package in Ubuntu. You can install it with: ```
sudo apt-get install startupmanager
``` Or find it in Synaptic.

Here's a little demo on Youtube I found that includes showing how to change the default OS.

[http://www.youtube.com/watch?v=Qpt31YU55is](http://www.youtube.com/watch?v=Qpt31YU55is)

Of course, you can always manually edit the /boot/grub/menu.lst file. That's a little more advanced, but useful to know how to do.

[https://help.ubuntu.com/community/GrubHowto#Change%20the%20default%20operating%20system](https://help.ubuntu.com/community/GrubHowto#Change%20the%20default%20operating%20system)

---

### Post by Ressurect on 2009-04-30
Thanks for the quick reply, I think i'll have to go for editing the boot menu as I only installed Ubuntu with 2.5GB partition and now I pretty much can't do anything on it :( Which is annoying because this is the first distro thats actually recognised my wireless adapter :(

When i've got time i'm probably just going to delete the partition and then fix the mbr from the windows install disk then try again with a bigger ubuntu partition :)

---

