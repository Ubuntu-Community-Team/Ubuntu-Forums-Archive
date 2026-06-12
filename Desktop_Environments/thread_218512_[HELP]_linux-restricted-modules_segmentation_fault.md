---
title: "[HELP] linux-restricted-modules segmentation fault"
date: 2006-07-18
forum: Desktop Environments
---

### Post by racoq on 2006-07-18
I was upgrading dapper, and following error appeared.

Installing linux-restricted-modules-2.6.15-26-386 (2.6.15.11-3) ...
/sbin/lrm-manager: line 85:  7280 Segmentation fault      depmod -a -q -F /boot/System.map-"$KVER" "$KVER"


Is there a way i can fix it?

---

### Post by tseliot on 2006-07-18
Try with:
```
sudo apt-get install -f
```

---

### Post by racoq on 2006-07-18
the same thing happens :-|

---

### Post by tseliot on 2006-07-18
try:
```
sudo depmod -A
```

Other than that I wouldn't know what to suggest but I hope someone else does

---

### Post by racoq on 2006-07-18
tried that, and then sudo apt-get install -f and the same thing happen.

i think the problem is here :

my /boot directory

```

rui@ubuntu:/boot$ ls 
abi-2.6.15-23-386     grub                      System.map-2.6.15-23-386
abi-2.6.15-26-386     initrd.img-2.6.15-23-386  System.map-2.6.15-26-386
config-2.6.15-23-386  initrd.img-2.6.15-26-386  vmlinuz-2.6.15-23-386
config-2.6.15-26-386  memtest86+.bin            vmlinuz-2.6.15-26-386

```

i've also tried:
```

rui@ubuntu:/boot$ sudo depmod -v 2.6.15-26-386
Segmentation fault

```

probably this is the error, dows anyone know how i can fix it?

 any suggestions?

---

### Post by racoq on 2006-07-18
I've found a workaround (not a solution)

To acomplish the sudo apt-get insatll -f, ive did the folowing:

```

sudo cp /boot/* /home/rui/boot_backup
cd boot
sudo rm -rf *2.6.15-26*
sudo apt-get install -f

```

Then i've had to edit the grub entry so that the ubuntu don't starts, the next time i reboot the machine, from 2.6.15-26 kernel, so i've did: 

```

 sudo nano /boot/grub/menu.lst

```

and commented the folowing lines:


```


# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## ## End Default Options ##

#title          Ubuntu, kernel 2.6.15-26-386
#root           (hd0,0)
#kernel         /boot/vmlinuz-2.6.15-26-386 root=/dev/hda1 ro quiet splash
#initrd         /boot/initrd.img-2.6.15-26-386
#savedefault
#boot

#title          Ubuntu, kernel 2.6.15-26-386 (recovery mode)
#root           (hd0,0)
#kernel         /boot/vmlinuz-2.6.15-26-386 root=/dev/hda1 ro single
#initrd         /boot/initrd.img-2.6.15-26-386


```

And voilá, no problems anymore

However a solution for this problem instead of this workaround would be apreciated, since i haven't managed to make work kernel, 2.6.15-26-386 , from the ubuntu upgrade.

---

