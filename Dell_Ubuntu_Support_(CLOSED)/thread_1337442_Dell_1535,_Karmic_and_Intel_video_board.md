---
title: "Dell 1535, Karmic and Intel video board"
date: 2009-11-25
forum: Dell Ubuntu Support (CLOSED)
---

### Post by lazar689 on 2009-11-25
I need some way to add the switch "nomodeset" to properly boot my system. At this moment I stop the boot with Esc and add the switch manually. 

 ubuntu karmic koala doesnot have /etc/X11/xorg.conf nor grub.conf and I don't know how to proceed. Will learn linux, but after pushing myself to the limit I have nice Karmic running smooth bilingual. Wifi, Bluetooth, music, video all up and running. The boot phase is a punishment.
Help

---

### Post by mikewhatever on 2009-11-25
Check out Grub2 howto.
[https://help.ubuntu.com/community/Grub2#Configuring%20GRUB%202](https://help.ubuntu.com/community/Grub2#Configuring%20GRUB%202)

The file in question is /etc/default/grub, and the parameter is GRUB_CMDLINE_LINUX_DEFAULT.

---

### Post by lazar689 on 2009-11-26
Yes, I did it! 
Added "nomodeset" in grub file and running update-grub. WoW - clean entry to Ubuntu
Thanks

---

### Post by jezzicaz789 on 2009-11-27
> **mikewhatever said:**
> Check out Grub2 howto.
[https://help.ubuntu.com/community/Grub2#Configuring%20GRUB%202]("https://help.ubuntu.com/community/Grub2#Configuring%20GRUB%202")

The file in question is /etc/default/grub, and the parameter is GRUB_CMDLINE_LINUX_DEFAULT.

Such a very amazing link!
Thanks you

---

### Post by orchiles on 2010-03-04
> **mikewhatever said:**
> Check out Grub2 howto.
[https://help.ubuntu.com/community/Grub2#Configuring%20GRUB%202](https://help.ubuntu.com/community/Grub2#Configuring%20GRUB%202)

The file in question is /etc/default/grub, and the parameter is GRUB_CMDLINE_LINUX_DEFAULT.

Thanks great source!
______________________
[Watch Movies Online]("http://imdbvip.com") 
[Watch TV Shows Online]("http://mytvy.com")

---

