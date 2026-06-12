---
title: "Error Code 15"
date: 2009-05-19
forum: General Help
---

### Post by rps1106 on 2009-05-19
Hi - Can anyone help?
 
Several weeks ago I updated Ubuntu 8.1 with 9.04. All seemed to go well. About a week ago I stated up the laptop and it would not boot, it jusy came up with No Operating System. After trying to boot 6 times it booted OK. The following day exactly the same thing again. Two days ago it wouldn't boot and even after 20 times the problem was the same.
 
I decided to reinstall from the CD. It installed but when it came to boot up I got Error Code 15. I can boot from the CD but not from the hard drive. I am unable to find anything on the hard drive at all.
 
Any ideas?? Please accept my apologies if I do not reply immediately. I am at work using my work PC and anything you suggest Itry will have to wait until I get home tonight and the answer to your questions will have to wait until I'm back at work the next day! Sorry for this.
 
Robin

---

### Post by VMC on 2009-05-19
> **rps1106 said:**
> Hi - Can anyone help?
 
Several weeks ago I updated Ubuntu 8.1 with 9.04....After trying to boot 6 times it booted OK. ...
 
I decided to reinstall from the CD. It installed but when it came to boot up I got Error Code 15. I can boot from the CD but not from the hard drive. I am unable to find anything on the hard drive at all.
 
...
I'm not sure how you got it to boot trying 6 times?! Usually if you get error 15, it won't boot ever.

When you say you can boot from CD you mean that you can boot the CD disk, correct? Not that you can boot the hard drive using the CD? Which CD disk are you using - Ubuntu 8.10 or 9.04?

Are you using Ext4? If so, that's most likely your problem. 

Boot back up using the CD and type the following and then post the output:

```
sudo fdisk -l
```

---

### Post by rps1106 on 2009-05-19
> **VMC said:**
> I'm not sure how you got it to boot trying 6 times?! Usually if you get error 15, it won't boot ever.
 
When you say you can boot from CD you mean that you can boot the CD disk, correct? Not that you can boot the hard drive using the CD? Which CD disk are you using - Ubuntu 8.10 or 9.04?
 
Are you using Ext4? If so, that's most likely your problem. 
 
Boot back up using the CD and type the following and then post the output:
 
```
sudo fdisk -l
```
 
Hi I'm quite new to Linux so please excuse my ignorance. What is Ext4?
 
When I say boot 6 times I mean turning the PC off then on again.
 
Yes you are right, I can boot the CD disk. I have tried both versions.
 
When I get home tonight I will use the Terminal and put in the command as suggested. I'll get back to you as soon as I can.
 
Thanks for your help
 
Robin

---

### Post by rps1106 on 2009-05-19
> **rps1106 said:**
> Hi I'm quite new to Linux so please excuse my ignorance. What is Ext4?
 
When I say boot 6 times I mean turning the PC off then on again.
 
Yes you are right, I can boot the CD disk. I have tried both versions.
 
When I get home tonight I will use the Terminal and put in the command as suggested. I'll get back to you as soon as I can.
 
Thanks for your help
 
Robin

OK home now. I assume the command is Sudo fdisk -l as 1 is an invalid option

Then the output is

Device Boot Start  End  Blocks     ID  System
 /dev/sda1     1    4679 37584036 83   Linux
 /dev/sda2 4680   4864 1486012+ 2 Extended
 /dev/sda5 4680   4864 1485981  82 Linux Swap /Solaris

Hope this helps.

Robin

---

