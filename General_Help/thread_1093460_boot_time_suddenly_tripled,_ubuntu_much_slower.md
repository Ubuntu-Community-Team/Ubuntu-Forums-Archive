---
title: "boot time suddenly tripled, ubuntu much slower"
date: 2009-03-11
forum: General Help
---

### Post by Haluci on 2009-03-11
I'm not sure what's going on with ubuntu right now.  Just last week ubuntu was turning on just fine... [33 seconds]("http://bayimg.com/image/laoodaabd.jpg").  That's normal.  Now, things have been acting really weird.  First, ubuntu [now takes 1:30 to boot]("http://bayimg.com/image/laoogaabd.jpg"), things are about twice as slow (running programs, etc), and cpu usage seems to be staying at about 50% (I have a dual core processor, so it seems that one core is always in use).  Does anybody know where to even start with this problem?

Thanks! :)

---

### Post by ubudog on 2009-03-11
Open a terminal Applications>Accessories>Terminal and type top.  Do you see any suspicious programs running?

---

### Post by Haluci on 2009-03-11
There's nothing suspicious, but processes seem to be taking up more cpu than normal (xorg is taking about 20%, firefox about 15%).  Every once in a while there's this "dellWirelessCtl" that pops up and takes some cpu, but it goes away quickly.

I think I'll just reinstall ubuntu, I probably just b0rked it somehow randomly.

---

### Post by Haluci on 2009-03-11
I fail. :(

---

### Post by ubudog on 2009-03-11
I suggest you upgrade to 8.10.  Much faster.

---

### Post by Haluci on 2009-03-11
> **ubudog said:**
> I suggest you upgrade to 8.10.  Much faster.

I'm running 8.10, I've just never bothered to change it in my profile. :p

---

### Post by ubudog on 2009-03-11
Oh.

---

### Post by kuja on 2009-03-11
Well, if everything seems to be using up more CPU %, maybe the CPU is being throttled. That could do that. You can check the current CPU speed at /proc/cpuinfo (and many other ways, but that one is consistant)

---

### Post by MaxIBoy on 2009-03-11
Did you mess with anything in the BIOS?

---

### Post by Haluci on 2009-03-11
> **kuja said:**
> Well, if everything seems to be using up more CPU %, maybe the CPU is being throttled. That could do that. You can check the current CPU speed at /proc/cpuinfo (and many other ways, but that one is consistant)

I was having a problem with CPU scaling earlier, getting stuck at 1GHz, but I was able to fix that and now I can go to 2GHz, which is normal (well, at least cpuinfo says I'm running at 2GHz...)

> **MaxIBoy said:**
> Did you mess with anything in the BIOS?

I've already restored the BIOS to factory settings a couple times, this hasn't changed anything (although I was mucking about in the bios before I reset it).

---

### Post by Haluci on 2009-03-13
bump.

I'm beginning to think this is a problem with my computer itself... Windows won't even start, ubuntu is still taking 3x more time to boot and going twice as slow as normal, and now my computer has a tendency to overheat.  This is really odd, since just last week my computer was running just fine.

---

### Post by ushills on 2009-03-13
it could be that some hardware is failing. i would start with runninng memtest from the grub boot menu. if one of your memory modules is failing that could cause performance slow down. beyond that it could be your processor but personally i've never had a processor fail it's always been ram failures or motherboards.  motheboards always seem to cause hanging or resets though.

---

### Post by ubudog on 2009-03-13
You should probably just get a new computer.

---

### Post by martin roland smith on 2009-03-13
does the live cd work? try taking out any usbs.

---

### Post by ushills on 2009-03-13
> **ubudog said:**
> You should probably just get a new computer.

This is never the answer although often quoted, a new cpu will cost around £50 a new motherboard less say £50, memory is now really cheap.

Try memory first, swap between modules - if the rest of the hardware is okay the main guts can be replaced affordably.  Why replace harddrive, power supply, dvd drive etc.

My suggestion is check memory first, then try clean install (move /home to new partition first). Then look at replacing components.

---

### Post by Haluci on 2009-03-13
> **ushills said:**
> it could be that some hardware is failing. i would start with runninng memtest from the grub boot menu. if one of your memory modules is failing that could cause performance slow down. beyond that it could be your processor but personally i've never had a processor fail it's always been ram failures or motherboards.  motheboards always seem to cause hanging or resets though.

Thanks for the suggestion.   memtest seemed to help... ubuntu is still running slow but it doesn't seem *as* slow as it was (and I haven't even tried windows yet).  I'll probably run memtest again tonight.

If resets and hanging are hallmarks of motherboard failures, then I don't think that's the problem.  Ubuntu runs slow, but it's pretty stable.

Do you think posting the boot messages might help?  If so, I'm not too sure how to do that...

If all else fails I'll send the computer to dell for repairs, I don't think I'm good enough to repair it myself, hehe.

---

### Post by Haluci on 2009-03-13
an update: windows still won't start, even in safe mode.  Funny that ubuntu is the only thing that's still alive on here. :p

What I'll probably try to do is take apart my computer and see if there's any obvious physical problems can can be fixed.  If not, I'll just run memtest again overnight and call dell in the morning tomorrow unless somebody comes up with another thing I could try. :p

---

### Post by ushills on 2009-03-13
installing bootchart from the repositories will produce a graphical chart of your boot processes. you will be able to post that and see what is taking the time.  this may help pinpoint an errant process.

Did memtest report any errors?

---

