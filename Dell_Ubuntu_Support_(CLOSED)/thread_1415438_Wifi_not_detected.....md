---
title: "Wifi not detected...."
date: 2010-02-24
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Swastiksunki on 2010-02-24
Hi,

I am new to Ubuntu Linux and I am having a big time problem to connect wifi.
I saw some video on YouTube on how to connect Wifi but my card is not being detected. I have installed new Ubuntu 9.10 and please help me out on how to connect it. I tried to see driver through Hardware driver but it is not being installed. please tell me if there is some patch to solve that problem.

---

### Post by pajus on 2010-02-25
It depends, what kind of wifi card do you have?

```
lspci | grep Network

```if you have some "broadcom" it could be problem you should. first start Administroation->update manager and after reboot (maybe it is not nesessary)  start Administration->HW drivers you pick one of them (i have bcm4312 and i've selected) BroadcomSTA driver, cause otehr one didn't work

Maybe, that is not what you are asking for...so sorry :-[

---

### Post by Swastiksunki on 2010-03-02
Hi, I tried doing that but the broadcom wifi manager is not selectted. I clicked on update manager and updated my driver is not detected. I tried to enable it but nothing works. I don't know what to do. I am frustrated now. what is a possible solution for this. my wi-fi card is not detected more over the driver is is not been updated..:( :(

---

### Post by Buntzilla on 2010-03-02
I was having this same problem with my Del Studio 1555. I just connected through a wired connection first, then updated the WiFi driver.

Worked like a charm.

---

### Post by dmzamora on 2010-03-10
I used this help in order to fix this problem.

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

I hope this helps.:KS

---

### Post by yomuffin11 on 2010-03-11
I had that same problem too on my Dell Studio 1555 , m8 !

I found my hardware driver (Broadcom STA wireless driver), installed and tried to activate it. It said it was activated but never worked from the HD. From the Live CD, however, it did work <_<

But anyways, it seemed 9.10 did not cooperate on my laptop so I tried a few other distributions and found 9.04 to work the best. I have had no problems at all so far! So if you are not to far and nothing important is saved yet, why not give it a shot?! Or just backup your important files before proceeding! XD

-Hope This Helps

---

### Post by lz1dsb on 2010-03-12
On my Dell Studio there was no problem activating the STA Broadcom driver from the System->Administration->Hardware Driver utility. 
In fact I tried the driver from the Broadcom's site, but I had some problems with it. So I recommend you to activate the STA driver from the utility. It's easier, and driver is working much better. You'll need an internet connection though, as the utility needs to download it and than insert it into the kernel.

Cheers, 
Boyan

---

### Post by perham on 2010-03-12
open a terminal,

run this command:

```
sudo apt-get install bcmwl-kernel-source
```

it should work.

---

