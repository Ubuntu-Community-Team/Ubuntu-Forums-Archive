---
title: "Very slow to bootup Ubuntu after new installation"
date: 2006-02-27
forum: Desktop Environments
---

### Post by Alij on 2006-02-27
Hi there, I'm new to Linux, Ubuntu and this forum. I have installed Ubuntu 5.10 onto an IBM 600X Laptop, PIII with 12Gigabyte hard-drive. I installed it as the only system on the drive deleting my previous Win 98SE and partitioning the drive 11.5 Master and 0.512 Swap (default). When rebooting with Ubuntu it takes forever to reach the desktop screen (approx. 10 - 15 minutes rebooting 3 times) there is also quite a loud buzz from the built in speakers which was not there before. I'm sure there has to be something wrong with the setup. Can anyone please help?
Alij  :(

---

### Post by rubicon05 on 2006-02-28
I'm having the same issue on same Thinkpad 600x.  Any help would be appreciated.  After login I have a brown screen with a mouse pointer no desktop.  I have the same noise during login also, sounds like HD spinning loudly.  Thanks in advance.

Rob

---

### Post by Swiss on 2006-02-28
I don't know, it may be that Ubuntu is too much for your computer, Perhaps you should reinstall using the barebones version. 

This may help:

In order to boot Ubuntu (Hoary) on an IBM ThinkPad 600X, I had to supply the following kernel options at boot time:

    *

      acpi=off

May also be required:

    *

      ide=nodma noapic

---

The 'acpi=off' also seems to be required on Breezy (5.10) Otherwise you may wind up in the brown screen of death...

Also: Be aware that incremental kernel upgrades within Breezy may require you to re-add the boot option in the grub menu.lst file. It doesn't seem to be carried forward by the installation scripts. [ Or wasn't in my case... :-( ] 

Good luck...

P.S

If nothing works consider using Gentoo...

---

### Post by Alij on 2006-02-28
-

---

### Post by Alij on 2006-02-28
Thanks for that bit of advice.
How do I add the kernel at boot time, how would I access thisto add the kernel?

---

### Post by Ramses de Norre on 2006-02-28
In the grub menu press e to edit a line, so choose the kernel you want to edit and press e. Then pick the line which begins with "kernel", you need to press a button to edit it. I don't know which but it is displayed at the bottom. Then add the boot options and press ESC te exit the edit mode and then b to boot.
If it works: sudo gedit /boot/grub/menu.lst and aply the boot option there to the same line. It's permanent then.

---

### Post by rubicon05 on 2006-03-02
Swiss, thanks for the help, the ACPI=OFF did the trick for me.  Hope it worked for Alij, we seemed to be have identical problems.  I still get the annoying buzzing during login (even after disabling sound) but otherwise boots like a charm.

ALIJ, if you have not tried adding this yet, it may be the way to go for you as well.

Regards,
Rob

---

### Post by Alij on 2006-03-02
Hi there. Thanks for your help Swiss and Ramses. Yes, adding 
*
acpi=off
*
 to the kernel as stated definately made a difference and I was able to boot up normally. However, I was not able to solve the second part, i.e. writing it permanetly to the boot option.

i.e.
*
If it works: sudo gedit /boot/grub/menu.lst and apply the boot option there to the same line. It's permanent then. (Ramses de Norre)
*
I was not sure of how to access this part of the menu.
Still very green over here so could you spell it out to me please. How do i get to edit;
sudo gedit /boot/grub/menu.lst to make it permanent.

Many thanks for you help.

---

### Post by akiro.yamamoto on 2006-03-02
sudo gedit /boot/grub/menu.lst
Find the entry that looks like this:
title		Ubuntu, kernel 2.6.12-9-386 
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/hda6 ro quiet splash vga=792 
initrd		/boot/initrd.img-2.6.12-9-386
savedefault
boot

add the acpi=off entry to the kernel line.
Save and your done.
The next time you boot-up you should not have to enter that command.
Hope this helps. :)

---

### Post by Alij on 2006-03-09
Sorry for the delay in replying to your message. Unfortunately I have not been able to try what you suggested as the backup battery on my laptop (IBM) has died, causing me bootup problems.
 So until such time as I can get a new battery Ubuntu will have to wait. Thanks for you help anyway, I'm sure its good.:)

---

