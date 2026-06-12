---
title: "Dell inspiron 1545 SD card reader not working."
date: 2010-08-23
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Kilokk on 2010-08-23
Hello, I recently installed Ubuntu on my Inspiron laptop, and everything is working out great so far, except for the card reader.  It works sometimes, but when i really need it, it doesn't work.  Is there anything I can try?

Please excuse this newb question, I have been searching for a while now and I tried to avoid posting this, but here it is.

---

### Post by niziris on 2010-08-24
I found this [thread]("http://ubuntuforums.org/showthread.php?t=1454403") but their solution didnt work for me
maybe you will have better luck :)

if u succeed plsss explain how u done it
I have Dell vostro with same memory card problem

---

### Post by Jimtheplanner on 2010-08-24
Hi Folks,

I have a 1545 and the card reader works a treat for me. I use the 64 bit version of 10.04.

I have one suggestion. Before removing an SD card I use a right click on the desktop icon and "eject" rather than "Safely Remove Drive" (I'm doing this from memory as I don't have a card with at the moment).

If I use the "Remove" option I would have to reboot before another card is recognised. However, use eject and I can repeat the cycle many times over....without a reboot.

Hope this helps 

Jim

---

### Post by aa-hcl on 2011-01-02
to fix the SD card reader we need the following:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/605043](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/605043)

see #10  for the correct filename

Solution:  create the file "sdhci-pci.conf" that contains one single line "options sdhci debug_quirks=0x40" in a directory "/etc/modprobe.d" 

root@aa-i3:/etc/modprobe.d# cat ./sdhci-pci.conf 
options sdhci debug_quirks=0x40

and then reload the modules:

root@aa-i3:/etc/modprobe.d# rmmod sdhci-pci
root@aa-i3:/etc/modprobe.d# rmmod sdhci
root@aa-i3:/etc/modprobe.d# modprobe sdhci-pci

(or reboot)

and the SD card now works...

I was looking for the above solution for several months (although, not really that much looking for it), so I am very glad now that my SD card reader now works on dell E5510!

---

### Post by entodoays on 2011-01-20
My card was being recognised only if the card was inserted on boot. Now I tried this solution and it's not even recognising the card on boot-up. I tried erasing the .conf file and rebooted but the issue remains.

Any suggestions? 

I have a Dell Inspiron 6400.

---

### Post by entodoays on 2011-01-20
My card was being recognised only if the card was inserted on boot. Now I tried this solution and it's not even recognising the card on boot-up. I tried erasing the .conf file and rebooted but the issue remains.

Any suggestions? 

I have a Dell Inspiron 6400.

---

### Post by entodoays on 2011-01-20
My card was being recognised only if the card was inserted on boot. Now I tried this solution and it's not even recognising the card on boot-up. I tried erasing the .conf file and rebooted but the issue remains.

Any suggestions? 

I have a Dell Inspiron 6400.

---

### Post by luckyniji13 on 2011-02-19
I have an Inspiron 1545 and the SD card reader stopped working out of nowhere. I don't know what happened but it was working fine a few months ago. I tried rebooting the laptop with the SD card in it, didn't work.  I also tried seeing I needed to update the drive but it didn't need an update. 

I don't know...
There was someone talking about creating some file in a few posts up from here but I have no clue what that is and I don't want to try something dangerous though. 
[-o< -Kel

---

