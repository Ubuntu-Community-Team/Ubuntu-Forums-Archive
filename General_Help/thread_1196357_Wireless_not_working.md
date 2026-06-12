---
title: "Wireless not working"
date: 2009-06-24
forum: General Help
---

### Post by rgroene on 2009-06-24
Okay, I don't know if I'm posting this in the right place, especially as it is sort of more about Windows than about Ubuntu.

I recently got a new 250 GB hard drive, and I decided to dual boot Ubuntu Linux and Windows XP Pro on it. I partitioned my hard drive, using 80 GB of EXT3 for Linux, 80 GB of NTFS for Windows, and 90 GB of FAT32 for files that I want to use on both OS's (I later found out that Ubuntu can read and write to an NTFS partition, but I didn't realize this at first.) Anyway, both operating systems installed fine, except that I can't get wireless connection in Windows (it works fine on Linux). When I go to Network Connections, there is nothing listed except for the LAN connection. I had windows installed a while back on my old 80 GB hard drive, and I used the OS recovery disk to get Windows re-installed on this computer. On my old version of Windows, the wireless worked just fine, and all I had to do was double click on the wireless icon and choose a network to connect to. Does anybody know what might be causing this or what I can do to fix this?

---

### Post by synapsys on 2009-06-24
You need a driver for your wireless card. 

Go to the card manufacturer's website, download the driver, and install it. If you don't know what wireless card you're using look up the model number of your computer on google (windows) or open up a terminal (ubuntu) and type:

```
lspci | grep Wireless
```

---

