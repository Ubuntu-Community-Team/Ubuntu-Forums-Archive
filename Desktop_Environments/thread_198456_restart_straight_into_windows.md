---
title: "restart straight into windows?"
date: 2006-06-17
forum: Desktop Environments
---

### Post by delfick on 2006-06-17
hello

currently i have a dualboot between ubuntu (best OS ever!) and windows with Ubuntu being the defualt in the Grub menu.

Is it possible to restart ubuntu and tell it to go straight into windows just for that particular restart?

thnx

---

### Post by rumli on 2006-06-17
[QUOTE=delfick]
Is it possible to restart ubuntu and tell it to go straight into windows just for that particular restart?
thnx[/QUOTE]

You can use:

```
sudo grub-reboot [number]
```

where [number] is the entry number of Windows XP in your grub menu.

To calculate what [number] should be, look at your Grub Menu when it shows up during boot, and count the number of lines before (but not including) the Windows boot option. (Include the "Other operating systems:" line in your count).  For example, in the following screenshot [http://yekubuntu.free.fr/warty/images/grub.png]("http://yekubuntu.free.fr/warty/images/grub.png"),
[number] would be 4 because there are 4 lines before the Windows option.

NOTE: In order to get this to work, you must make sure to change the line:
```
default    0
``` to ```
default    saved
``` in your /boot/grub/menu.lst file.

---

### Post by delfick on 2006-06-17
if i do this, will ubuntu stay default in the grub menu after restarting straight into windows?

---

### Post by habakkuk on 2006-06-18
I assume you want to re-start into Windows just for that time (keeping Ubuntu as default for the next time etc).
When you see the Grub menu, use the arrow keys to highlight Windows, and press Enter. Windows will start up. You will not need to change any code for this approach. If you want Windows to be the default, then the grub/menu.lst file will need to be changed.

---

### Post by Chris03 on 2006-06-18
The default setup for Grub is a bit annoying since you need to press Esc to access the list. This is an example of a minimalist Grub entry:

default 0 # Tells which one is default, the list starts at 0 with the second entry being 1
timeout 3 # How long to wait in seconds before auto-selecting the default

title		Microsoft Windows
root		(hd0,0) # First number represents hard drive number, second is which partition
savedefault
makeactive
chainloader +1

title		Ubuntu
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.*(can vary) root=/dev/hda* ro quiet splash # This will change depending on the kernel installed, don't change the text
initrd		/boot/initrd.img-2.6.* # This changes also
savedefault
boot

That's all that's needed for a basic dual-boot. Using the Esc key won't be needed if using this config, it'll show the choices right away and you can use the up and down arrow to select which one.

---

### Post by rumli on 2006-06-18
[QUOTE=delfick]if i do this, will ubuntu stay default in the grub menu after restarting straight into windows?[/QUOTE]

Yes.  Ubuntu will remain the default; when you reboot Windows, it will boot back into Ubuntu automatically.

---

### Post by delfick on 2006-06-18
[QUOTE=rumli]
NOTE: In order to get this to work, you must make sure to change the line:
```
default    0
``` to ```
default    saved
``` in your /boot/grub/menu.lst file.[/QUOTE]

in that file before that line it says 

> # WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default		0

first of all what is dmraid
and secondly how do i know if i'm using it?

thnx

---

### Post by delfick on 2006-06-21
anyone?

---

### Post by rumli on 2006-06-21
One way to check that you are not using dmraid is to see whether the dmraid package is even installed.  You can do this by search for packages named "dmraid" using  Synaptic Package Manager).

I don't know exactly what dmraid is, but I found this webpage which has a short description: [http://www.linuxmanpages.com/man8/dmraid.8.php]("http://www.linuxmanpages.com/man8/dmraid.8.php").

The following page also provides some information: [https://help.ubuntu.com/community/FakeRaidHowto]("https://help.ubuntu.com/community/FakeRaidHowto").

---

### Post by delfick on 2006-06-22
thnx for that, it isn't installed, so all is good :D:D

---

