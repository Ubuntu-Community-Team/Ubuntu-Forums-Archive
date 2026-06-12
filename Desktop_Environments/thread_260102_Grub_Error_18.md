---
title: "Grub Error 18"
date: 2006-09-18
forum: Desktop Environments
---

### Post by TommyMann on 2006-09-18
I'm on my liveCD because I can't the OS up. I get Grub Error 18 when I start and anywhere I look for help it talks about older model PCs, but mine is hardly a year old. I use an external harddrive, so at first I thought it might have something to do with  that. I fixed it temporarily yesterday by changing the BIOS from DOS to OTHER, and I was overjoyed with my seeming wit... but alas, today it is back to the Grub Error 18 and the old switcheroo back to dos didn't work so I tried back to other and that didn't work, so now I have no solutions. Is there some code I can put into terminal from my live CD?

Everywhere I look online the lingua franca when dealing with Grub Errors is Greek to me, doesn't seem to be anything that I know how to do having only been linuxed for a month, refers to old computers, and says that new computers shouldn't have this problem.

Fairly depressing.

I don't want to have to start nightly back ups and do the windows reformat thing.

My laptop has has 512 ram a Pentium M and 60 gig hard drive with a single partition with Kubuntu on it.

With personal thanks,

Tommy

---

### Post by jd65pl on 2006-09-18
Try

```
sudo grub

root (hd1,0) (where it is your ubuntu partition)

setup (hd0) (where it is your disk containing MBR)

quit
```

If it doesn't work post back

J

---

### Post by TommyMann on 2006-09-18
I'm getting "selected disk does not exist"
I tried C:
and :/C
But I'm on live CD and it's saying my harddrive isn't mounted when I go to look at what it's titled. I'm not sure what the harddrive name is since I'm new to linux. It should be whatever linux defaults it at.

Thanks for your help.

-Tommy

---

### Post by jd65pl on 2006-09-18
Do you have a dual boot do you know which partition you installed linux to?

If you don't know try
```
fdisk -l
```
To work out which disk/ partition linux is on.

Print the result in the forum if you want further help.

Thanks

J

---

### Post by TommyMann on 2006-09-18
it didn't do anything

> ubuntu@ubuntu:~$ fdisk -l
ubuntu@ubuntu:~$ fdisk -l
ubuntu@ubuntu:~$

and here's what I got earlier


>     GNU GRUB  version 0.97  (640K lower / 3072K upper memory)

       [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]

grub>

grub> root (hd1,0) (/:C)

Error 21: Selected disk does not exist

grub>

grub> setup (hd0) (/:C)

Error 23: Error while parsing number

grub>

it makes me think that I can't edit my drive from the liveCD, but that's probably just inexperience talking. Or maybe I mislabeled the drive.

I only have one partition. The only OS on the computer is Kubuntu.

-Tommy

---

### Post by jd65pl on 2006-09-18
You have misunderstood or I haven't been clear!

Just type
```

sudo grub

root (hd1,0)
setup (hd0)

quit
```

---

### Post by jd65pl on 2006-09-18
Have a look at this follwo the instructions and see if it helps you

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")

Thanks

J

---

### Post by TommyMann on 2006-09-18
I definitely missunderstood

> 
    GNU GRUB  version 0.97  (640K lower / 3072K upper memory)

       [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]

grub>

grub> root (hd1,0)

Error 21: Selected disk does not exist

grub>

grub> setup (hd0)

Error 12: Invalid device requested

grub>


I'm at work so I haven't had time to look at the site yet, but I'll get to it asap.

Thanks again,
Tommy

---

### Post by Pjotr123 on 2006-09-18
Shouldn't it be: hd0,0 instead of hd0 ?

Greeting, Pjotr.

---

### Post by jd65pl on 2006-09-18
I think that would be referencing a specific partition on the disk instead of the MBR for the whole disk.

correct me if i'm wrong though i love to learn!

---

