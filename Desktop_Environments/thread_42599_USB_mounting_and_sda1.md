---
title: "USB mounting and sda1"
date: 2005-06-18
forum: Desktop Environments
---

### Post by dqsis on 2005-06-18
Hello Ubuntu Friends! 

Well I have the following problem which I "partially" solved:

I was trying to mount my usb-mp3 player and my digital HP camera. 

I followed the normal procedure (edit fstab>> /media/camera etc and mount /media/camera etc) but I was always getting the error:

mount: special device /dev/sda1 does not exist

I searched the forums but 90% of the posts were like:

"Ooohhh Ubuntu found my camera immediately" or "WooooW... I didn't do anything and my USB is there" (Why on earth people write that posts anyway? They get me upset!!!  :roll: )

Well, anyway! Enough with nugging! Suddenly I found a post that saved my life! 

If you are faceing the same problem, you have to type in (as su):

modprobe -r ehci-hcd

and then (a miracle happens) your USB is there! 

The problem now is that I can copy my pictures by using gtkam. But how can I do it manually since mount doesn't work???

How can I browse to the camera folder (I repeat that gtkam can!). 

If I manage going there manually then I will be able to also use my USB mp3 player (is there for that a program like gtkam?)

Thanks!

/DQ

---

### Post by mrcbrown on 2005-06-18
Some digital cameras talk to things diffrent - I know my Canon never shows up as a removable drive - it talks slight different, had similar issues on Mac - would never show, but iPhoto hop'd up and started the dialog to download it.

What kind of MP3 player are you trying to attach?

---

### Post by beefsprocket on 2005-06-18
Not sure if it will help but... what about removing the device and then plugging it in again -- after which run dmesg. The last few lines should show the details of your device etc. regardless of whether it is mounted or not.

---

### Post by ante0 on 2005-06-20
If your camera has a removable card inside it should be detected automaticly... my camera were autodetected as a removable-drive. If you want you could try pluggin it into a computer with Windows XP installed, if its detected it should be so in linux too.

---

