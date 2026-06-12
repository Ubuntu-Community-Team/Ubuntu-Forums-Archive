---
title: "Ubuntu 9.04 Freezes during routine check at startup."
date: 2009-04-17
forum: General Help
---

### Post by clyde9999 on 2009-04-17
During startup, The computer attempts to do a routine integrity check and locks up (freezes). Computer must be shut off and restarted, then the check must be skipped in order for it to startup.

My computer is a Toshiba Satellite A75-S206 with 756 meg of ram.

Can anyone help me?

clyde9999

---

### Post by clyde9999 on 2009-04-18
The routine check of drives at bootup is locking my computer up!! Can anyone help me Please!!!!!

clyde9999:(

---

### Post by cariboo on 2009-04-18
It seems you may have a hardware problem, I would suggest that you boot from the LiveCD and manually run fsck on you Linux partition.

Once you are at the desktop open an Aplications-->Accessories-->Terminal and type:

```
sudo fsck -a /dev/sdx
```

where /dev/sdax is is your Linux partition.

If that doesn't work I would suggest you go to the hard drives manufuacturers web site and download the diagnostic tools, and run them on your hard drive.

BTW it is against forum policy to bump a thread until after 24 hours has elapsed.

Jim

---

### Post by clyde9999 on 2009-04-18
> **cariboo907 said:**
> 
BTW it is against forum policy to bump a thread until after 24 hours has elapsed.

Jim

I will re-read the forum policy's again. Thanks

clyde9999

---

### Post by clyde9999 on 2009-04-18
Thank you for the information Jim, I will do it right now.

---

### Post by clyde9999 on 2009-04-18
Okay Jim,

I did the check. The following was the result.

> ubuntu@ubuntu:~$ sudo fsck -a /dev/sda1
fsck 1.41.4 (27-Jan-2009)
/dev/sda1 has been mounted 35 times without being checked, check forced.
/dev/sda1: 198977/3538944 files (1.1% non-contiguous), 3126812/14137192 blocks
ubuntu@ubuntu:~$ 



I am not sure what it means, but it did complete its test

clyde9999

---

### Post by clyde9999 on 2009-05-14
It seems that I need to do this > sudo fsck -a /dev/sda1 every 30 starts. Here are the new results from the disk check:

> 
ubuntu@ubuntu:~$ sudo fsck -a /dev/sda1
fsck 1.41.4 (27-Jan-2009)
/dev/sda1 has been mounted 32 times without being checked, check forced.
/dev/sda1: 219098/3538944 files (1.3% non-contiguous), 5266455/14137192 blocks


If my HD is going south, I will just get a new one.

Jack

---

### Post by clyde9999 on 2009-05-27
I have replaced the Hard Drive, It finally gave up the ghost. This should solve the issue.

Jack

---

### Post by clyde9999 on 2009-05-29
I replaced my hard drive. after 20 boot-ups it went through a routine check, but locked up again, did not make it out of the first stage. I do not know what is happening. Hard drives are not cheap, and I am not wealthy by any means, and am very concerned that my hard drives are being destroyed. I ran Xubuntu from disk and checked my system. The results follow.

> ubuntu@ubuntu:~$ sudo fsck -a /dev/sda1
fsck 1.41.4 (27-Jan-2009)
/dev/sda1 has been mounted 21 times without being checked, check forced.
/dev/sda1: 172774/640848 files (0.4% non-contiguous), 928991/2560351 blocks
ubuntu@ubuntu:~$ 

Is there anyone out there that can help me?

Jack

---

### Post by clyde9999 on 2009-05-31
I have installed a different version of linux (puppy) onto this computer with the original hard drive to see what happens. So far, the OS and drive are working fine. I have scanned the hard drive with a disk utility, and no defects have been detected. I will take a couple of weeks to see how the hard drive reacts to the other OS and report here when I have results.

---

### Post by philferrar on 2009-06-17
I've had the same problem but when it occurs [after about 24 cold loads] I power off/on and during the re-boot select the 2nd load option on grub menu - this causes FSCK to run [no errors are ever reported] and when completed [after 20 - 30 seconds ?] it offers a 'continue with normal load' option which I take and everything seems o.k. Hope this helps.

---

### Post by clyde9999 on 2009-06-27
Okay, I have good news and bad news concerning this subject of Freezing during routine check at startup. It seems that my A75-S206 is a lemon, and yes it has way passed the deadline for replacement of any kind. I knew that it had problems, but did not realize the extent of its problems. Too bad, really fast machine. The resident ram is flawed and the only way to replace it is to replace the mother board. I guess that I will seek out a 3rd party motherboard for it since it has been with me so long. I hope it is cheap. In the mean time, It is a good computer to test out new distros and that is truly fun for me indeed. Thank you all who helped with this post.

Jack

---

