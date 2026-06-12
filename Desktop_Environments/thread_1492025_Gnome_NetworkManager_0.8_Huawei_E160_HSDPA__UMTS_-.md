---
title: "Gnome NetworkManager 0.8 Huawei E160 HSDPA / UMTS - does not connect"
date: 2010-05-24
forum: Desktop Environments
---

### Post by lupo23 on 2010-05-24
Hi There.

I decided to post at this section, because NetworkManager is belongs to gnome. Please give me a hint, if this is not the correct section of the forum.

Some month ago i bought a UMTS / HSDPA Stick "HUAWEI Mobile Connect E160". I worried about getting it running with Ubuntu, but it was freaking easy to get it running. Even less complicated than installing the same device with windows.

It worked some month without any problem and then suddenly, didnt work any more. If i plug the device to my laptop (lenovo x61) unter linux now, i still can click to start the mobile broadband, it trys to connect some time, but shows "disonnected" at the end (dont know the exact message in englisch, because i use german language prompts).  The same device still works fine with same hardware with windows vista at all 3 usb ports. I deleted the mobile broadband settings couples of times and made a new one, without any effect to the behavior.

Now i don't know how to isolate the cause or reason further.

I would be thankful for your advice.

Thank you for your attention.

Merlin.

---

### Post by Sven6210 on 2010-05-24
Did you recently install any other tools accessing your E160? I had a comparable problem some time ago. I was able to use my 3G stick without any additional software out-of-the-box. One day I installed some other software using my 3G stick and since then it stopped working.

As I was not that familiar with Ubuntu when it happened (I am still a beginner) I went the brute-force-way and reinstalled Ubuntu from scratch. Et voila, everything worked again.

Maybe you have also installed some new packages that are in conflict with the gnome network manager?

---

### Post by Minsky on 2010-05-24
Could the OS be identifying the HUAWEI stick as a storage device instead of as a modem? Open your file manager and see if its listed as a storage device, if so, unmount it and you should be able to use it as a modem again.

---

### Post by 3g modem on 2010-05-24
[http://www.3gmodem.com.hk/Huawei/E160.html](http://www.3gmodem.com.hk/Huawei/E160.html)
 
The Huawei [E160]("http://www.3gmodem.com.hk/Huawei/E160.html") 3G modem is very common and used in many countries by different mobile operators. Generally considered a lower end model and for this reason is often the dongle supplied with Pay As You Go mobile broadband. Although lower end, it is a perfectly capable modem and for most users easily fulfils their requirements. 
The E160 comes in several flavours [E160]("http://www.3gmodem.com.hk/Huawei/E160.html"), E160E, E160G and E160X. The difference between the models is the **UMTS frequency bands** at which they work.

---

### Post by seanm2 on 2010-06-03
Did you ever find a solution to this problem? After a month or so of working without any problems, all of a sudden I have the same problem as you.

This morning it worked.  Then I disconnected.  Then I tried to connect again later and it didn't work.  I didn't install anything in between.  I am clueless as to why it stopped working.

---

### Post by bonninho on 2010-09-18
I am a new ubuntu user and i need to know how to install and use the huawei E160 HSDPA USB stick. Someone please help me out.

---

### Post by startling on 2010-11-04
I too cannot connect with my Vodafone Huawei E160X dongle.

This is especially frustrating as it worked in Ubuntu 8.10, but will not work in 10.04!

I have installed Betavine Connection Manager but that also cannot connect.

I have installed usb-modeswitch but that does not work either. 

Any suggestions would be gratefully received.

---

