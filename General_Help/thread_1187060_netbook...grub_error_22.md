---
title: "netbook...grub error 22"
date: 2009-06-14
forum: General Help
---

### Post by greenspeed on 2009-06-14
I've done a lot of reading on here about the liveCD installs and what not on fixing the grub error 22. However I used a sd flash card to do my install on my asus netbook, and here's basically what I can do.
 
I can f2 at my set up and change my boot to load off the sd card only. if i give it the option to boot of the HD i get the error and it stops working. When i tried to re-install ubuntu I can't get the partican to take over the old partician of ubuntu.
 
What cause the error i suspect was I turned off my comp while ubuntu was loading.
 
any help would be great. I wanna get to know how to use this os some more and I'm pissed that after a week it threw this error and I'm getting no where now

---

### Post by greenspeed on 2009-06-14
ttt

---

### Post by 3startuna on 2009-06-14
error 22 is a simple error to fix.

It happens when you delete a partition.

Linux is very specific about things like this. 

You deleted a partition and therefore GGrub doesnt know where the OS kernel is.

To fix it restart in live CD bring up terminal and reinstall grub from terminal. 

Their is a thread detailing this I will post links to it in a bit

---

### Post by greenspeed on 2009-06-14
Please click one of the Quick Reply icons in the posts above to activate Quick Reply.

---

### Post by greenspeed on 2009-06-14
Well I'm booting of my sd slot since I don't have a disk drive on the net book. 

Should I just choose the option to run ubuntu and not change any of my os settings option? That is the only one that will get me to the terminal. 

And the link would really help i'vr been stuck browsing on my BB and it's getting tedious.

---

### Post by greenspeed on 2009-06-14
This is the walk through I found and am trying to use. 

step 1.boot computer into the ubuntu live CD [try ubuntu without any changes]step 2."sudo"step 3."grub"step 4."find /boot/grub/stage1"step 5."root (hd0,UR)"final step 6. "setup (hd0,UR)"type EXIT

Step 4 keeps giving me a error 15 file not found. I even tried find /grub/stage1 and got the same thing I'm stumped.

---

### Post by greenspeed on 2009-06-14
And if it matters my system is an asus Eee 1000he

---

### Post by 3startuna on 2009-06-15
> **greenspeed said:**
> This is the walk through I found and am trying to use. 

step 1.boot computer into the ubuntu live CD [try ubuntu without any changes]step 2."sudo"step 3."grub"step 4."find /boot/grub/stage1"step 5."root (hd0,UR)"final step 6. "setup (hd0,UR)"type EXIT

Step 4 keeps giving me a error 15 file not found. I even tried find /grub/stage1 and got the same thing I'm stumped.


I had the same set of problems Grub is now installed on the wrong partition.

In the end I ended up fixing it by remaking the deleted partition. Then reinstalling grub using the method you specified.

Also not grub labels the partitions differently from Ubuntu.

so SDa1 might be called hd(0,0)

---

### Post by greenspeed on 2009-06-15
I just tried to re install using the Advanced feature and it keeps sayig I have no root system defined.

---

### Post by greenspeed on 2009-06-15
I will try the 00 config you mentioned I'm going guess I'll be out of luck

---

### Post by greenspeed on 2009-06-15
Root (hd0,0)
Setup (hd0)

Gives me error 17 cannot mount selected partition 

Find /root/grub/stage1 

Gives me error 15: file not found

---

### Post by greenspeed on 2009-06-15
Well I gave up. Idk what happened by no fixes I read worked too many files were not reconized and the only thing I can think is too many things were mixed up while I ran window for the first time ?

I'll just run virtual box for the program I need windows for.

---

### Post by 3startuna on 2009-06-15
This one is bigger than me

---

