---
title: "Multiple Ubuntu distributions."
date: 2009-01-23
forum: General Help
---

### Post by DarknessEnemy on 2009-01-23
HI everybody, I hope that you are ok!
I came to ask something.

Can I install more than 1 ubuntu distro?

Or Can I install one ubuntu distro and other "properly"?

I hope that you can answer me ^^

---

### Post by azmo35 on 2009-01-23
Hi,if you ask if is possible dual boot 2 distros the answer is yes,but you ask on wubi so if you wanted ubuntu/kubuntu/xubuntu you have to use synaptic to install the requered software and choose at login the session ubuntu/kubuntu/xubuntu,but this have limitations for each kde/xfe you need space on wubi,for kde i know you need 500+mb of space,if wubi is tight use [lvpm]("http://ubuntuforums.org/showthread.php?t=438591"),i hope this help.

---

### Post by DarknessEnemy on 2009-01-23
Thanks (and yes, I was talking about wubi), but that means that I cannot install 64 and 32 distros at the same time with wubi?

---

### Post by brandon88tube on 2009-01-23
Not sure if I understand you entirely here, but if you are looking to install multiple versions of Ubuntu using Wubi then this it what you want to do.

This is if you already have one version installed using Wubi.
1. Rename the ubuntu folder to ubuntu32 or ubuntu64 depending on the version that is already installed. You can also name it however you like as long as you know what is what.

2. Then open the newly renamed folder, I'll be using ubuntu64 as the example. Go to the winboot folder and open up menu.lst with a text editor. Change the lines listed into this. Note: The name ubuntu64 will change to whatever you named your folder to.```
title find /ubuntu64/disks/boot/grub/menu.lst
	find --set-root --ignore-floppies /ubuntu64/disks/boot/grub/menu.lst
	configfile /ubuntu64/disks/boot/grub/menu.lst

title find /ubuntu64/install/boot/grub/menu.lst
	fallback 2
	find --set-root --ignore-floppies /ubuntu64/install/boot/grub/menu.lst
	configfile /ubuntu64/install/boot/grub/menu.lst
```
3. Run the wubi.exe again and install the other version of ubuntu.

4. If you wish to install a third one, then follow the steps 1-3 again.

---

### Post by DarknessEnemy on 2009-01-24
Thank you so much... This helped a lot.^^

---

### Post by brandon88tube on 2009-01-24
No problem, just glad that I could help.

---

### Post by Openrulers on 2009-02-05
I do have a similar question. But I want install Fedora 10 with Ubuntu 8.10 with the help of Wubi in Windows XP.
Will the same idea will work
Thank you

---

### Post by brandon88tube on 2009-02-05
> **Openrulers said:**
> I do have a similar question. But I want install Fedora 10 with Ubuntu 8.10 with the help of Wubi in Windows XP.
Will the same idea will work
Thank you

I don't think you can do it with wubi as it is intended to install Ubuntu only.

---

### Post by Openrulers on 2009-02-13
Thank you.
Any other workaround to run two distributions of Linux in Windows.

I tried to run Fedora 10 with unetbootin on windows XP machine in which Wubi installed Ubuntu 8.10 , I had a screen for triple booting but Unetbootin cannot find Fedora iso it seems 
I am still trying for a workaround.
Anybody with any luck with triple booting

---

### Post by har02052 on 2009-03-30
I am wondering how to make this work correctly.  I want to install Linux mint (which has it's own version of wubi), 8.10, and 9.04. All using wubi so that when I get to that first boot screen from Windows I will have Vista, Mint, 8.10 and 9.04.  Is this possible?  I see what you are saying previously with modifying the winboot file, but how exactly does that change the options on the boot screen?

---

