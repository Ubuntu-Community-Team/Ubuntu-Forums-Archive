---
title: "Slow performance w/ KDE"
date: 2005-09-03
forum: Desktop Environments
---

### Post by raveman7 on 2005-09-03
Im about 3 months into playing with linux as my full time OS on my desktop and laptop. I installed Kubuntu 5.04 on my IBM Thinkpad R31 laptop recently and im having very slow performance issues. 

It is connected to my broadband connection, so far the web browing is slower than my other pc, the control center takes a while (3-4 minutes) to apply changes. Sometimes it just sits there waiting to apply changes or load the menu..

Sorry im not as detailed as id like to be but im new to this so any help would be appreciated on what i can check..

---

### Post by weekend warrior on 2005-09-04
That certainly isn't normal. Is your CPU usage very high? There could be a process running incorrectly and eating up your resources.

---

### Post by mlomker on 2005-09-04
[QUOTE=weekend warrior]That certainly isn't normal. Is your CPU usage very high? There could be a process running incorrectly and eating up your resources.[/QUOTE]

Open a Konsole window and run **top** to check out your memory and processor utilization.

Are you using wired or wireless with your broadband?  Ndiswrappers over wireless can be painful.

---

### Post by GeneralZod on 2005-09-04
Have you enabled DMA on your harddrive?

---

### Post by bin on 2005-09-04
This is in no way a criticism of Kubuntu, but it does seem to have problems with performance under some conditions. I tried it on my laptop (Compaq M700) and it was not happy. I know it's supposed to just be Ubuntu with KDE but I suspect there's more to it than that.

What is the specification of your R31? Low emory and or lack of hard drive space can cause problems

When it is taking time to do stuff is the HD light on a lot, is it  'thrashing' the drive?

Have you tried using normal Ubuntu?

May be worth altering the boot line in grub by adding pci=noacpi. When booting it gives you 2 or 3 seconds to access the boot menu (GRUB). You can then press e to edit, e to edit ht eboot line and then b to boot. This is not permanent so if you mess up - just reboot.

in light

bin

---

### Post by raveman7 on 2005-09-04
checked out TOP, i dont see anything out of the ordinary taking up all the memory and cpu, i guess this is only happening at times when im running Kaffeine. 

i am using a wired connection to my router and this is wired to a cable modem so no wireless being used. 

the specs on the IBM R31 are as follows: 
Pentium(R) III Mobile CPU 1133MHz (speedstep)
256mb of ram 
30GB hard drive
14.4" TFT. Hardware brightness (802.11b arial) working 
1024x768 (vga=791) disable stretch working 
i830MG Graphics chipset most things Xv, 2D, 3D, no DRI 
10/100 LAN, Intel EEPRO (eepro100/e100)

---

### Post by benson on 2005-09-04
can someone atleast give some tips on how to speed up KDE? :)

---

### Post by drizek on 2005-09-04
[QUOTE=benson]can someone atleast give some tips on how to speed up KDE? :)[/QUOTE]
 (make sure you have universe enabled)
sudo -s
apt-get update
apt-get install prelink
prelink -a

should give a veyr noticeable increase in appliaction launch speeds.

---

