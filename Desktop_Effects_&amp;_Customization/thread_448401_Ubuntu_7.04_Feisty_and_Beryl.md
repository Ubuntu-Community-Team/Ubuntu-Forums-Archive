---
title: "Ubuntu 7.04 Feisty and Beryl"
date: 2007-05-19
forum: Desktop Effects &amp; Customization
---

### Post by Abdulaziz on 2007-05-19
Hi,

Last week i saw a video on YouTube someone had Ubuntu and was playing with his desktop showing off his Beryl effects, I liked it a lot. Next day I installed Ubuntu ( i was a Windows XP user , but i have experince with Linux ) and I download Beryl and installed it. When I tried to open Beryl-manager, WSOD shows up.

I'm using Ubuntu 7.04 Feisty and Beryl 0.2.1


my laptop is Dell Inspiron 6000.


Please help me with this :(.
Pease.

---

### Post by Ub1476 on 2007-05-19
Just so it said, many has expired problems with v. 0.2.1. You should rather try 0.2.0:) 

Good guide here:

[http://ubuntuguide.org/wiki/Ubuntu_Feisty#How_to_install_Beryl_.28ATI.29](http://ubuntuguide.org/wiki/Ubuntu_Feisty#How_to_install_Beryl_.28ATI.29)

Follow the second part of the guide were you are using XGL. Starts like this: ...Alternate method: Using closed source FGLRX drivers from ATI...

Hope it works now:)

---

### Post by strumluff on 2007-05-19
Steady on Ubi, does a Dell inspiron 6000 have an ATI card or Nvidia card?

If it has an ATI card then follow Ubi's instructions otherwise use the same guide but you can install it a lot easier with AIGLX and a standard gnome session so you can follow the guide from the top.

---

### Post by Ub1476 on 2007-05-19
It has ATI X300. I checked:)

---

### Post by strumluff on 2007-05-19
Ah good job, hey don't know why I've been calling you ubi for ages just realised its just Ub :P

So Abdulaziz follow Ub's post, you **will** have to force the version to 0.2.0 as the higher version in the universe repo does not support XGL, which is the only method you can use to install Beryl. Don't worry its all covered in the second half of that guide.

---

### Post by Abdulaziz on 2007-05-19
Thank you ... I will try it now .

---

### Post by drummingpariah on 2007-05-19
man, nVidia rocks my socks.  I just set Beryl up on my Ati-based machine and it really was a bit of a pain.  My nVidia card was a snap, and the drivers were very easy to install in the first place as well (once I figured out how to kill X so I could install them).  I wish you luck, and look forward to your results!

---

