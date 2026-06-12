---
title: "3 way boot GRUB"
date: 2006-06-09
forum: Desktop Environments
---

### Post by Uta on 2006-06-09
At present on my Dell laptop there are 3 distros. 

title		Ubuntu, kernel 2.6.15-23-386 (on /dev/hda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hda1 ro quiet splash 
initrd		/boot/initrd.img-2.6.15-23-386

-------------------------------------------------
title		Kubuntu, kernel 2.6.15-23-386
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hdc1 ro quiet splash
initrd		/boot/initrd.img-2.6.15-23-386

-------------------------------------------------

I recently resized the hdc drive, it has Kubuntu on it and now Mepis. When I installed Mepis I didn't install GRUB because I didn't want it to destroy my working dual boot but of course I want to add it to my menu.lst. now.
Kubuntu is hdc1 and Mepis is hdc3. I know I need to edit the menu.lst and probably the device.map ( yes?). How do I add Mepis and how do I know what the "title,root, kernel,initrd" info is for this distro. Where do I locate that info. Thanks!

---

### Post by jimbob on 2006-06-09
Here is my Mepis entry modified to fit your setup  (if I understand it correctly):

title           MEPIS kernel 2.6.15-1-586tsc (on /dev/hdc3)
root           (hd1,2)
kernel         /boot/vmlinuz-2.6.15-1-586tsc root=/dev/hdc3 nomce quiet vga=791          
initrd          /boot/initrd.img-2.6.15-1-586tsc
savedefault
boot

Give it a try and see what happens.
________________________________       
  If I can't be Mr. Root I won't play ...

___________________________________
AMD 64 Sempron 3400+ 512MB 60GB IDE 80 GB SATA
Gigabyte GA-K8NS socket 754 nForce3 250 chipset
nVidia GeForce2 MX/MX400 64 MB

[COLOR="Red"][SIZE="2"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

### Post by Irony on 2006-06-09
From an earlier post;

Its quite simple just edit your current grub list (don't over install it with Fedora's);

[PHP]# This entry added by me as an example
# installation on /dev/hda9
title		Fedora Core 4, hda9
root		(hd0,8)
kernel		/boot/vmlinuz-2.6.11-1.1369_FC4 root=/dev/hda9 ro quiet splash
initrd		/boot/initrd-2.6.11-1.1369_FC4.img
savedefault

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		XP Home SP2, hda1
root		(hd0,0)
savedefault
makeactive
chainloader	+1
[/PHP]
To find out what your kernel and initrd file versions are, simply mount your Fedora partition from Ubuntu and navigate your way to the /boot folder and look up the exact versions.

---

### Post by Uta on 2006-06-09
[QUOTE=Irony]From an earlier post;

To find out what your kernel and initrd file versions are, simply mount your Fedora partition from Ubuntu and navigate your way to the /boot folder and look up the exact versions.[/QUOTE]
Great!
Please remind me what the mount command is. "sudo mount /dev/hdc3"

only sez it's not in /etc/fstab which I know so what do I need to do?
Thanks again.

---

### Post by Irony on 2006-06-09
First you make a directory for example in the /mnt folder;

[PHP]sudo mkdir /mnt/mepis[/PHP]

Then you mount it;

[PHP]sudo mount /dev/hda3 /mnt/mepis[/PHP]

You'll have to replace hda3 with whatever the partition that your distro is installed on.

---

### Post by Uta on 2006-06-09
First thanks for your help, I got it to boot. Things are a little strange, starting Mepis, it briefly shows the Kubuntu Splash image logo and then goes into Mepis? Why would it first show Kubuntu if I chose Mepis? It does boot into Mepis successfully.

---

### Post by jturnbul on 2006-06-11
[QUOTE=Uta]First thanks for your help, I got it to boot. Things are a little strange, starting Mepis, it briefly shows the Kubuntu Splash image logo and then goes into Mepis? Why would it first show Kubuntu if I chose Mepis? It does boot into Mepis successfully.[/QUOTE]

probablay a grub splash screen you install or came install, that displays till your other OS boots

---

