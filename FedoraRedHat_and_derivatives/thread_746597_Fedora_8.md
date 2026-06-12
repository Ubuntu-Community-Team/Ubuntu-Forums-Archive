---
title: "Fedora 8"
date: 2008-04-05
forum: Fedora/RedHat and derivatives
---

### Post by gangsterhead3 on 2008-04-05
i have just installed Fedora 8 on my laptop

sda1 win vista
sda2 ubuntu
sda3 swap
sda4 fedora


when i installed it, i didnt install grub.
i want to add fedora to my ubuntu grub but i dont know what to write.

does anyone know the kernel, intrd for fedora 8?
and what do i write if fedora is on sda4?

---

### Post by jpeddicord on 2008-04-05
Moved to the Fedora forum; you'll get better help here with the problem here.

---

### Post by markharding557 on 2008-04-05
if i remember correctly fedora does not recognize other linux so you would need to install fedora first and ubuntu last so ubuntu writes the final grub

---

### Post by gangsterhead3 on 2008-04-05
is there a way to do it without reinstalling ubuntu????

cant i just add it to my ubuntu grub?

---

### Post by gangsterhead3 on 2008-04-06
bump

---

### Post by Antman on 2008-04-06
> **gangsterhead3 said:**
> is there a way to do it without reinstalling ubuntu????

cant i just add it to my ubuntu grub?

Post your grub contents. :-k

---

### Post by gangsterhead3 on 2008-04-06
> **Antman said:**
> Post your grub contents. :-k
default 0
timeout 10

title Ubuntu hardy (development branch), kernel 2.6.24-15-generic
root (hd0,1)
kernel /boot/vmlinuz-2.6.24-15-generic root=UUID=42daa819-0086-455c-ba4b-bdfe4ffe7c6c ro quiet splash
initrd /boot/initrd.img-2.6.24-15-generic
quiet

title Ubuntu hardy (development branch), kernel 2.6.24-15-generic (recovery mode)
root (hd0,1)
kernel /boot/vmlinuz-2.6.24-15-generic root=UUID=42daa819-0086-455c-ba4b-bdfe4ffe7c6c ro single
initrd /boot/initrd.img-2.6.24-15-generic

title Other operating systems:
root 

title Windows Vista/Longhorn (loader)
root (hd0,0)
chainloader +1
savedefault
makeactive

---

### Post by Antman on 2008-04-06
First, you may want to verify your kernel version with:
```
uname -r
```

and **replace the areas in red with your kernel name**.

Ok... try this code at the end of your grub.conf:

```
title Fedora ([COLOR="Red"]2.6.23.1-42.fc8[/COLOR])
	root (hd0,3)
	kernel /vmlinuz-[COLOR="Red"]2.6.23.1-42.fc8[/COLOR] ro root=/dev/VolGroup00/LogVol00 rhgb quiet
	initrd /initrd-[COLOR="Red"]2.6.23.1-42.fc8[/COLOR].img
```

Let me know if this works for you.

---

### Post by gangsterhead3 on 2008-04-06
uname -r tells me my ubuntu kernel so i dont think it is very useful for fedora


ill try what you just gave me and ill let you know if it works

---

### Post by Antman on 2008-04-06
> **gangsterhead3 said:**
> uname -r tells me my ubuntu kernel so i dont think it is very useful for fedora


ill try what you just gave me and ill let you know if it works

Oopss... sorry. I forgot that you can't boot into fedora to check the kernel... ](*,)

I tend to keep 4 kernels in my grub so I can revert back if needed. So I **think** the one I posted is the default kernel on the F8 install.

I hope this helps.

AntMan

---

### Post by gangsterhead3 on 2008-04-06
i doesnt work
it says 

ERROR 15 : file not found

---

### Post by gangsterhead3 on 2008-04-06
i doesnt work
it says

ERROR 15 : file not found

---

### Post by Antman on 2008-04-06
> **gangsterhead3 said:**
> i doesnt work
it says

ERROR 15 : file not found

I'm not sure, but grub may not be pointing to your LVM correctly.
I don't have a multi-OS system so my grub is pretty simple. :-k

---

### Post by gangsterhead3 on 2008-04-06
so does that mean you cant help me?

---

