---
title: "Wireless networks not being detected on Dell Inspiron 14R"
date: 2010-08-28
forum: Dell Ubuntu Support (CLOSED)
---

### Post by deepak.sebastian on 2010-08-28
Hi 

I installed Ubuntu 10.04 on my Dell Inspiron N4010 laptop using wubi yesterday. After reading a few threads I managed to get my wired ethernet up and running. But I am still facing issues with the wireless device. On the network connections at the top right of the screen the wireless device shows up as disconnected. I tried giving the explicit WLAN name and connecting it but it doesn't. 

In my ifconfig output the device shows up as eth1(instead of wlan0). Also in the network connections program in System->Preferences, nothing shows up.

Could someone help me out here?

Thanks.
Deepak

---

### Post by mike909 on 2010-08-29
go into your bios and disable the "wlan toggle". That's what did it for me. I just can't figure out how to get the headphone jack to work.

---

### Post by mike909 on 2010-08-30
Follow my post at:
[http://ubuntuforums.org/showthread.php?t=1505697&page=9](http://ubuntuforums.org/showthread.php?t=1505697&page=9)
report back and let me know. Does your headphone jack work? That's what I'm trying to figure out.

---

### Post by xircon on 2010-08-30
Or just update, I have an N5010, run:
```
sudo apt-get update && sudo apt-get upgrade
```

I assume the wireless card is a DW1501?

---

### Post by mike909 on 2010-08-30
The N4010 ships with one of two wireless cards. My solution works with the broadcom 4747 (lspci)
Deepak,
please show us the output of "lspci" to see which card you have.

---

### Post by xircon on 2010-08-30
Yes, thats why I asked, mine reports as a 4727.

---

### Post by mike909 on 2010-08-30
> **deepak.sebastian said:**
> Hi 
After reading a few threads I managed to get my wired ethernet up and running.
Depending on how he fixed his wired connection, he may have screwed up the wireless connection. (ie if he used the compat-wireless driver fix, it overwrites some files that the wireless nic needs to use). If you read the 10 page thread where I posted the solution to this you'll see what I mean.

---

### Post by deepak.sebastian on 2010-09-07
Mike

Thank you for all the instructions that you posted in the thread. They completely fixed my networking problems! :)

Regarding the sound, as you said the laptop speakers work but earphones don't! Have you found any solution to that yet?

Thanks again!

---

### Post by mike909 on 2010-09-07
Yes, the solution for the sound problem is located here:
[http://ubuntuforums.org/showthread.php?p=9817325#post9817325](http://ubuntuforums.org/showthread.php?p=9817325#post9817325)

---

