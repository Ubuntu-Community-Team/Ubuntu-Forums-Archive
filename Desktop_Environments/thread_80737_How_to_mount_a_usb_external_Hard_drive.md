---
title: "How to mount a usb external Hard drive?"
date: 2005-10-22
forum: Desktop Environments
---

### Post by Fern_azul10 on 2005-10-22
Hello I just bought from a friend a usb hard drive I use it mainly at my college to show anime and movies and stuff like that on a windows machine but I have to add new stuff on it and now im using Linux Ubuntu and I don't have a clue how to mount it?? All I thought i had to do was just connect the usb hub and I will be able to use it but it seems it doesn't work that way can anyone tell me how I can use it?? Also will I have to keep doing this process over and over since I am always connecting it and disconnecting it??

---

### Post by aysiu on 2005-10-22
If everything's working right, you should be able to just plug it in. An icon will appear on your desktop for it (mounted), and you can do whatever you want with the files inside. Once you're done, you right-click it and select "unmount volume," and it'll be safe to unplug.

That's if everything's working right. Obviously not everything's working right. That's odd.

I suppose you can always manually mount it. To do that, you'll have to figure out where it's located (it may be /dev/sda1 or /dev/sde1... type in ```
sudo fdisk -l
``` to find out--the command will also tell you what filesystem type it is). Let's assume it's /dev/sda1 and FAT32. Then you just ```
sudo mkdir /mnt/usbdrive
sudo mount -t vfat /dev/sda1 /mnt/usbdrive
```

---

