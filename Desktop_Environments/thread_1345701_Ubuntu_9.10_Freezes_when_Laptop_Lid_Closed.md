---
title: "Ubuntu 9.10 Freezes when Laptop Lid Closed"
date: 2009-12-04
forum: Desktop Environments
---

### Post by VeGeTa-X on 2009-12-04
I am have been trying to search on this forum on how to resolve and issue with ubuntu 9.10  when I closed my laptop lid and then reopen it the computers freezes and the screen goes black and the mouse and keyboard are frozen I have seen other threads were people have had the same issue has anyone figured out how to solve this issue?  it is very very annoying

---

### Post by ajgreeny on 2009-12-04
What is the setting for your laptop when the lid is closed?  You can find that in the power management utility.  If it is for suspend, what happens if you use "suspend" manually?  If you have the same problem you will need to find out why that is happening.  I have that problem on my old acer laptop which will never come out of suspend, so I set the screen to just blank when the lid is closed, rather than suspend.  Not as good for power saving but better than nothing.

---

### Post by VeGeTa-X on 2009-12-04
well I took a look at power management and it was set to suspend but i have changed it to go blank when I closed the lid and I have the same results but I when I load ubuntu 9.04 i do not have the same issue the laptop lid closes fine.

---

### Post by ajgreeny on 2009-12-05
So what happens when you suspend manually?  Do you get back to a proper desktop?

---

### Post by VeGeTa-X on 2009-12-05
when I suspend manually it actually goes into suspend mode and it comes back fine.

---

### Post by vdbergh on 2009-12-15
I found out that the problem is kernel mode setting. You may disable
it by passing nomodeset as a kernel option.

---

### Post by VeGeTa-X on 2009-12-15
ok kool can you let me know how to disable the passing of the nomodeset as a kernel option?  Thx for your help

---

### Post by VeGeTa-X on 2009-12-15
> **vdbergh said:**
> I found out that the problem is kernel mode setting. You may disable
it by passing nomodeset as a kernel option.

ok kool can you let me know how to disable the passing of the nomodeset as a kernel option?  Thx for your help

---

### Post by mmeija on 2010-01-01
> **VeGeTa-X said:**
> ok kool can you let me know how to disable the passing of the nomodeset as a kernel option?  Thx for your help

this was pissing me off for quite some time;
same thing, 9.04 works good; 910 freezes nomatter what the power management settings are.
my laptop is a dell latitude d505
 
anyway i'm not sure this is the most elegant way to add this setting but essentially all you do is 

```

sudo nano /boot/grub/menu.lst

```

your looking for the first uncommented "kernel" line
at this point mine looks like this:

```

kernel          /boot/vmlinuz-2.6.31-16-generic root=UUID=b9ad83fd-77c0-4834-bdcb-29d632f38e47 ro quiet splash

```

appened nomodeset as follows:

```

kernel          /boot/vmlinuz-2.6.31-16-generic root=UUID=b9ad83fd-77c0-4834-bdcb-29d632f38e47 ro quiet splash nomodeset

```

