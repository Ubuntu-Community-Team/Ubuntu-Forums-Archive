---
title: "Bluetooth GPS experiences"
date: 2009-01-24
forum: Education &amp; Science
---

### Post by FiReSTaRT on 2009-01-24
I've never played with any BT-connective devices (EVER) and I've never had to dump GPS receiver data directly into my Ubuntu box, so I wanted to ask you guys about your experiences. I'm thinking of getting a bt GPS logger, so I have a couple of questions..
1) I'm assuming that standard bt connectivity shouldn't be an issue. While I'll test it with my cell phone, I'd appreciate your experiences even if it's just a confirmation of your assumption.
2) Do you need a special driver/software for the device or can you just connect and download the GPX straight from the device?
Thanks in advance ladies and gentlemen.

---

### Post by AnvarOne on 2009-01-30
It has some tricky points. First of all you have to have good bt support.
So best install blue man instead of bluez.
Then connect to your bt gps with blue man en set up a trust.
After that you have to read out the serial channel & set it up in rfcomm.conf. When you done that you can connect with a command...

So a lot of commands is needed to get a bt gps working on ubuntu 8.10
But the good news is, it works :)
Only one prob, can't find a good gps nav program...

A suggestion doh is swscanner, works good for some wardriving (one note, start the program a root (so edit the start as root command))

---

### Post by FiReSTaRT on 2009-09-07
I got a RoyalTek and this guide was very helpful to me [http://www.pwrusr.com/tips-and-tricks/royaltek-rbt-2210-ubuntu/](http://www.pwrusr.com/tips-and-tricks/royaltek-rbt-2210-ubuntu/) Once I went through the steps, I was able to collect great sample datasets for the Quantum Navigator project.

---

