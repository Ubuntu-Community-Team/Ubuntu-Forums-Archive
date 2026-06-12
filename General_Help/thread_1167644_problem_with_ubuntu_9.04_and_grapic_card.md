---
title: "problem with ubuntu 9.04 and grapic card"
date: 2009-05-23
forum: General Help
---

### Post by offir on 2009-05-23
hllo
i install ubuntu 9.04
and i have a grapic card nvidia

the max resulushen that i have with the nvidia 96 driver is 640x480

i tryed to install another driver nvidia 173
but it wont work
i cant even see it in the driver maneger




sorry abut my bad english

---

### Post by Kevbert on 2009-05-23
Please go to Applications-Accessories-Terminal and enter
```
lshw -C display
```
Please post back the reply by selecting the text and pressing Ctrl-Shift-C to copy and open a new post and press Ctrl-V to paste it here.
It's possible that you need to use to 180.xx driver. If you go to System-Administration-Restricted Drivers you should be able to select this (the download will take time). Next reboot the PC and you should have the new driver.

---

### Post by offir on 2009-05-23
WARNING: you should run this program as super-user.
  *-display UNCLAIMED     
       description: VGA compatible controller
       product: NV18 [GeForce4 MX 440 AGP 8x]
       vendor: nVidia Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a2
       width: 32 bits
       clock: 66MHz
       capabilities: cap_list
       configuration: latency=40 maxlatency=1 mingnt=5


this ?

---

### Post by Kevbert on 2009-05-23
Correct. Please take a look at [[COLOR="Red"]this post[/COLOR]]("http://ubuntuforums.org/showthread.php?p=7274058").

---

### Post by offir on 2009-05-23
[http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html)

i got to here
i dont know what to download 


i try to download what is in the four line
but i also dont know how to install this
i dubble klik on it and nutting heppend

---

### Post by fillintheblanks on 2009-05-23
Looks like your card is a GeForce 4 MX series. did you try going to this page [http://www.nvidia.com/Download/index.aspx?lang=en-us](http://www.nvidia.com/Download/index.aspx?lang=en-us)


the install instructions are here [http://ubuntuforums.org/showthread.php?t=1166213&page=2&post=#19](http://ubuntuforums.org/showthread.php?t=1166213&page=2&post=#19)

---

