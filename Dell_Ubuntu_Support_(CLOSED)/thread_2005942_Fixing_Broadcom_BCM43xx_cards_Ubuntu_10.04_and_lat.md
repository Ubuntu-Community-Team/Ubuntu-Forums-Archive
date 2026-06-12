---
title: "Fixing Broadcom BCM43xx cards Ubuntu 10.04 and later"
date: 2012-06-18
forum: Dell Ubuntu Support (CLOSED)
---

### Post by irv on 2012-06-18
I thought I would post this information in Dell Ubuntu Support for others to see.
First, I have been running Ubuntu on this Laptop going on 4 years now. Some earlier releases of Ubuntu ran with no problems. I want to say it was around the the release of 10.04 that the issues with the wifi card came into play. But there is a work around.
If you are using a Broadcom BCM43xx card (I am using a 4311). Do the following:
After installing 10.xx, 11.xx, or 12.xx making sure you have a network cable plugged in. 
1. Make sure you have dkms installed.
```
sudo apt-get install dkms
```
2. I uninstalled “bcmwl-kernel-source” package,
```
sudo apt-get remove bcmwl-kernel-source
```
3. I installed “firmware-b43-installer” package
```
sudo apt-get install firmware-b43-installer
```
4. I installed “b43-fwcutter” packager
```
sudo apt-get install b43-fwcutter
```
5. I typed into the terminal:
 ```
cat /etc/modprobe.d/* | egrep '8180|acx|at76|ath|b43|bcm|CX|eth|ipw|irmware|isl| lbtf|orinoco|ndiswrapper|NPE|p54|prism|rtl|rt2|rt3 |rt6|rt7|witch|wl'
```
This was the output:
> # which ath5k cannot recover. To prevent this condition, stop
blacklist ath_pci
blacklist eth1394
# replaced by p54pci
blacklist prism54
# replaced by b43 and ssb.
blacklist bcm43xx
blacklist uart6850
blacklist twl4030_wdt
You might have to restart the laptop at this point. Before restarting click on your network icon in the upper right corner of your desktop if you see wireless connections listed under wireless just select one and you should connect without restarting. 
I hope this will help others as it help me.

---

### Post by kiro1000 on 2013-03-20
It's help me!
THANKS

---

### Post by coldraven on 2013-03-20
Thanks, is it too late to add tags to this post? I bet that I'll be looking for it it before too long :)

---

### Post by irv on 2013-03-20
When I find something that works for me, I copy the URL and paste it and post it to an email to myself, and then file it and label it as "Howto" Fixes. It make it easy for me to find.

---

### Post by coldraven on 2013-03-21
> **irv said:**
> When I find something that works for me, I copy the URL and paste it and post it to an email to myself, and then file it and label it as "Howto" Fixes. It make it easy for me to find.

That's clever, my list of bookmarks is getting out of hand so I will give your method a try. Cheers!

---

### Post by iiSkeletorii on 2013-04-29
Worked like a charm. Banged my head against this one for a while. Thanks. :p

---

### Post by irv on 2013-04-30
> **irv said:**
> When I find something that works for me, I copy the URL and paste it and post it to an email to myself, and then file it and label it as "Howto" Fixes. It make it easy for me to find.

Recently I started do something different. I started using "Evernote Web" and use a utility call "Clip to Evernote" for webpages. Also I created a Evernote email address and I just email all my howtos to a notebook in Evernote call "Howtos". Anytime I need something I can do a quick search in Evernote.

---

