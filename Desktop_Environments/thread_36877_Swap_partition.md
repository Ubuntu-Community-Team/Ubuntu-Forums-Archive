---
title: "Swap partition"
date: 2005-05-25
forum: Desktop Environments
---

### Post by frs-design on 2005-05-25
Hello all !

I installed kubuntu without a swap partition and now, i'd like to add one.

FOr now, i have created a part with fdisk and set it to 82 hex code for the swap file system.

But after that ? how to format it, and how to activate it ?

Thank you to help me  :-| 

Bye

---

### Post by f.prisson on 2005-05-25
Try ```
sudo swapon -a
```

---

### Post by frs-design on 2005-05-25
Ok thank you, i didn't know this command.

I'll describe how i did to create a swap after installing kubuntu without one (maybe it'll be usefull for somebody :) )

- I used fdisk /dev/hda with sudo

- i created a partition with n
the hda3 will be the swap.

- i changed the type with t (hex value for swap = 82)

- i applied the changes with w and quit with q

- i edited the /etc/fstab file and added  this line:

/dev/hda3       none    swap    sw      0       0

- i entered: sudo mkswap /dev/hda3 

- i launched sudo swapon -a

And that's all !!

thx! bye !

---

### Post by gtdaqua on 2007-08-30
Thanks a lot!! 

I repartitioned my Ubuntu Feisty Fawn server with a 3rd party software (acronis). All went well, but the system acted up - it would just become slow after running VMWare server or simply after some time.

Figured it might be the swap and it was! Swap was not being recognized. It showed as 0k. So followed your post with some change - deleted the existing swap drive and the swap extened partition. Rebooted the machine. Created an extended partition and then a swap logical drive. And most importantly commented the UID line is /etc/fstab and forced it to use "/dev/sda5" and restarted. Voila! I am back up with full strength now!!

---

