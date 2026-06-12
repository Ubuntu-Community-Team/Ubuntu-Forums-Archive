---
title: "NTFS partitions &amp; Router"
date: 2007-08-07
forum: Desktop Environments
---

### Post by nilfisk1 on 2007-08-07
Hello,

I just started working with Linux so these are some pretty simple questions I guess ;)

I have ubuntu installed next to my windows xp, now when I boot ubuntu I can still see my ntfs partitions from windows. I always thought linux doesn't see those. Is there any way I can make them invisible? I realy want 2 separated systems, not 2 os'es with the same files.

Also, I was under the impression linux would automaticly install the right drivers for my router and set it up. Well I don't have internet :). As expected I was unable to launch the cd that came with the router from linux, what should I do? It's a gigaset usb adapter 108 from siemens.

Last but not least, when grub starts it gives me the options to boot linux , linux recovery, ram check and windows. What i want realy is that it only gives me the options linux and windows, and windows being the primary. Where can I find the grub config file to change this( if there is one )?


Thanks for reading this, and I hope you can help me out.

Nils

---

### Post by merlinus on 2007-08-07
Ubuntu will not confuse your windows drive with its own filesystem.  If you do not want it mounted at startup, you can remove the line referring to it in /etc/fstab.

Check you network setting in System/Administration/Network.

Grub settings are in /boot/grub/menu.lst.  You can comment out the stanzas you do not wish to see, and then change default 0 (near the top of the file) to default 1 to boot windows first.  You can also set the timeout to 5.

-merlin

---

### Post by nilfisk1 on 2007-08-07
As I go to boot>grub>menu.lst, I edit the settings, but can't click save. It sais it's because it's read only. I go to it's properties, and it sais I can't change them because I'm not the owner, whitch appears to be Root. 

How do I solve this? Can I actualy login as Root? I only have 1 user account, the one I submitted when installing. The one I login with.

Any feedback on this?

---

### Post by merlinus on 2007-08-07
```

gksudo gedit /boot/grub/menu.lst

```-merlin

---

### Post by nilfisk1 on 2007-08-07
Thanks again for your help Merlin, I realy realy appreciate this ( I know newb questions like this probably pop up like mushrooms on these forums but I hope you understand ). I read somewhere else  that I might fix it by going to actions>edit as root. I'll try both ways since I realy want to learn about this stuff.

Could you maybe help me analyse that line you just put?

I'm assuming gedit is the editor and the path speaks for itself. Does the gksudo part mean it runs it as admin/root? if so, would you happen to know what those letters stand for?

---

### Post by merlinus on 2007-08-07
sudo is used in front of a terminal command to get root access.  sudo means "do as superuser," more or less.

e.g. sudo fdisk -l will list your various partitions.

gksudo does the same thing for graphical apps such as gedit and nautilus.

-merlin

---

