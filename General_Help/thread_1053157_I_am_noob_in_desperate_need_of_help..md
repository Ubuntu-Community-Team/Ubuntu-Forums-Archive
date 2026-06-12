---
title: "I am noob in desperate need of help."
date: 2009-01-28
forum: General Help
---

### Post by mutiny218 on 2009-01-28
Hello, and thanks in advance for your time.
Last Christmas, I received a computer as a gift with two operating systems installed, Ubuntu 8.10 and Windows 2000. My brother in law, the person the gift came from, is very good with computers and I'm positive that everything is installed properly. When I turn my computer on, it boots into 
Ubuntu by default. For gaming purposes, I would like to boot it into Windows 2000, but I have very little technical knowledge of Ubuntu and only slightly more of computers in general. In short, I have no idea how to do that. If someone could walk me through this process it would be greatly appreciated. Don't be afraid to make your instructions incredibly dumbed-down, it might be necessary. Thanks again.

---

### Post by N4zgu1 on 2009-01-28
I guess you have Grub installed, if that is the case. Just move the arrow down until you reach the windows option and press enter  when you boot

---

### Post by sdowney717 on 2009-01-28
you can change it to boot windows 2000 by default

you just edit one file called menu.lst
this is in a folder /boot/grub/menu.lst

just move windows entry to the top

type in gksudo gedit /boot/grub/menu.lst

move this up to the beginning of the grub list
it wont be exactly the same as mine

title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1


save the changes and reboot


menu.lst

```
## ## End Default Options ##

title		Ubuntu 8.10, kernel 2.6.27-11-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=d6269386-1a91-432d-9014-cce8e93eb891 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=d6269386-1a91-432d-9014-cce8e93eb891 ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.27-9-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=d6269386-1a91-432d-9014-cce8e93eb891 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=d6269386-1a91-432d-9014-cce8e93eb891 ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=d6269386-1a91-432d-9014-cce8e93eb891 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=d6269386-1a91-432d-9014-cce8e93eb891 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1
```

---

### Post by drs305 on 2009-01-28
You can change the default OS via a gui app called StartUp-Manager. 

Install via command line with "sudo apt-get install startupmanager" OR:

To do this entirely via gui, open Synaptic (System, Administration, Synaptic Package Manager).

Make sure the *universe* repository is enabled: Settings > Repositories > tick/enable the *universe* repository.
Hit "Reload" if it was not enabled initially.
Find and highlight *startupmanager* in the right pane. Right click, "Mark for Installation".
Hit "Apply" in the top menu.

To Run:
System, Administration, StartUp-Manager.
In the "Boot Options" tab:
Select from the "Default operating system": Windows

While in StartUp-Manager, you might want to change the menu timeout so you have time to select which OS you want during boot. You can change the menu timeout in the same tab.

There is a link in my signature line for more information on how to use StartUp-Manager.

---

### Post by mutiny218 on 2009-01-28
Ok, just to make sure I'm not making a huge, stupid mistake here...

Is there a way I can check and be absolutely positive that Windows is, in fact, installed?

---

### Post by sdowney717 on 2009-01-28
do you get a boot menu option when starting the computer?
if you do, select the windows entry and see if it boots

---

