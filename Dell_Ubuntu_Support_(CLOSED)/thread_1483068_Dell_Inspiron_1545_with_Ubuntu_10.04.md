---
title: "Dell Inspiron 1545 with Ubuntu 10.04"
date: 2010-05-14
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Saklovitij on 2010-05-14
I have a DELL Inspiron 1545 Laptop with an Ubuntu 10.04 and a Windows 7 on it. Since I have upgraded to Lucid Lynx, I sometimes  experience a strange craclking noise, sort of a sizzling when I quit Ubuntu (nothing like that when Windows). Not every time I quit Ubuntu, but quite often. What is this noise, does it signal any problem? What should I do to eliminate it?

Thanks in advance for any help.

Saklovitij

---

### Post by Jimtheplanner on 2010-05-14
Hi I've got a 1545 using 10.04 (64 bit) the only hassle I had was overheating and screen flicker both now solved.....

The noise is a new one on me.... Is it from the sound (speakers) or from the laptop hardware???

You could try a search on launchpad for a similar issue?

Jim

---

### Post by WhoSayIn on 2010-07-03
same problem here. im using ubuntu 10.04 32bit on dell inspiron 1545. screen is sometimes flickering, just for a second or half. im using ubuntu since the version 8.10 on this laptop, and there was not any problem like this before. its only on the version 10.04

---

### Post by Jimtheplanner on 2010-07-04
Screen Flicker....

Ok this is a work around, open up the terminal then: 

First 
```
sudo gedit /etc/default/grub
```

then find this line in the text file:

```
 GRUB_CMDLINE_LINUX ""
```

then add in the following detail:

 ```
GRUB_CMDLINE_LINUX "[COLOR="Red"]i915.powersave=0[/COLOR]" 
```

Once done then save the changes, then run:

```
sudo update-grub
```

Then re-boot... 

Best regards
Jim

---

### Post by dagacrack on 2010-08-03
Hi my friend, please I need to do a question about the graphics card... I have a dell inspiron 1545 too, with GMA X4500HD graphics card... I have installed Ubuntu 10.04 and I have the same problem... 

Salu2

jp

---

