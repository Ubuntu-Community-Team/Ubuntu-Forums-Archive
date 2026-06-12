---
title: "Dialup modem not detected by Dell drivers"
date: 2009-05-22
forum: Dell Ubuntu Support (CLOSED)
---

### Post by rocky5051 on 2009-05-22
Hello everyone, I recently was asked by a friend if I could setup Ubuntu on his sister's laptop, an Inspiron 1501, but I have run into one small problem which prevents me from accomplishing anything on it.

I have a dialup internet connection, and in order to setup anything on the laptop I need connectivity through the lappy's modem. I assumed, considering it is a Dell and it seems the same drivers worked on the E1505, that using the Dell OEM HSF modem drivers for linux would work.

For whatever reason, using the [method I discovered to work for Jaunty]("http://ubuntuforums.org/showthread.php?t=1143904") to get the driver to install, the modem is not detected on the laptop. The module compiles successfully, however, though it does completely kill the audio on the laptop (I can fix that).

Any suggestions?

Dell Inspiron 1501
Ubuntu 9.04 Jaunty Jackalope 32-bit
Assuming some form of Conexant HSF modem as well as a Broadcom wireless adapter and some form of ethernet port.

Thanks.

---

### Post by coffeeaddict22 on 2009-05-23
Hi,
Sounds complicated.  You're wanting to set up
1) a dial up connection from a modem, and can't get any output?
   Do you mean when you go into network manager you can't see it?  What program/s are you using as a front end?
2)Wireless, and 
3) Ethernet.
You have got some of these working?
What's the output from ```
lshw -C network
```
and 
```
ifconfig
```

---

### Post by rocky5051 on 2009-05-25
> a dial up connection from a modem, and can't get any output?

When hsfconfig is setting up the hsf modem module, it builds a module successfully but it can't find the dialup modem. Therefore, even if the driver works properly it won't facilitate a connection.


> Do you mean when you go into network manager you can't see it? What program/s are you using as a front end?

I mean it simply doesn't show up, not even using lspci or lshw while other network hardware such as the Broadcom wireless and ethernet adapters.

I use pppconfig to setup a connection and use pon/poff because it's simple.

> Wireless, and . . . Ethernet. You have got some of these working?

Yeah, which leads me to the conclusion of this thread. I brought it to a friend's house and got a high speed connection using the ethernet adapter. After that I was able to install the wireless adapter driver from the proprietary hardware drivers menu automatically without a hitch, though I was unable to configure it or tell the laptop's owner how to scan and connect to networks with it as I had nothing to test it with.

So, I managed to set it up fine despite the lack of a dialup connectivity. I still plan to figure out where the problem was because it shouldn't have had any issue.

---

### Post by coffeeaddict22 on 2009-05-25
One thought is that if it's not seen by lspci it might be turned off in the BIOS, or on a hardware switch.  I'm not sure of the key/key combination to turn the modem on or off, but there'll probably be one.

---

### Post by rocky5051 on 2009-05-25
> **coffeeaddict22 said:**
> One thought is that if it's not seen by lspci it might be turned off in the BIOS, or on a hardware switch.  I'm not sure of the key/key combination to turn the modem on or off, but there'll probably be one.

I checked the BIOS and there was an option to disable/enable it, but it was on. If I still had the laptop and I felt like forsaking all the work I had done on it I'd install Windows and see if it detects it.

Ah well, if I ever have to work on it again, I'll check if there are any hardware switches to adjust.

---

