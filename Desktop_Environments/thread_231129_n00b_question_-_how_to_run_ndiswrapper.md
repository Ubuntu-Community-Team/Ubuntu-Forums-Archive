---
title: "n00b question - how to run ndiswrapper"
date: 2006-08-07
forum: Desktop Environments
---

### Post by skecherkid on 2006-08-07
I went to the ndiswrapper Wiki and am in the process of following some instructions.  I added ndiswrapper by using sudo modprobe ndiswrapper and I see it loaded using lsmod.  

The instructions tell me to load my windows driver by typing 
ndiswrapper -i <filename>  but when I run this in the terminal I get:
bash: ndiswrapper: command not found

However as I said I can see it:
 lsmod | grep ndis
ndiswrapper           177364  0
usbcore               130692  3 ndiswrapper,uhci_hcd

Two questions - what am I doing wrong in running the command and also, how do I get ndiswrapper to be loaded when I startup?

---

### Post by Jagot on 2006-08-07
Try running a sudo before the command.

Also, to get it to load automatically run this after the modprobe:

```
sudo nidswrapper -m
```

---

