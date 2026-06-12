---
title: "Dual booting question"
date: 2011-04-15
forum: Desktop Environments
---

### Post by dctrsatan on 2011-04-15
Does installing both M$ Windows 7 along side Ubuntu cause performance loss?  Also is there a special way the HDD should be defragmented?

Thanks, Greg

---

### Post by Kirboosy on 2011-04-15
Hi Greg,

I would recommend before installing Ubuntu that you run disk cleanup and defragmentor from Windows. Make sure its tidy and neat before you add Ubuntu.

Ubuntu and Windows are totally separates from each other. You shouldn't see any performance loss. The only "loss" you will have is space on your Windows partition.

> **dctrsatan said:**
> Also is there a special way the HDD should be defragmented?

I believe you mean partitioned. :) I would leave that till you are booted into the Ubuntu LiveCD. 

A simple way to install Ubuntu (which does affect Windows because Windows sees it as a program) is call [WUBI]("http://www.ubuntu.com/desktop/get-ubuntu/windows-installer") I would recommend this method if you aren't sure if you want to commit to Ubuntu just yet. 

A "harder" way is to partition the drive. Generally its good practice to have a generous amount of space given to Ubuntu when you install it. (not because it needs tons and tons but that way you have plenty of space to store everything after you fall in love with Ubuntu ;) ) Its a pain to resize partitions once everything is setup.

I've seen people say that Ubuntu installer if its selected to "Install Alongside other Operating Systems" eats the Windows drive. I've never had this problem and I've installed Ubuntu multiple times on many types of computers. Its really your call.

Remember with a hard drive you can only have 4 primary partitions or 3 primary and 1 extended. If you could tell me how your hard drive is partitioned at the moment I would be able to help you more. :)


~Caboose

---

### Post by dctrsatan on 2011-04-15
Thank you, I currently do not have a partition made as the hard drive is blank.  It is a 1TB hard drive and from my understanding I should install M$ Windows 7 on it first, lets say half of the hard drive partitioned for that and the other for Ubuntu.

---

### Post by Kirboosy on 2011-04-15
Oh no. Windows can use its standard defrag tool. Linux doesn't have or really need one. (so much simpler than I originally thought. :) )


Well you install Windows and creat a 500 GB partition and then let the Ubuntu install use the other 500 partition. You will need  two partitions for Ubuntu. Storage and Swap. SWAP is basically virtual RAM (simple explanation) and is generally 2x the size of your physical RAM. So with the Ubuntu installer you would click "Specify Partitions manually" and create a 8 GB Swap space (if you had 4 GB of RAM) and the rest would be a ext4 mounted at "/" partition.


~Caboose

---

### Post by dctrsatan on 2011-04-15
Does Ubuntu write data to the drive differently than the M$ os's?

---

### Post by Kirboosy on 2011-04-15
Ok this is getting confusing...see my post above. I saw your edit and changed mine...


Yes Ubuntu uses a different partition format than Windows. Ubuntu will be able to see your files in Windows but Windows can not read ext4 (without special tools)


~Caboose

---

### Post by dctrsatan on 2011-04-15
Alright, I understand now thank you very much!  My system is very high end and I can not wait to get it up and running tonight!

---

### Post by Kirboosy on 2011-04-15
Ok Awesome. Let me know how it goes. Any problems don't hesitate to post about them. :)

~Caboose

---

### Post by scott-ian on 2011-04-15
There are many ways to do a dual boot.  I might try wubi, since it is very easy to damage to boot up of existing operating systems.  And the dreaded words, "It is a good to be sure you backup your hard drive before messing with such things."

---

### Post by dctrsatan on 2011-04-15
Alright thank you all very much, I will look into this program you both mentioned.

---

### Post by dctrsatan on 2011-04-17
As soon as I turned on the computer I loaded the M$ Windows  7 disc and allocated 2 partitions each  500gb.  Now that I have windows installed I have 3 partions: M$ Windows  7 500gb, 100mb M$ Windows  7 loader, and the unformatted 500gb space for Ubuntu.  

Thank you, Greg

Edit: I found instructions online.  For anyone else reading this post direct your browser here: [https://help.ubuntu.com/8.04/switching/installing-partitioning.html](https://help.ubuntu.com/8.04/switching/installing-partitioning.html)

---

