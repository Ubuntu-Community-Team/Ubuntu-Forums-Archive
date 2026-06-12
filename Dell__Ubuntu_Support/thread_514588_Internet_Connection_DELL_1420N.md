---
title: "Internet Connection DELL 1420N"
date: 2007-07-31
forum: Dell  Ubuntu Support
---

### Post by Don-Zorro on 2007-07-31
I just got my new new DeLL Inspiron 1420N .. and had not sucess connecting it to the Internet. I am just starting to work with Lynux. I already have a Windows Vista machine connected to cable modem that work perfeclty fine, so the only thing I did was to swap the Ethernet cable from the cable modem to the Inspiron, and activated the default wired connection network in the laptop with address (dchp). However, it does not work reviewing the connection information I can see that it connects to the netwrok, but there is no Internet access. Can somebody help me? Should I do something else?

Thanks.

---

### Post by deserthowler on 2007-08-01
How are you testing your internet connection? 

I found with my DSL modem I had to disable ivp6 in firefox but ping worked.

Earl

---

### Post by LMP900 on 2007-08-01
I just received my 1420n today and my wired connection didn't work right away. However, I followed the instructions on the Dell Wiki and got it working by removing the installed tg3 driver and installing a different version of the driver.

Here is the relevant information you need:

[http://linux.dell.com/wiki/index.php/Ubuntu_7.04/Issues/tg3_driver_does_not_recognize_network_controller](http://linux.dell.com/wiki/index.php/Ubuntu_7.04/Issues/tg3_driver_does_not_recognize_network_controller)

---

