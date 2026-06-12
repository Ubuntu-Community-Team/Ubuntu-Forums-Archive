---
title: "How do i erase Windows"
date: 2009-05-04
forum: General Help
---

### Post by conrod on 2009-05-04
HI, 
 
I have a corrupt version of windows (that refuses to start) on my laptop, so decided to try Ubuntu.
 
I LIKE IT.
 
At the moment i am running Ubuntu from disc, but would like to install it completely. My only worry is that i am not sure how to do so bearing in mind that i have limited space on a laptop so want to make sure that it over writes windows rather than sits along side of it.
 
I hope that this makes sense, as i must sound like a complete novice to most of you.
 
PS. I am a complete novice.
 
Many thanks

---

### Post by dragonbeast25 on 2009-05-04
possibly you could format it from ubuntu live cd, look in start for lots of options. or maby when you install it you can install it on the formated partiton or installation will ask you to overite, try all but if you can format the C: or whatever do it then install it on partion.

---

### Post by lemcoe9 on 2009-05-04
When you are in the partition phase of the installer (shown below), you want to select "Guided - Use Entire Disk". That will delete ANYTHING that is on the hard drive you select.

[IMG]http://files.fosswire.com/2008/07/part.png[/IMG]

---

### Post by kryptikos on 2009-05-04
Welcome to Linux country! The forums and folks here you'll find are very friendly and ready to help. For you to get your feet wet it is best to follow this document [https://help.ubuntu.com/community/GraphicalInstall]("https://help.ubuntu.com/community/GraphicalInstall")

That is the walk through for a graphical installation. There is a section in there that you will see as you install that talks about partitioning. Simply click the checkbox that says **Guided: use entire disk**. That will remove your Windows partition. _**NOTE!!!**_ **Be sure this is what you want to do. Once you select that and Ubuntu begins to install it will wipe all information and you will LOSE all of your data that currently exists in your Windows partition. BE SURE you have copied any Windows data you want to keep to a USB stick or burn to disc before installing**.

If you run into trouble be sure to list as much information as possible. You'll find you will get more rapid responses with details rather than just saying "hey it broke". The forum is here to help you!

Again, welcome to Linux! You'll love it, just remember to give it time, explore the box and be ready to read, discuss...and never be afraid to ask any question no matter how small or noobish you might think it is. We all started as "noobs" at one point :)

Good luck! Hollar if you need help.....

---

### Post by utnubuuser on 2009-05-04
You can also keep your existing Ubuntu install, boot from the liveCD, and use Gparted (System>>Administration>>Partition editor), to remove the Windows partitions.
Windows partitions are NTSF etc, while Ubuntu uses ext3, ext2, etc. 

Sounds as though you might be better off doing a fresh install like lemcoe9 suggested, but I'd suggest doing "Manual", erasing all the partitions, than doing a 3 or 4gig / (root) partition, a swap that's 1.5 times the amount of ram in your machine, and the remainder of the disk as the /home partition.
(Remember that your Swap needs to be AT LEAST as much as your ram for the laptop to be able to hibernate).

---

### Post by lemcoe9 on 2009-05-04
> **utnubuuser said:**
> You can also keep your existing Ubuntu install, boot from the liveCD, and use Gparted (System>>Administration>>Partition editor), to remove the Windows partitions.
Windows partitions are NTSF etc, while Ubuntu ext3, ext2, etc. 

Sounds as though you might be better off doing a fresh install like lemcoe9 suggested, but I'd suggest doing "Manual", erasing all the partitions, than doing a 3 or 4gig / (root) partition, a swap that's 1.5 times the amount of ram in your machine, and the remainder of the disk as the /home partition.
(Remember that your Swap needs to be AT LEAST as much as your ram for the laptop to be able to hibernate).

The reason I didn't recommend doing manual, is because I was scared to death that I would mess something up using manual when I first installed Linux. hehe!

---

### Post by conrod on 2009-05-06
Many many thanks to you all, 

With all your help, i got it right first time. I am up and running, and pleased to find such a lot of help minded people all in one place.

Now the start of a long learning curve.

Cheers to all.

Conrod

---

### Post by Deamos on 2009-05-06
> **conrod said:**
> Many many thanks to you all, 

With all your help, i got it right first time. I am up and running, and pleased to find such a lot of help minded people all in one place.

Now the start of a long learning curve.

Cheers to all.

Conrod

Welcome to the last OS you will ever need!

---

