---
title: "hard drive partitionioning"
date: 2009-03-30
forum: General Help
---

### Post by SpenceMakesSense on 2009-03-30
Before I go and screw this up. I want to make sure I dont do anything wrong. So I'll just give a description of my plans.

After screwing up with some previous hard drive partitioning my partitions managed to overlap. Making a 100gb partition unusable. So heres my plan. 

After asking the forums and getting some help but no one seemed to know what to do ([http://ubuntuforums.org/showthread.php?t=1103720](http://ubuntuforums.org/showthread.php?t=1103720)) so I decided to just redo everything. My only problem is that I want to save everything in my /home partition. So I figure I would take a portable hard drive and move everything in /home onto that. Then I would repartition everything and copy it back on. 

My hard drive is 400 gb. 200 gb would go towards my /home. 10 gb would go to /. And the rest would be formatted for windows xp. Then before booting into ubuntu after installing it I would copy my /home contents back in. 

Would this work or should I try a different route.

---

### Post by James_Lochhead on 2009-03-30
That is a good plan except:

You might want a 15-20 GB root partition just to be sure. I use well over 10 GB personally.

You might want a swap partition.

Make sure you delete all the hidden files (begin with a ., press ctrl h to see them) out of your home directory or your new configuration will be screwed up when you copy and paste back in.

---

### Post by aeiah on 2009-03-30
> **James_Lochhead said:**
> 
Make sure you delete all the hidden files (begin with a ., press ctrl h to see them) out of your home directory or your new configuration will be screwed up when you copy and paste back in.

dont delete all your hidden files, just overwrite them with the ones from your backup. that way, you wont delete ones that you havent got a replacement for.

note that your setting files are in home, but the software isnt. id first make sure your new system has the same software installed before moving over an old home partition.

---

### Post by SpenceMakesSense on 2009-03-30
Well I plan on copying over the new /home before even booting into a freshly installed ubuntu. So while on a live cd I would just delete /home/spence and replace it with the other /home/spence from the portable hard drive. Or will that not work?

and oh ya forgot about swap >.>

---

### Post by kestrel1 on 2009-03-30
I would definitely go with a minimum of 15gb for the '/' partition.
You may also be better off formatting your '/home' partition from the Live CD, then copy your files back in & when you install Ubuntu, get the installer to use that partition for '/home' but do not format it. Hope that makes sense.
Also if you are intending installing WinXP, do this before you install Ubuntu.

---

### Post by timcredible on 2009-03-30
> **james_lochhead said:**
> 
you might want a swap partition.

+1

---

### Post by Chemical Imbalance on 2009-03-30
You might want to read this first:

[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

---

