---
title: "dd truncates flash capacity but I want it all"
date: 2009-06-23
forum: General Help
---

### Post by mmmmna on 2009-06-23
UNR 9.04 written with dd to an 8Gig SDHC.

I followed these istructions: [https://help.ubuntu.com/community/Installation/FromImgFiles](https://help.ubuntu.com/community/Installation/FromImgFiles)

The 8 Gig is now 900 something megs total capacity. I want to use the whole 8Gig capacity of the card after the image file is written to the 8Gig SDHC card.

Man dd doesn't produce any obvious answers, so I wonder what options to dd would produce the full 8Gig capacity after properly writing the install structures.

As the Ubuntu install page instructs me to do it:
sudo dd if=/path/to/downloaded.img of=/dev/device/node bs=1M

the bs=1M portion says to read and write 1 megabytes at a time, so that really isn't the best answer until I get to bs=8000M. Which seems wrong since input (the img file) will underrun the 8000M specification.

I also wondered about notrunc, but the file is still only 900+ megs, the lost card capacity problem might still remain.

Has anyone used dd for what I'm looking to do? I really do not want to install 'Imagewriter' and the dependencies since my Ubuntu system drive is full.

---

### Post by dcstar on 2009-06-24
> **mmmmna said:**
> UNR 9.04 written with dd to an 8Gig SDHC.

I followed these istructions: [https://help.ubuntu.com/community/Installation/FromImgFiles](https://help.ubuntu.com/community/Installation/FromImgFiles)

The 8 Gig is now 900 something megs total capacity. I want to use the whole 8Gig capacity of the card after the image file is written to the 8Gig SDHC card.
........

The image provides a boot/install device, it does not provide a filesystem.

You are supposed to put this image on a temporary bootable device for install (like  USB stick), and then reformat that device once the install is completed.

---

