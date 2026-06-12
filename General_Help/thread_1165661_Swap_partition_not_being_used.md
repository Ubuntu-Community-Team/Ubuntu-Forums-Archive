---
title: "Swap partition not being used"
date: 2009-05-20
forum: General Help
---

### Post by Blue_Mercury on 2009-05-20
I recently installed Xubuntu 9.04 on an older AMD 2.4gHz with only 256mb of RAM

The system runs fine but when you open the System Monitor it says there is zero swap memory, and as a consequence if you fill the RAM the computer crashes and needs to be manually rebooted. (which is fairly easy to do)

There is a 500mb linux-swap partition on the harddrive according to Gparted.
Why isn't Xubuntu using it, and how do I make it utilize the swap?

---

### Post by geirha on 2009-05-20
Have the swap partition been resized after you installed? That'll change the UUID of the swap. 

Anyway, to make sure it's using the right UUID, first find the correct UUID for the swap partition with this command ```
sudo blkid -t TYPE=swap
```

Then edit /etc/fstab (sudoedit /etc/fstab), and set the correct UUID on the entry for the swap partition. Here's my swap entry in /etc/fstab.

```
UUID=51945e4b-5b02-4124-afb9-97724bdf6b5a none swap sw 0 0
```

Once you've done that change, and saved the file, enable the swap with ```
sudo swapon -a
```
And confirm that it is in use with ```
swapon -s
```
If that worked out, it should automatically use that swap partition next time you boot.

---

### Post by Blue_Mercury on 2009-05-21
Thank you, the swap partition had been moved after the installation.
All I needed to do was change the UUID, the swapon command was not necessary as swap was already on (just reading zero)

---

