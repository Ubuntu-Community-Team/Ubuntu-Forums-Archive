---
title: "GUI a bit sluggish (slow)"
date: 2010-08-26
forum: Dell Ubuntu Support (CLOSED)
---

### Post by kamohammed on 2010-08-26
nothing major, but its annoying me.
Moving windows around goes smoothly, minimizing animation moves smoothly, BUT when I restore a minimize window, or even open a new one, there is a 2 to 5 second delay before it comes up.

I had assumed it could be compiz or a bad configuration from it.
I was planning to completely remove it, and re-install it in the assumption that, that could be the problem.

Anyone have any suggestions or advice before I proceed?

I recently updated... (well installed proper) my graphics drivers so my 3d apps / games work fluently. But it didnt solve thy sluggish-ness. 

fyi:
Dell Studio 1535
ATi Radeon HD 3450 256MB
Intel core 2 Duo 2.something GHz
2 GB DDR2 RAM
5400 rpm 250GB HDD Sata

---

### Post by EPurpl3 on 2010-08-28
You should be happy, i have slow down even when i maximize, minimize or resize any window. If you solve the problem please let me know.

---

### Post by mr clark25 on 2010-08-28
i wouldnt remove compiz- just disable it. system>preferences>appearance>visual effects. just select "none" there. if your system comes back up to speed, it is probably one of the settings in compiz that you have enabled.

---

### Post by kamohammed on 2010-11-09
removed compiz and.. still sluggish...
I suspect it can be the hard drive that is messing up as it has delays when trying to read/access files.

Gonna get a new Hdd... and re-install fresh... 

Gonna try 10.10 if anything...

---

### Post by irv on 2010-11-09
> **kamohammed said:**
> removed compiz and.. still sluggish...
I suspect it can be the hard drive that is messing up as it has delays when trying to read/access files.

Gonna get a new Hdd... and re-install fresh... 

Gonna try 10.10 if anything...
I see you said your removed compiz, what I do is hit <Alt> <F2> and type ```
metacity --replace
```
and then when I want to use compiz again I just type
```
compiz --replace
```
I see you have this thread under Dell. What Dell are you using. I have a Dell Inspiron 1521 and things seem to run OK.
Edit: Oh Yes, I am running 10.10.

---

### Post by kamohammed on 2010-11-09
im using a dell studio 1535...

---

### Post by irv on 2010-11-09
> **kamohammed said:**
> im using a dell studio 1535...

Could it be that your hard drive is getting full? How much memory do you have. I increased my memory from 2 to 4 GiB. That's the most I can put in it. Here is a screen shot of my HD in gparted. 
[ATTACH]175098[/ATTACH]
The sda5 is my Ubuntu partition.

---

### Post by kamohammed on 2010-11-09
doubt my hdd was getting full...

Cant check atm since i have a new hdd installed atm 

(Long story with other problems now :/ )

but it was a 250 GB with about 20 GB used with music, some movie clips and Lineage2...
also running on 2GB DDR2 memory... 

I had 8.04 on it and the compiz worked perfectly, but got the sluggish behaviors when updated to 9.10 (8.04 -> 8.10 -> 9.04 -> 9.10) ... 

did a clean install to 10.04 and install the compiz... sadly i didnt had proper graphics drivers then, but when that was fixed, the slugginess was still present...

now thinking that I never had proper graphics drivers to begin with :/

---

### Post by irv on 2010-11-09
Maybe you could try to completely remove compiz, reinstall your video driver and see how things work. If they speed up then try to reinstall compiz. Like you said, it could be your video which is slowing things down. Going from 10.04 to 10.10 would use the same driver. On my dell 1521 I don't need to load a driver for my video, when installing 10.04 and 10.10 it just uses what ever installs and things just work.

---

