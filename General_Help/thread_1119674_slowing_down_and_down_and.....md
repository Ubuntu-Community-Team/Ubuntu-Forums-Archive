---
title: "slowing down and down and...."
date: 2009-04-08
forum: General Help
---

### Post by ravenhousepim on 2009-04-08
Hi, I'm using Ubuntu hardy heron. Since I have installed about a year ago ubuntu I have got numerous updates. In the beginning Ubuntu started real fast. Now it is slowing down and down and down...strange lines fill the screen.
Is there a tool to speed ubuntu up??? or a cleaning tool?? this is getting weirder by the day.
Every suggestion is welcome. Pim, Amsterdam.

---

### Post by hangfire on 2009-04-08
ravenhousepim,

What strange lines are filling the screen? Can you get a screen shot?

Check your partitions. If they are full (100%), Ubuntu will slow down. Please post the results of:

```
df -kT
```

-HF

---

### Post by HermanAB on 2009-04-08
Here are the common performance debug tools:
# top
# df

If the internet is slow, check the DNS in /etc/resolv.conf:
# cat /etc/resolv.conf
# dig @1.2.3.4 [www.yahoo.com](www.yahoo.com)

If a DNS is lame, find a new one, or move it to the bottom of the list.

---

### Post by ravenhousepim on 2009-04-09
> **hangfire said:**
> ravenhousepim,

What strange lines are filling the screen? Can you get a screen shot?

Check your partitions. If they are full (100%), Ubuntu will slow down. Please post the results of:

```
df -kT
```

-HF
Thanks. The lines are kind of DOS lines, running over the screen while the system is booting, saying what ubuntu apparently is doing. I didn't have those lines before.
The partition might be a problem, I used to have windows xp home ed. on the disk. Then I installed Ubuntu. I guess it made its own partition. So my question is: 1. how do I check that. 2. How do I enlarge it? RP.

---

### Post by ravenhousepim on 2009-04-09
> **HermanAB said:**
> Here are the common performance debug tools:
# top
# df

If the internet is slow, check the DNS in /etc/resolv.conf:
# cat /etc/resolv.conf
# dig @1.2.3.4 [www.yahoo.com](www.yahoo.com)

If a DNS is lame, find a new one, or move it to the bottom of the list.
Thanks for your reply. It is not the internet. It is booting the system that slows down. RP

---

### Post by DeMus on 2009-04-09
> **ravenhousepim said:**
> Thanks. The lines are kind of DOS lines, running over the screen while the system is booting, saying what ubuntu apparently is doing. I didn't have those lines before.
The partition might be a problem, I used to have windows xp home ed. on the disk. Then I installed Ubuntu. I guess it made its own partition. So my question is: 1. how do I check that. 2. How do I enlarge it? RP.

Pim, it looks to me something has changed in your boot up. 
In your /boot/grub/menu.lst file you find the different choices to boot from. One of them is obviously Ubuntu.

In the line that starts Ubuntu you can either have the word quiet, or you don't have it. When you don't see the word quiet in there you will see all the things Ubuntu does while booting you PC. With quiet you see nothing. Still the same things happen, no difference there.
What do you mean with: the partition might be a problem?
Ubuntu is installed in its own partition so there is no need to be afraid to use the command df -kT.

Succes met je computer.
Jan.

---

### Post by ravenhousepim on 2009-04-11
Hi Jan, Great reply. At least this is something I can handle. Found the file menu 1st. I spotted 4 Ubuntu versions: kernel 2.6.24-19/21/22/23.generic. Each version has a recovery mode. The recovery mode is without "quiet splash" instead it says: "single".
Remains the fact that the very first time I had installed ubuntu, the system booted remarkably fast. Now I have apparently reached kernel 2.6.24-23 one needs patience.
According to your suggestion,could it be that Ubuntu starts in recovery mode??

---

### Post by DeMus on 2009-04-11
> **ravenhousepim said:**
> Hi Jan, Great reply. At least this is something I can handle. Found the file menu 1st. I spotted 4 Ubuntu versions: kernel 2.6.24-19/21/22/23.generic. Each version has a recovery mode. The recovery mode is without "quiet splash" instead it says: "single".
Remains the fact that the very first time I had installed ubuntu, the system booted remarkably fast. Now I have apparently reached kernel 2.6.24-23 one needs patience.
According to your suggestion,could it be that Ubuntu starts in recovery mode??

Pim, in the menu.lst file, at the beginning, there is a parameter called default. Which value does it get?
This will probably be 0. So, the first item in the list, at the bottom of the file, will get started, This is normally not the recovery mode but the normal mode. Does it contain the word quiet?

Raar hè dat we in het Engels moeten schrijven.

Jan.

---

