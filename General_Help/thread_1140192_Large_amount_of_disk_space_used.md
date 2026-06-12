---
title: "Large amount of disk space used??"
date: 2009-04-27
forum: General Help
---

### Post by snorbens on 2009-04-27
Hi,
I am hoping that someone can advise me please,I am using Jaunty.

According to GParted the size of my sda1 is 217.49GiB and of that 32.82GiB used. That in itself seems a large amount.

When I go to places and computer open filesystem properties it shows contents of only 5.3GB.

Has anyone got a clue of what might be going on? or am I missing something.

---

### Post by DeMus on 2009-04-27
> **snorbens said:**
> Hi,
I am hoping that someone can advise me please,I am using Jaunty.

According to GParted the size of my sda1 is 217.49GiB and of that 32.82GiB used. That in itself seems a large amount.

When I go to places and computer open filesystem properties it shows contents of only 5.3GB.

Has anyone got a clue of what might be going on? or am I missing something.

How about hidden files? You can show them in Nautilus by pressing ctrl-h.
Try that and see again.

---

### Post by snorbens on 2009-04-27
> **DeMus said:**
> How about hidden files? You can show them in Nautilus by pressing ctrl-h.
Try that and see again.

No, still shows only 5.3GB so do not know what is going on. As I say over 32GiB showing in partition seems rather large considering I only use this laptop for the internet? and a few small programs.

---

### Post by bacardiandwatermelon on 2009-04-27
Have you tried Disk Usage Analyser?

---

### Post by snorbens on 2009-04-28
> **bacardiandwatermelon said:**
> Have you tried Disk Usage Analyser?

Hi,
Just done that. Analyser shows 29.4Gb but the scan of the filesystem shows nowhere near that figure.

A quick guestimate of the figures of the scan shows approx 8Gb used on the files.

Still at a loss.

---

### Post by stef4001 on 2009-04-28
[http://ubuntuforums.org/showthread.php?t=215177](http://ubuntuforums.org/showthread.php?t=215177)

---

### Post by snorbens on 2009-04-28
> **stef4001 said:**
> [http://ubuntuforums.org/showthread.php?t=215177](http://ubuntuforums.org/showthread.php?t=215177)

Thanks for that...........It is not the Total GB size of the Drive that I am querying, but that somehow on sda1,the filesystem has used a Total of 32.82Gb,if  you understand what I mean?

What GParted shows is:/dev/sda  (232.88GiB)

/dev/sda1 ext3      size: 217.49GiB    Used:32.82GiB   Unused:184.66GiB
                                                               
/dev/sda3 ext2            10.01GiB          1.74GiB            8.27GiB

/dev/sda2 extended          5.39GiB

/dev/sda5 linux swap        5.39GiB
 
It is the used 32.82 GiB on sda1 that I cannot understand. I just use this laptop for Internet and only have a few programs on the system, none of which I think constitutes that amount of usage.

The only thing that comes to mind is that I tried to do a full backup using compression using tar.bz2 to my sda3 partition which failed.

I looked for any residual folder in case it somehow took some space but cannot see anything.
Thanks

---

### Post by ddrichardson on 2009-04-28
Is there a fragment of this in /tmp?

---

### Post by freonchill on 2009-04-28
whats "df" show?

---

### Post by snorbens on 2009-04-28
> **ddrichardson said:**
> Is there a fragment of this in /tmp?

Nothing there either?

Thanks

---

### Post by snorbens on 2009-04-28
> **freonchill said:**
> whats "df" show?

Here it is....Just to mention that I am a complete and utter newbie at this who gets my bus pass next year.:confused:

mervyn@mervyn-laptop:~$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda1            224472336  30838456 182231348  15% /
tmpfs                   964364         0    964364   0% /lib/init/rw
varrun                  964364       104    964260   1% /var/run
varlock                 964364         0    964364   0% /var/lock
udev                    964364       152    964212   1% /dev
tmpfs                   964364        76    964288   1% /dev/shm
lrm                     964364      2392    961972   1% /lib/modules/2.6.28-11-generic/volatile
mervyn@mervyn-laptop:~$ 
Thanks

---