save,reboot,and you are good
(don't copy and paste my example; uuid is somewhat unique)

this likely doesn't stick through kernel upgrades. also, this setting relates to the new intel graphics stack i assume - and as such i don't knoww hat the true ramifications of this setting might be yet, does anyone have a good link for detail on exactly what nomodeset does? thus far i've not found good clear info.

---

### Post by mmeija on 2010-01-01
a little more googling on nomodeset makes me thing it completely disables the fresh intel stack? that kinda sucks

but haven't seen definitive explanation

---

### Post by olafurg on 2010-01-05
I have the same problem as described here. Have a Dell Latitude D505 with 9.10 set up. When I close the lid, no matter what the setting is, the computer freezes. When I set it manually to suspend/hibernate it succeeds as expected. 

However I don't see any /boot/grub/menu.lst file.

```
olafur@olafur-d505:/boot/grub$ ls /boot/grub/menu*
ls: cannot access /boot/grub/menu*: No such file or directory
```

Should I manually enter the line you suggested as a replacement or is there some other solution available? 

This was working fine in Ubuntu 9.4.

---

### Post by mmeija on 2010-01-05
> **olafurg said:**
> I have the same problem as described here. Have a Dell Latitude D505 with 9.10 set up. When I close the lid, no matter what the setting is, the computer freezes. When I set it manually to suspend/hibernate it succeeds as expected. 

However I don't see any /boot/grub/menu.lst file.

```
olafur@olafur-d505:/boot/grub$ ls /boot/grub/menu*
ls: cannot access /boot/grub/menu*: No such file or directory
```

Should I manually enter the line you suggested as a replacement or is there some other solution available? 

This was working fine in Ubuntu 9.4.


well you are either in really bad shape, or the file's moved somewhere. this machine i'm on was originally installed as 9.04 and i did a dist-upgrade to 9.10, so it's possible the file has moved.

in fact quick google on "where is menu.lst 9.10"
got me to this article [https://wiki.ubuntu.com/Grub2](https://wiki.ubuntu.com/Grub2)
it says your file may be located in /etc/grub.d/grub.cfg ?

i think the same stuff applies from that point, you want to append that option on the first linux line

i'm thinking there's a more elegant way, especially considering grub version 2, it's likely worth your time to review that entire article, i don't have the time

---

### Post by praveenmarkandu on 2010-01-06
the problem with grub2 is, you dont have much control over it. you can edit the /etc/grub.d/grub.cfg files to put manual commands. but if you do a kernel update, ubuntu will run update-grub and that will wipe your manual entry in /etc/grub.d/grub.cfg  if im not mistaken. so you would have to do this everytime you updatee your kernel.

***edit***
my mistake, i think you can edit the /etc/grub.d/40_custom file

---

### Post by mmeija on 2010-01-06
> **praveenmarkandu said:**
> the problem with grub2 is, you dont have much control over it. you can edit the /etc/grub.d/grub.cfg files to put manual commands. but if you do a kernel update, ubuntu will run update-grub and that will wipe your manual entry in /etc/grub.d/grub.cfg  if im not mistaken. so you would have to do this everytime you updatee your kernel.

***edit***
my mistake, i think you can edit the /etc/grub.d/40_custom file


:) i was going to say, that problem is definitely the case for "grub1" which comes with 9.04, but i imagine some of the motivation for grub2 would be to solve that issue. also why the original poster should read the entire grub2 article as opposed to relying on us

---

### Post by mmeija on 2010-01-07
> **mmeija said:**
> :) i was going to say, that problem is definitely the case for "grub1" which comes with 9.04, but i imagine some of the motivation for grub2 would be to solve that issue. also why the original poster should read the entire grub2 article as opposed to relying on us

i had an issue today on a new machine with grub2 where i tried to hibernate, which may have worked, but the machine returned blank from thagt point forward. in the previous grub it would have been esc to get to the recovery menu, not so anymore, this post was useful and is likely an easier read than the one i posted earlier


[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

### Post by ROBER1S on 2010-01-14
I was having similar problems with my Dell Latitude E 6500 (Nvidia chipset).  Installing the backports-modules seems to have fixed it for me.

---

### Post by olafurg on 2010-01-15
Thanks for the replies! I'll try these out when I get home to the computer, @work currently.

---

### Post by bzzzzz on 2010-01-20
I have same problem (running linux mint8-which is based heavily on ubuntu 9.10)

I've got a work around.  It's not ideal but will suffice until its fixed properly. 

If you put your computer in suspend mode before you close the lid, then you can wake it up in the same way as normal. 

It seems that the button triggering suspend is not configured correctly.

---

### Post by vitoreiji on 2010-01-20
Hi, I have the same problem with karmic.
The nomodeset did not work for me, neither did the "suspended" workaround. I do not have the slow keys thing on.
Any other ideas?
Thx

PS: mouse works perfectly.

---

### Post by olafurg on 2010-01-21
I've tried installing linux-backports-modules and read the grub2 article. Still haven't found a fix. Other ideas or a general solution to the problem via updates would be very welcome.

---

### Post by SenorZ on 2010-02-19
Had a similar problem.  Karmic installed on a partition alongside Vista on a Thinkpad x61t.  When lid was closed the "half-moon" blinked rapidly.  Upon opening lip I saw my regular desktop but it was frozen.  This just started happening after an update.
Fix: 
Open Synaptic, File -> History, and look for last update.  Luckily I only had 3 (metacity, metacity-common, libmetacity0).  Did a "Force Version" on all of these to last version, and everything was OK after that.
Hope this helps.

---

### Post by bzzzzz on 2010-02-20
how do you do a force version?

---

### Post by praveenmarkandu on 2010-02-20
highlight the package in synaptic --> Package --> Force Version
or you can highlight the package and just Ctrl + E

just choose what version you want.

---

### Post by bzzzzz on 2010-02-24
Thanks for the tip.  As this fault has always been present on 9.10 I wasn't expecting it to work - and it didn't.

Back to the drawing board.

---

