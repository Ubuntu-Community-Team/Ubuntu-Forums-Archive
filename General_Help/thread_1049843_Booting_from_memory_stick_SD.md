---
title: "Booting from memory stick SD"
date: 2009-01-25
forum: General Help
---

### Post by Blackdragon1400 on 2009-01-25
Since there is no option in my BIOS to boot from an SD card I am currently trying to find a way to add it in the Grub  /boot/grub/menu.lst

I have only found ways to do this for USB boots. Any know what I could do???
Thx

---

### Post by 2hot6ft2 on 2009-01-25
> **Blackdragon1400 said:**
> Since there is no option in my BIOS to boot from an SD card I am currently trying to find a way to add it in the Grub  /boot/grub/menu.lst

I have only found ways to do this for USB boots. Any know what I could do???
Thx
There isn't an option for it in mine either. BUT, what I did was installed to it using a usb SD card reader. Then put it in the SD card slot and it worked fine. Apparently the SD card reader is connected internally like a usb card reader.

I don't have a grub entry for mine. If the card is in it boots from it. If it's not in it boots normally. So can't help with the grub entry with the info you have given.

---

### Post by Blackdragon1400 on 2009-01-25
I'll try to see if my laptop recognizes the internal card reader as usb. As for an entry for Grub I'm trying to find out what exactly Grub recognizes an SD card as. Example.

title BackTrack 3 USB
    root (hd1,0)
    makeactive
    chainloader +1

(hd1,0)=USB for Grub in this case
Im looking for an entry closer to that if that is more precise.
For now Im going to try another boot.

---

### Post by Blackdragon1400 on 2009-01-25
I just tested to see if my internal card reader was recognized as USB, it is not. I understand you were speaking of an external card reader, but i checked to make sure. Im surprised that I cant find any information on the web about this...

I have also tried an external card reader like you suggested. It did not work, I did not even see the laptop try to read anything off of the SD card because the light on the card reader never came on... 

Does anyone have another suggestion???

Is there a way to check to see where a device is mounted (other thatn "mount") to determine the boot point that grub wants? ex.

(hd1,0)

---

### Post by Blackdragon1400 on 2009-01-25
bump...

---

### Post by RobMalcolm on 2009-01-25
This is maybe not the smartest suggestion, but have you checked if there is a newer version of your bios available, or that the bios doesn't have a hidden option. The reason I mention this is that my bios doesn't give boot from USB as an option. However if you plug one in, and then list the bios boot options it appears.

---

### Post by Blackdragon1400 on 2009-01-25
Upon further investigation apparently the mount point for my SD card in the internal reader is listed as
/dev/mmcblk0p1
which I am assuming means "memory card block 0 partition 1" there is only one partition on that card.

And when in my USB card reader
/dev/sdb1

hope this can add to the needed information on how I can get the computer to boot from the internal card reader.

---

