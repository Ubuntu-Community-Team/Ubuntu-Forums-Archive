---
title: "Corel Linux Photo Paint install error"
date: 2005-10-29
forum: Desktop Environments
---

### Post by rem on 2005-10-29
Hi,

First of all, I would like to thank you all involved into this great project and for your patience you showed here with us all.

This is my first post even though I first installed Ubuntu few month ago. Everything here on this forum or the Unofficial guide were pretty enough for me as a long time Windows and first time Linux user, and I managed to get almost everything I needed from my local copy of Ubuntu Hoary then Breezy latest.

First time when I got to a dead end was when I tried to get installed a Linux copy of Corel Photo Paint.
I'm developing and designing websites for a living and searching for some Windows alternates (besides Gimp) I was thinking to give myself a second chance to replace Photoshop so even the Internet is full of threads announcing that Corel brought it's products to Linux desktops, I hardly found a valid download link for it here (seems that linux.corel.com is down) [http://www.linuxsoft.cz/en/sw_detail.php?id_item=104]("http://www.linuxsoft.cz/en/sw_detail.php?id_item=104")

Even in this package there's an installer and it should be very easy to handle, I couldn't make any use of it because of this error: **Qt: Locales not supported on X server**. 

I searched the Ubuntu forums and others but no results to it. Then I tried to install some of it's libraries (I thought that might be a dependences issue) but I broke my packages and blocked apt-get. It took me some more time and other searches to find about how to fix it and I did but no hope with Photo Paint and finally I gave up. Please can you advice? Any help on this would be greatly appreciated!

Thanks a lot for reading this and hats off for Ubuntu! It's different, but it surely makes a difference!

My best.

---

### Post by claydoh on 2005-10-29
That app is waaay old, from 2000, and it may not be compatible anymore. If you want to try something, look in the /CorelPHOTOPAINT9Lnx/dists/slink directory and you will find a whole bunch of deb files. But I doubt it will work as the base libraries have changed a lot since then. 

One application that is very similar in scope and capabilities iirc is Krita, which is a KDE application.

---

### Post by rem on 2005-10-30
Hi,

Thanks a lot for the tip! I wouldn't thought that I'm so way behind... it's kind of funny :)  But what happened after all with newest Corel products? Aren't they supporting Linux anymore? Oh, I know: Microsoft might bought them off ;) 

My best.

---

