---
title: "Booting 904 nbr off of a 1GB SD card"
date: 2009-04-25
forum: General Help
---

### Post by Streamline35 on 2009-04-25
Hi, 

I feel like this is a dumb question with an obvious answer, but oh well. I'm trying to boot 904 netbook remix off a 1GB SD flash card. I downloaded the .img file, and I followed [these (very simple) steps]("https://help.ubuntu.com/community/Installation/FromImgFiles") to the letter in windows. When it is done, it's pretty much empty (4kb used out of 978mb), and when I try to boot from it, it says "missing operating system". I've tried it on two different machines, same thing. I thought maybe I needed put the image file on the drive as well, but it doesn't quite fit. I have it formatted as FAT32. Any ideas?

---

### Post by dcstar on 2009-04-25
> **Streamline35 said:**
> Hi, 

I feel like this is a dumb question with an obvious answer, but oh well. I'm trying to boot 904 netbook remix off a 1GB SD flash card. I downloaded the .img file, and I followed [these (very simple) steps]("https://help.ubuntu.com/community/Installation/FromImgFiles") to the letter in windows. When it is done, it's pretty much empty (4kb used out of 978mb), and when I try to boot from it, it says "missing operating system". I've tried it on two different machines, same thing. I thought maybe I needed put the image file on the drive as well, but it doesn't quite fit. I have it formatted as FAT32. Any ideas?

You shouldn't be "formatting" anything, the image copy should wipe the drive/card. Delete any partition you created and try again.

---

### Post by Streamline35 on 2009-04-25
I didn't format it after writing the image to it. That's just the format the card is in (and it was what it was formatted as before writing the image to it)

---

### Post by dcstar on 2009-04-25
> **Streamline35 said:**
> I didn't format it after writing the image to it. That's just the format the card is in (and it was what it was formatted as before writing the image to it)

As I said, delete the partition and try again.

---

### Post by Streamline35 on 2009-04-25
I just tried that - deleted the partition, then immediately wrote the .img to it. Same problem. It seems like there should be more than 4kb used. 

(btw, I appreciate your answers. I'm a bit of a linux noob)

---

### Post by dcstar on 2009-04-25
> **Streamline35 said:**
> I just tried that - deleted the partition, then immediately wrote the .img to it. Same problem. It seems like there should be more than 4kb used. 

(btw, I appreciate your answers. I'm a bit of a linux noob)

Ok, do it manually in Ubuntu (first find the /dev for the SD card):
```
sudo fdisk -l
sudo dd if=the-.img-file-name of=/dev/the-sd_card
```

I also had trouble making a 1GB USB with the tool but the dd worked fine.

---

### Post by jimv on 2009-04-25
Call me crazy, but couldn't you just use the USB boot creator app to do this?

---

### Post by dcstar on 2009-04-25
> **jimv said:**
> Call me crazy, but couldn't you just use the USB boot creator app to do this?

No, it does not work with .img, only .iso or CDs.

---

