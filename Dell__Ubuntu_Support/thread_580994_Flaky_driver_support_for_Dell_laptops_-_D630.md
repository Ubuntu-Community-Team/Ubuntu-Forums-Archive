---
title: "Flaky driver support for Dell laptops - D630"
date: 2007-10-19
forum: Dell  Ubuntu Support
---

### Post by daimer77 on 2007-10-19
Hello Ubuntu. On the surface... really really nice work. Everythings looks cool, and as linux user since 98 I am really interested in this Ubuntu release.

But... I just got my new Dell D630 laptop. I have seen I can make it run with all drivers if I go through some scripts and hacking guides posted here in the forum. 

I just don't understand why this Dell Laptop is not supported out of the box. It is  one of the most common business laptops from one of the largest Laptop producers int the World. 

The drivers exist. Everything can work. Why the ¤@!€€@ can't You manage to make it work out of the box ???

I am disappointed since I have been bragging about Ubuntu to all my collegues for long time now :(

I will try to get it work. But now adays these kind of problems are not supposed to consume time for normal users...

Best regards, Daniel Mersebak

---

### Post by gdanko on 2007-10-19
The only thing I had to fix was sound. Everything else is perfect.

---

### Post by daimer77 on 2007-10-22
Everything works for You ?

Compiz graphics, Bluetooth ?

Did You use the sound guide posted here ?

Best regards, Daniel Mersebak

---

### Post by tturrisi on 2007-10-22
Ubuntu is essentially beta software.  How can you expect it to work seamlessly out of the box?
The Dell 630, a nice solid workhorse of a laptop, can be purchased with many different harware configs, thus installing any op sys will differ on each 630 laptop.

---

### Post by slyboots on 2007-10-22
Hi.
I found some issues by D630 with Gutsy. By the Wifi card iwl4965 is working, but the Network manager is causing that the wifi don't work after hibernate and you must kill the process and restart Networkmanager and Networkdispatcher again.

Second issue is with the sound that work only with extracting alsa into kernel and after install of new kernel wont work.... Logical ;)

But the sound is don't working after suspend or hibernate too, and you must restart the pc to solve the issue.

---

