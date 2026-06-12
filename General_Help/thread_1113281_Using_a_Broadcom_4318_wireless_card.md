---
title: "Using a Broadcom 4318 wireless card"
date: 2009-04-01
forum: General Help
---

### Post by jwernecke on 2009-04-01
I was having a great difficulty with using a Broadcom 4318 wireless card.  I searched many many sites for the right answer.  There are many posts out there that are very complex and very in-depth.  None of which of course work.  I am new to linux but i have already figured out that the problem is usually REALLY simple.  If you have a B4318 card use the following lines....

dpkg --purge b43-fwcutter
rm -rf /lib/firmware/b43 /lib/firmware/b43legacy
apt-get update
apt-get install b43-fwcutter 

Then after you do all of that restart your computer and ta da it works.  This worked great for me I hope it helps someone else.

---

### Post by jwernecke on 2009-04-01
Ok I was wrong I got all excited when the WiFi light came on and didnt realize that I still had my eth0 connection on.  If anyone can help with this issue I would greatly appreciate it.  I am running a Dell Inspiron B120 with a Celeron M and 1.5gigs of RAM.  It has a Broadcom 4318 wlan card and I did the previous post and the card is active but it doesnt see any networks. I know that there are networks because they are mine.  Thanks in advance

---

### Post by KenCranford on 2009-04-02
I have been frustrated while trying to get my Broadcom 4328 wireless working in my Dell Inspiron E1505 that is quite similar to your 4318 experience. I did connect via ethernet and followed the instructions in your message - but was disappointed that I still had to wireless connection. However, when I clicked System > Administration > Hardware Drivers, I noticed that I had two Broadcom wireless drivers listed - a "B43" non-proprietary driver that was enabled and an "STA" that was not enabled. I Googled "Broadcom STA adapter" and found a link to "Technix Update" - which told me to enable the STA driver, plus steps needed to log onto my WPA2 home network. It worked - and my ethernet connection was unplugged! Good luck to you, and thanks for your original message.:lolflag:

---

