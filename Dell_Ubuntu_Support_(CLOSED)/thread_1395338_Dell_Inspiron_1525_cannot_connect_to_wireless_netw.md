---
title: "Dell Inspiron 1525 cannot connect to wireless network"
date: 2010-01-31
forum: Dell Ubuntu Support (CLOSED)
---

### Post by ninjamohawk on 2010-01-31
I'm completely new to linux, and today I installed ubuntu 9.10 onto my Dell Inspiron 1525 laptop.

Everything feels really slick except that it doesn't recognize my wireless connection. I did some intensive searching on google and found that my wireless adapter needs a driver installed in order for ubuntu to recognize it.

SO

After more searching and checking my system I discovered I needed this file
iwlwifi-3945-2.ucode

so I downloaded it, transfered it to the laptop with a flash drive. It's now on my desktop.
my question is where do I put this driver file, and how do I install it to my computer?

I realize that I'm being a newbie and I feel really embarrassed having to ask for help but help would be appreciated. Also, if I have posted this in the wrong forum I'm really sorry.

Thanks in advance!

---

### Post by corcomp84 on 2010-01-31
you need to go to the synaptic package manager and download ndiswrapper-utils-1.9  It will also download the common package.  after installing it you should be able to see the link under either the system or preferences. then you should be able to install the windows driver

---

### Post by gabo.cr on 2010-02-01
I have that same laptop.
You need to install the wireless proprietary drivers.
Just go to System > Administration > Hardware Drivers.
You will see the drivers you need to install, you will need to connect to the Internet with the Ethernet cable to do that.
;)

---

### Post by cyong999 on 2010-10-24
yes, able to find the driver, and trying to install it
but at the end saying intallation archive failed ??? what should i do ?

---

