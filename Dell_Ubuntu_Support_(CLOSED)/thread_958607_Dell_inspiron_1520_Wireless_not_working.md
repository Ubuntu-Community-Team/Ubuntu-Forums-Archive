---
title: "Dell inspiron 1520 Wireless not working"
date: 2008-10-25
forum: Dell Ubuntu Support (CLOSED)
---

### Post by hhashim on 2008-10-25
I installed ubuntu 8.04 on my dell inspiron 1520 every thing went fine no problem at all, but when I do search for wireless network it show me no networks available though I have my own AP a few feet a way. what do I do to connect to my AP ?

---

### Post by Teamgeist on 2008-10-26
can u post the outcome of ```
lspci
``` please.

---

### Post by beidache on 2008-10-26
> **hhashim said:**
> I installed ubuntu 8.04 on my dell inspiron 1520 every thing went fine no problem at all, but when I do search for wireless network it show me no networks available though I have my own AP a few feet a way. what do I do to connect to my AP ?
Check this page, I had the same problem but after follow this steps everything was working good

[http://ubuntuforums.org/showthread.php?t=475963](http://ubuntuforums.org/showthread.php?t=475963)

Hope helps u

---

### Post by wiimaster67 on 2008-10-26
I heard the new ubuntu 8.10 will come with the driver needed to connect through a Dell wireless 1390 mini-card.
Im not sure thought...

---

### Post by casey02 on 2008-10-27
Perhaps you like to try to check if your interface is brought up by the following command :

sudo ifconfig

or iwconfig

you should see

eht0 (for your lan card)

wlan0 (perhaps for your wirelss card)

or if you are using a Atheros wifi card, if would be driven by MADWIFI driver, and you should have the following:

ath0

hope it point you to some way. good luck.

---

### Post by hhashim on 2008-12-29
Thank you all

---

