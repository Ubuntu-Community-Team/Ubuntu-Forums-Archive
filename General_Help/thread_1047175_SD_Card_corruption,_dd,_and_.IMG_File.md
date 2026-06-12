---
title: "SD Card corruption, dd, and .IMG File"
date: 2009-01-22
forum: General Help
---

### Post by 1awesomeguy on 2009-01-22
My SD card somehow got corrupted. I used the "dd" command to make an .img file and used "recoverjpeg" to recover missing jpeg files. I would still like to recover my missing RAW files however and have been having some difficulties.

I have tried using "mount" to mount the IMG and I tried converting the IMG to ISO using a program called "iat". I am still at a loss however even after searching Google for the last hour.

Any help would be *greatly* appreciated! Thanks in advanced.

---

### Post by unutbu on 2009-01-22
Have you tried using the command
```
sudo mount -o loop FILE.img /mnt
```
to mount FILE.img? 

You will find this command, and further commands to try to recover files here:
[https://help.ubuntu.com/community/DataRecovery#Extract%20individual%20files%20from%20recovered%20image](https://help.ubuntu.com/community/DataRecovery#Extract%20individual%20files%20from%20recovered%20image)

This page explains how to use Foremost, Scalpel, Magic Rescue, Photorec, and recoverjpeg.

It's wise that you made a copy with dd. You could in theory try each of these recovery tools. 

Best of luck! Let us know how it goes...

---

### Post by 1awesomeguy on 2009-01-22
I used a couple of the programs mentioned in that documentationon on the IMG file and was able to recover almost all the files. Thank you.

---