### Post by Antman on 2008-04-06
> **gangsterhead3 said:**
> 
sda1 win vista
sda2 ubuntu
sda3 swap
sda4 fedora

Are all of these on Primary partitions?

---

### Post by gangsterhead3 on 2008-04-06
> **Antman said:**
> Are all of these on Primary partitions?
ye

---

### Post by odiseo77 on 2008-04-06
Can you mount your fedora partition and list the contents of its /boot directory? Something like this:

```
sudo mkdir /mnt/fedora
sudo mount /dev/sda4 /mnt/fedora
ls -l /mnt/fedora/boot
```

This should give us a clue on what to write on your Ubuntu's menu.lst, so you can boot fedora.

---

### Post by gangsterhead3 on 2008-04-06
> **odiseo77 said:**
> Can you mount your fedora partition and list the contents of its /boot directory? Something like this:

```
sudo mkdir /mnt/fedora
sudo mount /dev/sda4 /mnt/fedora
ls -l /mnt/fedora/boot
```

This should give us a clue on what to write on your Ubuntu's menu.lst, so you can boot fedora.
ive done that

what now?

---

### Post by odiseo77 on 2008-04-06
> **gangsterhead3 said:**
> ive done that

what now?

Sorry, I forgot to tell you to post the output of the last command here (so we know what's inside /mnt/fedora/boot).

Greetings.

---

### Post by gangsterhead3 on 2008-04-07
> **odiseo77 said:**
> Sorry, I forgot to tell you to post the output of the last command here (so we know what's inside /mnt/fedora/boot).

Greetings.
total 6208
-rw-r--r--+ 1 root root   71912 2007-10-30 13:26 config-2.6.23.1-42.fc8
drwxr-xr-x+ 2 root root    4096 2007-09-20 16:17 grub
-rw-------+ 1 root root 3247574 2008-04-05 14:05 initrd-2.6.23.1-42.fc8.img
-rw-r--r--+ 1 root root 1064713 2007-10-30 13:26 System.map-2.6.23.1-42.fc8
-rw-r--r--+ 1 root root 1927704 2007-10-30 13:26 vmlinuz-2.6.23.1-42.fc8

---

### Post by odiseo77 on 2008-04-07
Well, you can try editing your Ubuntu menu.lst file (located inside /boot/grub) and adding the following lines at the end of it:

```
# Fedora 
title  Fedora
root   (hd0,3)
kernel /boot/vmlinuz-2.6.23.1-42.fc8 root=/dev/sda4 ro
initrd /boot/initrd-2.6.23.1-42.fc8.img
```

Save the file, reboot and see if it works :)

---

### Post by gangsterhead3 on 2008-04-07
thank you for making it work
thank too antman for tryin

---

### Post by odiseo77 on 2008-04-07
No problem, glad to help. I just wanted to tell you something: if you get a new kernel on fedora after an update, then you probably will want to boot with the new kernel, but if you use the previous grub entry, you'll still be using the previous kernel. You have two options here: 

a.) Add a new entry on your Ubuntu's menu.lst for the new fedora kernel in the same way we did before (which can by annoying to do every time you get a kernel update), 
or b.) install grub on fedora and then tell Ubuntu's grub to read the configuration file from fedora's /boot directory, so you don't have to touch your menu.lst every time (if you want/need help with this option, please let me know by posting here and I'll tell you how :))

Greetings.

---

### Post by igknighted on 2008-04-07
> **odiseo77 said:**
> No problem, glad to help. I just wanted to tell you something: if you get a new kernel on fedora after an update, then you probably will want to boot with the new kernel, but if you use the previous grub entry, you'll still be using the previous kernel. You have two options here: 

a.) Add a new entry on your Ubuntu's menu.lst for the new fedora kernel in the same way we did before (which can by annoying to do every time you get a kernel update), 
or b.) install grub on fedora and then tell Ubuntu's grub to read the configuration file from fedora's /boot directory, so you don't have to touch your menu.lst every time (if you want/need help with this option, please let me know by posting here and I'll tell you how :))

Greetings.

You should really look into #2 here.  Fedora upgrades kernels very regularly, so you will find yourself re-writing that grub line each time unless you do that.  I would probably have used Fedora's grub because Ubuntu doesn't change kernels like Fedora does, but at this point at least pointing to the Fedora grub would save you some work.

---

