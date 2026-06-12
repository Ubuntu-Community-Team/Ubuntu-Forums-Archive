---
title: "install dual boot kubuntu/xp"
date: 2005-06-14
forum: Desktop Environments
---

### Post by tuerten on 2005-06-14
Hi everyone,

  I'm an absolute Linux newbie (I only learnt what the command line was 5 days ago) and not overly familiar with system config stuff for XP.  I want to install a dual boot system but have not been able to find info on the forum or through google that is basic enough.  I really possess limited knowledge and need a step by step guide.  I tried messing around myself and just managed to ruin my windows install and partition.  If anyone could help me out that would be wonderful.  Thanks.

---

### Post by orev on 2005-06-14
When you say  "messed up", what do you mean?  Are you able to boot either OS?  Did you get the full install of Kubuntu (Ubuntu) completed?  Did you boot into either OS once since your original mess up?

I am new-ish, but might be able to help here.  I am running a dual boot AMD XP/Kubuntu box.

---

### Post by tuerten on 2005-06-14
I had xp installed and the disk partitioned into 4 parts, a switch first ( I think) then a blank partition (where I intended to install kubuntu) then XP, and finally someother partition that I have no idea about.  I ran the kubuntu live/install dvd and went to the standard install.  From there I had the option of deleting the whole hd or editing partitions.  I figured the edit partition option would allow me to choose where to install kubuntu.  I changed some options I shouldn't have.  Now none of it works and I'm running kubuntu live.  

I am very willing to start from scratch.  I have all the necessary disks and plenty of time.

---

### Post by Digitallysick on 2005-06-14
Here are some good things to check out, this is how i got mine up and running

First, make sure in your bios, that the hardisk is selected and it is not set to "auto" (grub kept giving me error 17 forever until i figured that out) if it already shows your hardrive, then great, 

I partitioned useing partition magic, i have a 200 gig hd, i used 50 gig of it for ubuntu, i partitioned 50 gigs to fat32. 

Set your cd rom for boot (most are by default) run the disk, when it asks for a partition, you should be able to select your fat 32 partiton (or fat partition) and install, i really didn't have trouble installing linux, getting the partitioning right was a little challanging , the grub part was extremely difficult for me to get correct, but if you follow the above (make sure the bios shows the harddrive) that will help alot.

---

### Post by tuerten on 2005-06-15
Thanks for your help guys but I couldn't figure it out.  I just dropped XP and installed Kubuntu instead.  I might try to fix it another time.  Thanks for your suggestions.   :-)

---

