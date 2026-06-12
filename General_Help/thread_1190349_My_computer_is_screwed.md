---
title: "My computer is screwed"
date: 2009-06-17
forum: General Help
---

### Post by John M2009 on 2009-06-17
OK i installed Ubuntu this evening,  only to find that it didnt give me the option to boot up into widows,  which I still wanted to use.  I tried to work out how to uninstall Ubuntu, until I could figure something out (I still want to be able to use windows)  but after reading loads of threads about uninstalling,  which were just too confusing,  I decided I would just delete the partition.  Seems as though that was not the thing to do....now when I reboot i get 

Grub Loading...

Error 22

All I have to run on my PC now is the Live CD

Please help!!!

---

### Post by merlinus on 2009-06-17
You will need your xp or other windows install disk.  Select Recovery (or Restore) and then fixmbr (or fixboot).

Supergrub will do the same job.

---

### Post by redilyn on 2009-06-17
If you install ubuntu again (or if you still have it installed) and find that you still do not have an option to boot windows try the following.

Start ubuntu

Open a terminal (Applications -> Accessories -> Terminal) and type the following command
```

sudo gedit /boot/grub/menu.lst

```

Look for the following section - Yours will not be the same as the example below but you should see something similar
```

title		Ubuntu 9.04
uuid		4b48ee11-11fa-492a-92cc-67750eef3079
kernel		/boot/vmlinuz-2.6.28-12-netbook-eeepc root=UUID=4b48ee11-11fa-492a-92cc-67750eef3079 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-12-netbook-eeepc
quiet

```

Add the following to the file.
```

title		Microsoft Windows
rootnoverify	(hd0,0)
savedefault
chainloader	+1

```

You should now have this

```


title		Ubuntu 9.04
uuid		4b48ee11-11fa-492a-92cc-67750eef3079
kernel		/boot/vmlinuz-2.6.28-12-netbook-eeepc root=UUID=4b48ee11-11fa-492a-92cc-67750eef3079 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-12-netbook-eeepc
quiet

title		Microsoft Windows
rootnoverify	(hd0,0)
savedefault
chainloader	+1

```

Save the file and reboot.

---

