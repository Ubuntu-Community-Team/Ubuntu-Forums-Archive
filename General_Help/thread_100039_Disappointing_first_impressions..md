---
title: "Disappointing first impressions."
date: 2005-12-06
forum: General Help
---

### Post by bunty on 2005-12-06
Hi, 

first of all this is not just a moan, first impressions are very important, and with the choise and number of distros now to chose from decisions are made quickly.

My main system is Gentoo but I am looking for a distro that is more accessible to ordinary mortals that I can install for less technically competant friends. Ubuntu seemed to fit the bill.

I decided to get the 5.10 DVD ISO. It showed as being 2.0G both on the webpage and as the client started the download, so about 9h on my connection. Somewhere after about 6h it stalled. I was able to resume the download but was concerned it now showed as 2.9G! Looks like the file got "updated" ?  

Rather than start again I decided to press ahead and see if anything could be recovered. The md5 failed (no surprise) but I did manage to burn and boot to the live.

Second nasty surprise the dramatic music nearly blew out my speaker cones!! Best to make sure the sound system is correctly configured before throwing Watts at it if you dont mind.

I tried and installation but due to my faultly download it broke out during basic installation. Expected.

Eager to get something to install I went for a "dapper" CD install next.

All went pretty well (the text mode installed was fast and efficient) until I got  the grub setup. This seemed very inflexible and inapt to deal with my system that already had XP and SuSE. Fine , I'm a big boy , it said I could opt for manual installation. OK I have plenty of experience with grub, let's go...

Nothing! Good night Josephine , over and outm reboot. :confused: 

I was actually expecting it might tell me what I needed to manually add to my grub.conf not just shut down on me.

I now find myself spending a fair amount of time scouring google for posts and info about what I actually need in grub. I found a couple of things that dont even work so far , cool.

This is very poor. I presumably have a complete Ubuntu sitting on the system that I cant use.

What I saw on the live looked very good . Clean and compact for the little I tried to do with it but after all these false starts I am concluding that Ubuntu is still not really together enough to bother with.

OK , it's still young and looks promising . I'll come back in 6 - 12 months.

Keep up the good work.
:cool:

---

### Post by Joe_CoT on 2005-12-06
Breezy isn't *entirely* user-friendly; there's still some nagging problems that cause some extra tweaking to be necessary in certain cases, this being one of them. In Dapper Drake, it should be cleaned up a bit, but for now, it'll take some editing on your part.

in the console, use this command:
```
sudo gedit /boot/grub/menu.lst
```

this is the grub menu file. It's rather well documented, and even has examples on what entries look like. this is one of them:
```
# title         Windows 95/98/NT/2000
# root          (hd0,0)
# makeactive
# chainloader   +1

```

this is basically exactly what you need. If you put this at the bottom of the file (after removing the # signs, of course), that entry should work just fine. The only thing that needs changing is the drive and partition (the "(hd0,0)" part.

the drive and partitions numbers start at 0 and go from there. if the windows partition is on your first hard drive, the first number is 0. if it's also the first partition on the drive (you can check by running "sudo fdisk /dev/hda", and then pressing p to list the partitions), then the second number is 0, hence (hd0,0). if it's the second partition, it's (hd0,1). you get the idea i hope. Just save the file, reboot, and it should work fine.

---

### Post by kairu0 on 2005-12-06
First, we have MD5 sums for a reason. If an ISO fails the MD5 check then it's probably not a good idea to use it. After downloading such a large part of the file, it's not good news to anyone's ears, but you really should have started that download again.

I don't know if your speaker problem was related to the failed ISO installation, but I definitely wouldn't rule it out.

Second, it's probably not a good idea to evaluate a distro by using it's unstable, still-in-active-development version (dapper.)

Just the same, sad to hear that you got a bad impression and I hope you try an installation with a working, stable-version ISO again.

---

### Post by Joe_CoT on 2005-12-06
Oh, i didn't even notice that he was using **Dapper** instead of breezy. Breezy has the same problem with the grub configuration, but it's stable in most other respects. using dapper isn't a good idea for the time being.

---

### Post by RAOF on 2005-12-06
To get to your Ubuntu installation you'll want to add something like this to your menu.lst

```
title           Ubuntu, kernel 2.6.15-6-amd64-k8 Default 
root            (hd0,1)
kernel          /vmlinuz root=/dev/mapper/storage-dapper--root ro quiet splash
initrd          /initrd.img
savedefault
boot

```
Where you replace (hd0,1) with your /boot partition (in grub format), and /dev/mapper/storage-etc with your / partition (in linux format).

If you don't have a separate /boot partition, you'll want to replace /vmlinuz etc with /boot/vmlinuz etc

---

### Post by IanLowe on 2005-12-06
Is it really a fair complaint though?

A broken download with an MD5, okay - bad downloads happen to us all (to be honest, I'd suggest using the CD ISO of Breezy, then adding the extras from synaptic or using the automatix script rather than the chunky DVD ISO)

but to then jump onto Dapper? that's got warnings all over it that it's not ready for main desktop use - it's not due for release until April after all...

Why not try again, but use the Breezy CD ISO? It's very suitable for your non techy friends. :D

---

### Post by RAOF on 2005-12-06
It would indeed have been better to download the curent stable Breezy iso rather than the (frequently broken) Dapper install.  But his actual complaint (that he needs to manually edit the menu.lst) is valid for both Dapper & Breezy.

---

### Post by Curlydave on 2005-12-06
I don't see why one would expect Dapper to be stable.

Use Breezy.

---

### Post by tdaubs on 2005-12-06
I have been using Breezy for more than two weeks now.  I would call my experience with this distribution as 'surprisingly good'.  I have tried several distributions of Linux over the past 5 years.  Ubuntu is the closest operating system so far to make me very seriously question my dependance on Windows.  I am now using Ubuntu for about half the time I am on my computer.  I anticipate this will increase as I continue learning this excellent distribution.

---

### Post by apolyak on 2005-12-06
It looks that you used Firefox to download the dvd iso file. This is the Firefox problem. On Linux it shows incorrect file size - 2GB and stops when 2GB were downloaded. In Windows, at some point, it counts downloaded size and remaining time in negative numbers including milliseconds. This was known bug in Firefox 1.07 or 1.05. I installed Ubuntu from downloaded dvd iso on a few different computers without any problem. Initial sound settings are too high, but let's don't count this as a installation problem.

---

### Post by bunty on 2006-06-17
well I said I'd be back in 6-12 mths so I'm having another look and just got to see all your comments, thatnks for the replies.


It seems my point about the grub issue was a bit misunderstood.

There's no prob if I opt for "I know what I'm doing" style to have to edit grub.conf but I do need to know _exactly_ what to put in there. There's not way I can guess it.

My point was that I should not have to google for it or scour forums . I should get something on the screen I can note down before the system reboots. It would also be nice if I got a confirmation dlg before the damn thing just shut off. I may want to reconsider rather than start again.

Thanks for the suggestion of CD + synaptic , makes sense.

Sticking this idea on the download page may also lighten the load on your servers.

:cool:

---

