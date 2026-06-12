---
title: "Who can save my hard drive? (1420) The kernel is killing my hdd!"
date: 2007-10-13
forum: Dell  Ubuntu Support
---

### Post by JangMunho on 2007-10-13
A "famous" bug showed in kernel 2.6.20, which also affects ubuntu 7.04. The bug is that the kernel will not stop the hard drive properly when system shut down.
There is a solution, that is making a script to enable the patch provided by linux group, but unfortunately, the script won't work in my system. Everytime I shut down my 1420, the hdd will still make a "pop" sound, and the "power-off_retract_count" value (which is provided by smartctl that included in package "smartmontools", you can also get it from apt-get. once you installed, type "sudo smartctl --device=ata --attributes /dev/sda" in a concole window, then you will get the information) will increase 1. 

Then I noticed someone said the new kernel 2.6.22 has solved the problem, so I downloaded the source files, and build the kernel. The kernel can boot, and works perfectly except for the hard drive problem!:mad:

The power-off_retract_count value is still increasing, and I'm crazy now.

Why even the newest kernel can show the problem?! In other word, am I the only one in the world to have that a bad luck?](*,)

Who bought 1420n which has ubuntu 7.04 pre-installed it the laptop? Check your smartctl info, do you have the problem, too? Or can someone tell me how to solve the problem? Pleeeeease...

Thanks...

---

### Post by neptho on 2007-10-13
I can not reproduce this problem on my 6400, but I am also running a self-installed Kubuntu platform.

First, install hdparm 
```
%sudo apt-get install hdparm
```

Then, create the file /etc/acpi/suspend.d/87_hdparm.sh with the following:

```
#!/bin/sh
/sbin/hdparm -f /dev/sda
/bin/sleep 1s
```

Remember to chmod this file 755, and set it owned by root:root

This should force the device to flush the buffers, then wait one second before finishing the (usually last) script of turning off the framebuffer device.

---

### Post by JangMunho on 2007-10-13
Sorry, but the script seems to have no effects at all.
The hdd still made a pop sound, and the P.O.R.C value again increased 1.

---

### Post by neptho on 2007-10-13
> **JangMunho said:**
> I'm going to try this...
Thanks, neptho...

If that doesn't help, [here's the link to the 'Master Kernel' thread](http://ubuntuforums.org/showthread.php?t=311158).

---

### Post by JangMunho on 2007-10-13
As I guessed, after I built 2.6.23.1 in my laptop, the shutting down process still has that problem. But I found an interesting things maybe will unveil the problem, that is, when I shut down my laptop under Windows, the Power-Off_retract_count value will add 1, too.

I cannot describe the feeling I had when I found this fact this morning. You know, I spend about a mounth on this problem, the kernel changed from 2.6.20-16 to 2.6.22.9, then 2.6.23.1, but now, smartctl told me, Windows has an incorrect shutting down, too...

Another interesting thing is that  when I switch to Windows to check my hdd with hdd scan, the power-off_retract_count is 69 instead of 105 shown by smartctl in linux.

Maybe god thought my kernel is too old, so he gave me such a "problem" to force me to update my kernel. Anyway, I'm using kernel 2.6.23.1, the newest, which came out on October 12nd...

---

### Post by JangMunho on 2007-10-13
No, what I've said is not the truth...
In fact, I know now, 69=105. It's because 69 is a hex figure, that means, 0x69=105. I then shut down the laptop, and then power on, the value changed to 6A, 0x6a=106, and smartctl shows the value is 106...

I'm more than crazy now.

[SIZE="5"]**What i wanna know now is that what does "power-off retract count" mean?**[/SIZE]

---

### Post by saru411 on 2007-10-13
i find the way you ask for help annoying and very counter productive. i highly doubt anyone who can help you will do so with your attitude.

---

### Post by Linicks on 2007-10-14
> **JangMunho said:**
> 
What i wanna know now is that what does "power-off retract count" mean?

That means your hard drive is shut down 'uncleanly' and the emergency head park was used.

Here is the ultimate thread about this, and how to fix it:

[http://ubuntuforums.org/showthread.php?t=566072&page=1](http://ubuntuforums.org/showthread.php?t=566072&page=1)

Nick

---

### Post by nick_h on 2007-10-14
Have a look [here](http://en.wikipedia.org/wiki/Self-Monitoring,_Analysis,_and_Reporting_Technology).  Different manufacturers may implement the SMART technology slightly differently.  The PORC may be 192 or perhaps 228.

What is the manufacturer of your drive?

---

### Post by Palmyra on 2007-10-14
I used to have a strange popping/beeping noise at the end of a shutdown, and that was solved by some guide I followed.  Anyhow, now that beeping noise is back.  This all happened while using Feisty.  I don't know what this beeping noise does, but it appears to show up randomly, and I don't know whether it is causing any damage. 

I intend on selling this hard drive soon, but I would still like to sell it in a working state.  I'll do a search on the guide I previously used, and I'll get back to you (it may take me a while).  Shoot me a PM to remind me.

---

### Post by Squizzle on 2007-10-14
By all accounts, as irritating as the noise may be, having a drive park this way should not destroy it. The click is a good thing if anything, it's part of an 'emergency stop' mechanism to **prevent** the drive from getting damaged on shutdown. It probably ain't ideal, but I don't think we can start accusing ubuntu of wrecking hard drives.

---

