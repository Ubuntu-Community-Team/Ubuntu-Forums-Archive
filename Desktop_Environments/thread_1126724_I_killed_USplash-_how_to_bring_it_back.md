---
title: "I killed USplash- how to bring it back?"
date: 2009-04-15
forum: Desktop Environments
---

### Post by Sarai the Geek on 2009-04-15
A while back I decided to try Splashy for my bootsplash program instead of the default USplash. I could never get it to work and thus uninstalled it, but I can't seem to get USplash back. Right now I just get that really verbose bootloader screen with no graphics.
According to Synaptic, I have the following usplash-related packages installed:

"usplash" , "usplash-theme-freedom1024" , "usplash-theme-ubuntu" , "libusplash0" , "startupmanager"

I followed the instructions on [this thread]("http://ubuntuforums.org/showthread.php?t=886542") but it only made the bootloader screen appear when I was shutting down, not turning on.
What am I missing here?

(Also... 100th post! W00t!)

---

### Post by stderr on 2009-04-15
You could try installing startupmanager

```
sudo apt-get install startupmanager
```

Run via System -> Administration -> StartUp-Manager

It allows you to configure your bootup displays. You can, for example, ensure "Show text during boot" is unticked and "Show boot splash" is ticked (i.e. use your Usplash theme), and check a Usplash theme is selected under the Appearance tab.

---

### Post by Sarai the Geek on 2009-04-15
> **stderr said:**
> You could try installing startupmanager

```
sudo apt-get install startupmanager
```Run via System -> Administration -> StartUp-Manager

It allows you to configure your bootup displays. You can, for example, ensure "Show text during boot" is unticked and "Show boot splash" is ticked (i.e. use your Usplash theme), and check a Usplash theme is selected under the Appearance tab.

It's already installed. "startupmanager" was in my list of packages currently on my system. :)

---

### Post by stderr on 2009-04-15
So you had :)

I'm very surprised that setting those settings in startupmanager makes no difference.
Maybe it would be an idea to check your menu.lst file

```
gksudo gedit /boot/grub/menu.lst
```

The kernel line for the kernel you boot to should have "quiet" and "splash" on the end, and I think that's just what startupmanager does, so if yours does have those entries, then I'm out of ideas I'm afraid, aside from purging and re-installing usplash and running through the startupmanager settings once more.

My current boot line:
```
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=1227aa30-9bf3-40d0-bc37-3ff22b4c1a7d ro quiet splash 
```

---

### Post by Sarai the Geek on 2009-04-15
This is what mine says:

```
title        Ubuntu 8.10, kernel 2.6.27-11-generic
uuid        b93303ba-72c2-4efd-b5f0-481cd5c92dd1
kernel        /boot/vmlinuz-2.6.27-11-generic root=UUID=b93303ba-72c2-4efd-b5f0-481cd5c92dd1 ro quiet splash 
initrd        /boot/initrd.img-2.6.27-11-generic
quiet

title        Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid        b93303ba-72c2-4efd-b5f0-481cd5c92dd1
kernel        /boot/vmlinuz-2.6.27-11-generic root=UUID=b93303ba-72c2-4efd-b5f0-481cd5c92dd1 ro  single
initrd        /boot/initrd.img-2.6.27-11-generic

title        Ubuntu 8.10, kernel 2.6.27-7-generic
uuid        b93303ba-72c2-4efd-b5f0-481cd5c92dd1
kernel        /boot/vmlinuz-2.6.27-7-generic root=UUID=b93303ba-72c2-4efd-b5f0-481cd5c92dd1 ro quiet splash 
initrd        /boot/initrd.img-2.6.27-7-generic
quiet

title        Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid        b93303ba-72c2-4efd-b5f0-481cd5c92dd1
kernel        /boot/vmlinuz-2.6.27-7-generic root=UUID=b93303ba-72c2-4efd-b5f0-481cd5c92dd1 ro  single
initrd        /boot/initrd.img-2.6.27-7-generic

title        Ubuntu 8.10, memtest86+
uuid        b93303ba-72c2-4efd-b5f0-481cd5c92dd1
kernel        /boot/memtest86+.bin
quiet

```

Looks like quiet and splash are both there. I'll try uninstalling usplash and startupmanager then reinstalling.

---

