---
title: "Ubuntu Error"
date: 2009-04-22
forum: General Help
---

### Post by Danielinc on 2009-04-22
[B]Hi, I installed Ubuntu to my HDD the other day and put have a 250gb HD.

So I used 200 GB on Windows Vista and 50 on Ubuntu.  So when I tried reinstalling vista I tried to reformat the 50GB Partition but it gives me a error..  I want to put the 200 and 50  GBs back together..  Can anyone help me PLEASE? :(:confused:
[/B]

---

### Post by leonardo_neo on 2009-04-22
> **Danielinc said:**
> [B]Hi, I installed Ubuntu to my HDD the other day and put have a 250gb HD.

So I used 200 GB on Windows Vista and 50 on Ubuntu.  So when I tried reinstalling vista I tried to reformat the 50GB Partition but it gives me a error..  I want to put the 200 and 50  GBs back together..  Can anyone help me PLEASE? :(:confused:
[/B]

I am sorry, but I am not able to understand your situation properly? Do you want to say that you reinstalled vista in 200 Gb, and now you are not able to login to Ubuntu? What kind of error are you getting exactly??

---

### Post by lisati on 2009-04-22
Wouldn't it be easier to leave Vista on its own partition, delete the 50Gb partition, and then resize the Vista partition?

---

### Post by Ericyzfr1 on 2009-04-22
Why would you want to reinstall Vista?....Anyways....Try Gparted LiveCD to reformat your HD in whatever file system MS is using these days.

---

### Post by Megrimn on 2009-04-22
If you have no qualms about completely wiping the hard drive, here's what you can do:

1. Boot the ubuntu live CD

2. When you get to the desktop, navigate to System> Administration> Partition editor

3. From there you can wipe/resize the partitions to your liking.  Make sure none of the partitions are mounted.  The easiest way is to select the partition you want wiped and click "delete".  Don't forget to hit "Apply" when you are done.

You can use the partition editor to reformat as well.  NTFS is what windows vista is using.

---

### Post by Danielinc on 2009-04-22
> **Megrimn said:**
> If you have no qualms about completely wiping the hard drive, here's what you can do:

1. Boot the ubuntu live CD

2. When you get to the desktop, navigate to System> Administration> Partition editor

3. From there you can wipe/resize the partitions to your liking.  Make sure none of the partitions are mounted.  The easiest way is to select the partition you want wiped and click "delete".  Don't forget to hit "Apply" when you are done.

You can use the partition editor to reformat as well.  NTFS is what windows vista is using.

Im not seeing Partition editor in Administration:confused:..

EDIT:  I found the Partition Editor but how do I reformat from there?  there isnt any options for reformating..

---

### Post by Megrimn on 2009-04-23
> 
EDIT:  I found the Partition Editor but how do I reformat from there?  there isnt any options for reformating..

1. Once in the partition editor, 'delete' the two partitions so that they appear as one single partition.  

2. then select that single partition


3. now go to the menu Partition> Format to> ntfs

 [EDIT] what you need to do in the next dialogue is pretty obvious so I won't go into the details of it.  basically you decide how much of the HDD you want to format.  

4. the partition should now be a greenish color, meaning it's going to be formatted to the ntfs type of filesystem

5. hit "Apply"

6. watch as your HDD magically becomes whole once more...

I've had to do this several times myself, though not for the reason you are.  If you have any more questions, feel free to ask.  I will answer them to the best of my ability.

---

