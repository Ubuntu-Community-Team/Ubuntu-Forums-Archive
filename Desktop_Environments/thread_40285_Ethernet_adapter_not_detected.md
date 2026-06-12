---
title: "Ethernet adapter not detected"
date: 2005-06-08
forum: Desktop Environments
---

### Post by friedtestes on 2005-06-08
I just finished installing kubuntu and my ethernet adapter was not detected, i searched around and when i get into the network config everything is greyed out. I tried clicking on administrator mode but it just goes back to the same thing. It is an onboard gigabit 10/100/1000 Ic plus, i have the disk and i checked and it does have drivers for linux but i dont know how to get them off of the cd or install it. any help would be nice thanks.

---

### Post by kleeman on 2005-06-08
What does 
lspci | grep net
show?
I'm trying to figure out exactly which nic you have......

---

### Post by friedtestes on 2005-06-08
when i typed that it said
0000:02:0b.0 ethernet controller: sundance technology inc: unknown device 1023 (rev 41)

---

### Post by kleeman on 2005-06-08
Hmm this website suggests that your card is supported

[http://www.linux.com/howtos/Ethernet-HOWTO-4.shtml](http://www.linux.com/howtos/Ethernet-HOWTO-4.shtml)

(look for sundance)

Try this:

sudo modprobe sundance

and report what happens at the end of  /var/log/dmesg

If it looks good try

sudo dhclient eth0

also after modprobing above report what ifconfig shows....

---

### Post by tyttuz on 2005-09-28
I have the same problem qith my Ethernet adapter.

when I type 
lspci | grep net

show this:
0000:06:08.0 ethernet controller: Broadcom Corporation NetXtreme BCM5788 Gigabit Ethernet  (rev 03)

Anyone knows how can I put my Ethernet adapter working?

Thanks,
Tito

---

### Post by kleeman on 2005-09-28
There are some linux drivers for your card here:

[http://www.broadcom.com/drivers/downloaddrivers.php?archive=1](http://www.broadcom.com/drivers/downloaddrivers.php?archive=1)

make sure you follow the documentation carefully.

---

### Post by tyttuz on 2005-09-28
I already downloaded... and I follow the documentation

Please see:
[http://ubuntuforums.org/showthread.php?t=69845](http://ubuntuforums.org/showthread.php?t=69845)

---

### Post by tmmuk on 2005-09-29
I have been having trouble getting my wireless card working, and the onboard ethernet on my PC Chips M870 motherboard doesn't seem to work either

when I type lspci | grep net I get 

0000:00:04.0 Ethernet controller: Silicon Intergrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 91)

how can I get it to work?

---

### Post by shakin on 2005-09-29
[QUOTE=tmmuk]I have been having trouble getting my wireless card working, and the onboard ethernet on my PC Chips M870 motherboard doesn't seem to work either
when I type lspci | grep net I get 
0000:00:04.0 Ethernet controller: Silicon Intergrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 91)
how can I get it to work?[/QUOTE]

you need to run 'sudo modprobe sis900'

If that works, add sis900 to the bottom of /etc/modules so it runs every boot

---

### Post by shakin on 2005-09-29
[QUOTE=tyttuz]I have the same problem qith my Ethernet adapter.

when I type 
lspci | grep net

show this:
0000:06:08.0 ethernet controller: Broadcom Corporation NetXtreme BCM5788 Gigabit Ethernet  (rev 03)

Anyone knows how can I put my Ethernet adapter working?

Thanks,
Tito[/QUOTE]

run 'rmmod tg3' to remove the crappy redhat driver if it's loaded. Edit /etc/modules and make sure there is no line referencing the tg3 driver. Delete all lines that do refer to it, such as creating an alias to tg3. Now create an alias to the bcm5700 driver that should be installed if you followed the manufacturer's instructions. In /etc/modules, add 'alias eth0 bcm5700' to the bottom.

Now reboot and see if it works.

Keep in mind that I'm just using information I googled. I don't have this card.

---

### Post by tmmuk on 2005-09-29
How will I know if it has worked?

also, when I try and edit etc/modules and save, it wont let me

it thinks you have to be root 

how can I save it as root?

also, will adding ndiswrapper into this list make it launch upon startup? (sudo ndiswrapper -m didnt seem to work)

EDIT: will sudo chmod 777 /etc/modules do it?

---

