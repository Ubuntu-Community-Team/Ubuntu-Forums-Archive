---
title: "Another &quot;Wheres all my RAM thread?&quot;"
date: 2008-12-04
forum: General Help
---

### Post by supchaka on 2008-12-04
I googled and yahoo'd for info on RAM in ubuntu and found alot of arguments and conflicting information. 

I have 2 systems running 8.10. My laptop is a core 2 duo with 3gb of ram and the system shows 2.9gb. I'm fine with that one.

My other machine is a 2.4 quad with 4gb of ram and the system shows 2.8gb. Theres a command someone posted (can't recall which) to display the memory info. It shows the speed, amount, physical bank locations, serial # etc. That screen shows my 4gb correctly. My swap file is 8gb so I know it saw the 4gb on the install. I don't have integrated video so I know thats not taking from it. 

On that same machine I loaded the 64bit 8.10 and then my memory shows as 3.3gb

Does this seem normal? The 64 bit seems more responsive than the 32 with navigating gnome and single apps. From what I've read 64 bit usually runs applications slower than 32 and doesnt really start to shine until you run alot of apps. Either way, even if I were to stay with the 64bit I'd expect it to at least use the full 4gb of memory.

---

### Post by dabl on 2008-12-04
> **supchaka said:**
> 

Either way, even if I were to stay with the 64bit I'd expect it to at least use the full 4gb of memory.



My experience for a couple of years now is that it is rare for the full 4GB of memory in my system to be "used", and it also kinda depends on what you mean by "used". Linux just doesn't use the memory the way Windows does, and I assume that is your reference point.  Mostly it gets used as cache.  You really have to work at it to get it using more than 2GB for active processes.  On the rare occasions when I have pushed my hardware, like running two instances of gwc while browsing the web and playing a video, I ended up with the CPU as the bottleneck, not memory.  :)

---

### Post by binbash on 2008-12-04
This is a known problem.
[http://samiux.wordpress.com/2008/01/10/how-to-use-4-gb-ram-on-a-32-bit-ubuntu/](http://samiux.wordpress.com/2008/01/10/how-to-use-4-gb-ram-on-a-32-bit-ubuntu/)

---

### Post by sdennie on 2008-12-04
What command are you using to determine that the 64-bit install isn't seeing all 4GB of RAM?  I would try:

```

free -m

```

---

### Post by Kevbert on 2008-12-04
It may be that you have not set up the bios to use memory address re-use on the PC showing only 3.3Gb. It will probably be something like memory address remapping (which is the result of a historical limit being set on the amount of memory that the computer was expected to address).
Run memtest from the bootmenu, if this doesn't improve the amount of memory displayed with your 64 bit OS.

---

### Post by supchaka on 2008-12-04
free -m showed it  at 2807, I went ahead and loaded the server kernel and it now shows 3.8 I dont know if theres a downside to me doing that but it works and if I screw it up I can just start again! Thats how I learn. Thanks for the comments :)

---

### Post by supchaka on 2008-12-04
Well I dont know if its from what I did, but my sata to sata transfer rate got destroyed. Im getting 5mb/sec right now copying some video to my other drive. Its all good, I'm copying the files because I was getting ready to reload 64 anyway, it just seems better in my case.

---

### Post by Kevbert on 2008-12-05
The server version will show the maximum amount of memory available as it supports [[COLOR="Red"]PAE[/COLOR]]("http://en.wikipedia.org/wiki/Physical_Address_Extension").  You should have a setting in bios to use this 'additional memory'.
Using
```
free -m
```
gives me 3956Mb for 4Gb physically installed using the bios setting and 64 bit Ubuntu.

---

### Post by Nathan Sweeney on 2008-12-05
> **Kevbert said:**
> The server version will show the maximum amount of memory available as it supports [[COLOR=Red]PAE[/COLOR]]("http://en.wikipedia.org/wiki/Physical_Address_Extension").  You should have a setting in bios to use this 'additional memory'.
Using
```
free -m
```gives me 3956Mb for 4Gb physically installed using the bios setting and 64 bit Ubuntu.

I have 4 GB installed and showing 3892 mb in free -m.  I'm not sure where this bios setting would be.

BTW, Kevbert, do you really have a 1.6 **MHz** system running linux? ;)

---

### Post by hyper_ch on 2008-12-05
It may show less ram with PAE or 64bit because you might have a shared video card. So some ram could be assigned there.

---

### Post by Kevbert on 2008-12-05
> **Nathan Sweeney said:**
> I have 4 GB installed and showing 3892 mb in free -m.  I'm not sure where this bios setting would be.

BTW, Kevbert, do you really have a 1.6 **MHz** system running linux? ;)

Unfortunately, you'll have to hunt for the bios setting as it may not immediately be obvious. It may be reassign memory addresses or use memory hole.
Yes, it's an old Acer Travelmate (Centrino) laptop which runs both Xubuntu and Ubuntu quite well even when using compiz and playing DVDs at the same time.  I also have an old Athlon 900MHz running Xubuntu, Ubuntu 8.04 and 9.04 with a 32Mb Voodoo Video card and 512Mb RAM. Unfortunately compiz isn't supported on this (and it would be very slow if it did!!!)

---

### Post by Nathan Sweeney on 2008-12-05
> **Kevbert said:**
> Unfortunately, you'll have to hunt for the bios setting as it may not immediately be obvious. It may be reassign memory addresses or use memory hole.
Yes, it's an old Acer Travelmate (Centrino) laptop which runs both Xubuntu and Ubuntu quite well even when using compiz and playing DVDs at the same time.  I also have an old Athlon 900MHz running Xubuntu, Ubuntu 8.04 and 9.04 with a 32Mb Voodoo Video card and 512Mb RAM. Unfortunately compiz isn't supported on this (and it would be very slow if it did!!!)

You sure you don't mean 1.6 **GHz**?  :)

I've looked around in bios, but my options seem limited with HP.  I'm fine with what I have though.

---

### Post by Kevbert on 2008-12-05
OOPS - Thanks Nathan Sweeney.

---

