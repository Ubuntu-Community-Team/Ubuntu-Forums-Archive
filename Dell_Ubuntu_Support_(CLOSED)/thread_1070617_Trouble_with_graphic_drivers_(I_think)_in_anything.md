---
title: "Trouble with graphic drivers (I think) in anything over 7.10 and dell inspiorn 2600"
date: 2009-02-15
forum: Dell Ubuntu Support (CLOSED)
---

### Post by MacHaddock on 2009-02-15
I have problems installing anything later then 7.10 on my dell inspiron 2600. Well actually I can install it but there is something wrong with the graphic drivers I think. I have heard somewhere that it's because they stopped using proprietary drivers after 7.04 but that when you update your system to 7.10 it brings the once you had on the 7.04 system. That trick doesn't seem to work after 7.10 though.

All i get on the screen is something that looks like a horizontal color bar code.

I would be very glad if you could help me out with any information as I'm having trouble finding any myself.

---

### Post by geneh2 on 2009-02-15
I am new at this but I had to go with Hardy 8.04 to get drivers for the graphics on my Dell C400.  Good luck

---

### Post by theUg on 2009-02-18
I finally got it to work about a week ago. Using Xubuntu 8.10. Here are the links to write-up and to another thread:

[http://theug.pp.ru/en/information-technology/linux/finally-linux-worked-on-dell-inspiron-2600/](http://theug.pp.ru/en/information-technology/linux/finally-linux-worked-on-dell-inspiron-2600/)
[http://ubuntuforums.org/showthread.php?t=1011213](http://ubuntuforums.org/showthread.php?t=1011213)

---

### Post by MacHaddock on 2009-02-28
Yes I got it working!

---

### Post by armandh on 2009-03-01
I solved my older computer with onboard video / newer Ubuntu
by purging compiz, explained

[http://andrewtheart.blogspot.com/2008/12/blank-screen-on-startup-after.html](http://andrewtheart.blogspot.com/2008/12/blank-screen-on-startup-after.html)

except with root terminal you do not need the sudo prefix

---

### Post by MacHaddock on 2009-03-10
Ok i didn't get it working properly. There is still scetchy areas on the screen after running the os for a bit... 

Any ideas?

---

### Post by theUg on 2009-03-29
I thought it was a video RAM issue, but
```
grep -i videoram /var/log/Xorg.0.log
```
gives out
```
(==) intel(0): VideoRam: 131072 KB
```
or 128 MB.

I'm running Gnome (regular Ubuntu) right now and memory is filled to 85-90 % all the time with swap at 35-40% or 275 of 705 MB. And that is with upgraded memory to 512 MB (System monitor shows 493,8 MB). All I am running right now is Opera with 7 windows, terminal and system monitor. XP obviously runs faster here.

---

### Post by MacHaddock on 2009-05-08
ok I have now got the same problem with 9.04 but it "works" if I change the xorg. The problem now is that I get this strange graphics malfunctions. I'll ad a picture so you can see for yourself

---

