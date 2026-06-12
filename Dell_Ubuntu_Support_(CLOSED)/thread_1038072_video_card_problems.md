---
title: "video card problems"
date: 2009-01-12
forum: Dell Ubuntu Support (CLOSED)
---

### Post by michaelbenton on 2009-01-12
I just got a dell 830 with an academic install of xp which I partitioned with gparted freeing up half the hard drive.  I installed ubuntu to free space without a hitch.  I then connected to the internet and set my advanced preferences to extra.  I was prompted to install nvidia driver.  I downloaded and rebooted.  Upon reboot where I would normally see a login screen I see a light screen that darkens with a vertical dark line of about 1.5 inches wide.  Is it that my card is not supported yet and how would I verify this.

I am new to this and I was wondering if anybody had any ideas how I can first disable the video card driver I installed and help me find one that will work.  I am green with text mode so please be specific with code.

System info:
intel core 2 duo cpu
t9300 @ 2.5 GHz
3.5 GB of RAM
Nvidia Quadro NVS 140M
 

Thank you for you help,

Michael Benton

---

### Post by rocknrolf77 on 2009-01-12
Maybe try hitting ctrl + alt + F1

Log in to console (Just write username and password)

```
sudo aptitude remove nvidia-glx
```
```
sudo aptitude install envyng
```
```
sudo envyng -t
``` or ```
sudo envy -t
```
Cant't remember which one is the right.

And follow instructions.

---

