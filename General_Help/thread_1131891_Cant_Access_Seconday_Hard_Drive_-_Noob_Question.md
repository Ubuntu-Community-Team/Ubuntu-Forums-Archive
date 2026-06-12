---
title: "Cant Access Seconday Hard Drive - Noob Question"
date: 2009-04-21
forum: General Help
---

### Post by CaseyC on 2009-04-21
I go to Place > Computer > then click 80gb SATA which i saved stuff on when i had xp on my machine but i get this error each time Unable To Mount 80gb SATA

something i need to setup or what not? thanks.


edit: this happens when i try and open any other internal hard drive i have or a usb flash drive.

---

### Post by blueturtl on 2009-04-21
There might be file system errors on that partition.
If a file system is somehow corrupt, Ubuntu will often not mount it.

What you want to do in a situation like this is check it for errors.

Open a terminal (Applications->Accessories->Terminal) and give the command:
```
sudo fdisk -l
```

This should give you a list of devices and partitions.

If your secondary drive is something like /dev/sdb1 you would then give a command like:

```
sudo fsck /dev/sdb1
```

This will check the system for errors and afterwards you may be able to mount it.

---

### Post by hyperdude111 on 2009-04-21
Are you running the live cd? you will need to be root to mount a drive on live cd.

---

### Post by CaseyC on 2009-04-21
thanks i will try that. i also have to give it to you... you helped me fix dual boot problem with windows / linux so ty very much :D 

the bios and linux saw my 4 sata hard drives in different orders in the menu.lst and the sudo fdisk helped me organize them. 

but back to the point lol... 

any of the other 3 hard drives or any flash drive i put on the system it does not want to open and gives me an error although they work on other computers. could they all have file system problems?

---

### Post by CaseyC on 2009-04-21
i didnt change anything but they are now working, when i click them they mount to my desktop (did i say that correct) :D 

anyways thank you all for the help on the topic... i solved several problems in this one thread :D

---

### Post by blueturtl on 2009-04-21
Glad that it worked out for you.

Remember to mark this thread as solved, so others experiencing the same issue are more likely to look at it instead of posting their own.

Have a pleasant Ubuntu experience!

---

