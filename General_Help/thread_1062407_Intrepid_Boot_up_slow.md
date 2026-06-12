---
title: "Intrepid: Boot up slow"
date: 2009-02-06
forum: General Help
---

### Post by nithinsujir on 2009-02-06
I'm a big fan of Ubuntu, but a bit disappointed with how long it takes to boot and general slowness. 

Would be great if someone could help me figure out if it's something wrong on my machine.

------[ Time to Boot ]-----------------------
Grub to Login Screen with hard disk light off - 40 seconds
Login to Desktop with hard disk light off     - 45 seconds

From login to desktop the hard disk light remains solid.
Total 85 seconds till it is useable. 
Before the latest kernel install, this time was 75 seconds.

Windows XP boots on the same machine in 60 seconds to hard disk light turn off.

-----[ System Specs: ]------------------
Dell Inspiron 1501
AMD Athlon 64 X2 (Dual Core) TK-53
Separate root partition 14 GB and is 44% used



I also tried using readahead but it didn't help.

I've attached dmesg, ps output to show the programs that run at boot and boot chart output.


I'm wondering if the hard disk performance is not upto par. Because when I start firefox it takes 12 seconds the 1st time. On the 2nd time I would expect near instant startup, but it still takes 4 seconds with hard disk activity.

Here is the output from sudo hdparm -tT /dev/sda

/dev/sda:
 Timing cached reads:   1214 MB in  2.00 seconds = 606.80 MB/sec
 Timing buffered disk reads:  110 MB in  3.05 seconds =  36.03 MB/sec


Thanks,
Nithin.

---

### Post by mb_webguy on 2009-02-06
Since you have a dual-core processor, you can enable concurrent booting, which may help some.  In the terminal, type "gksu gedit /etc/init.d/rc".  Look for the line "CONCURRENCY=none" and change this to "CONCURRENCY=shell".  Save and exit.  The next time you boot may not be any faster, but after that it should be.

---

### Post by 2hot6ft2 on 2009-02-06
You can also hit the Esc key at the grub
arrow down once to the kernel line
hit e
add "profile" to the end without the ""'s
hit Enter
hit b

It will take a long time the first time but after that it will boot a little faster.

After a kernel upgrade you'll have to do it again.

---

### Post by nithinsujir on 2009-02-06
I tried both profile and concurrency. Boot time actually increased to 95 seconds. :(

---

### Post by mb_webguy on 2009-02-06
Was that on the very next boot?  Because both concurrency and readahead *will* cause a longer boot time for the first boot after they are enabled.

---

### Post by nithinsujir on 2009-02-06
No, I rebooted 3 times. The first time it was more than 3-4 mins because of the profile.

The next two times it was 95 seconds.

---

### Post by mb_webguy on 2009-02-06
Very odd.  How much memory do you have?

I'm running 64-bit Intrepid on a 2GHz Intel Core 2 Duo with 2GB memory, and while I haven't timed it, my boot time and login time are half yours easily.  My hard drives are a small bit faster than yours (1045.02 MB/sec cached, 42.70 MB/sec buffered), but I wouldn't think that would account for such a large discrepancy.

---

### Post by nithinsujir on 2009-02-06
I have 1 G of RAM. I don't think RAM is an issue. Since the hard disk light is solid for 99% of the time, I think it's something to do with reading data.

---

### Post by nithinsujir on 2009-02-06
Btw I'm running the 32 bit version of Ubuntu, but I don't think that should be an issue.

---

### Post by oscy724 on 2009-02-09
I'm having the same but slower issue with Ubuntu 8.10(32bit) on a Pentium 4 3.06Ghz with 1.5Gb RAM with 40GB hard drive. 'Starting up...' takes 3 minutes, from there to login screen takes 4 minutes. So around 8 minutes total to get to desktop in which runs sluggish at all times afterwards.:( 

XP takes 1 minute or less on same exact machine from power on to desktop!!! Is this some type of hardware incompatability in ubuntu? BIOS maybe?

It also took about 3 hours to install ubuntu....
Is there anything that can be done??

---

