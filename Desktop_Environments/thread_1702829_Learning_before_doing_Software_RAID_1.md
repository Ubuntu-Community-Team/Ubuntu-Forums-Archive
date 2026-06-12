---
title: "Learning before doing Software RAID 1"
date: 2011-03-08
forum: Desktop Environments
---

### Post by wanderingarticfox on 2011-03-08
Please, I know this is a long thread starter but I really could use some help and advice from someone that knows more about Ubuntu than I do.
I know someone out there can help me with this, please help me learn.

I do find it curious that I get responses in other forums but here at Ubuntu no one seems willing to help a newbie learn. Oh I have been using Ubuntu since the spring of 2009 but I am still a newbie and trying to learn from those that know more than I do.

I am going to build a new system in May and want to set it up with software RAID 1 using 2 WD 1TB blacks. I have found tons of pages and links to others via Ubuntu Community Documentation. I do have a few questions that I could use some help with clarification. I know I will be using 11.04, 64-bit Alt. Install ISO/CD. 

On the Community Doc. page: [https://help.ubuntu.com/community/Installation/SoftwareRAID?action=fullsearch&context=180&value=Convert+to+software+raid&titlesearch=Titles](https://help.ubuntu.com/community/Installation/SoftwareRAID?action=fullsearch&context=180&value=Convert+to+software+raid&titlesearch=Titles)
 it states under the partitioning Disk: Quote>  "Partitioning the disk

Warning: the /boot filesystem cannot use any softRAID level other than 1 with the stock Ubuntu bootloader. If you want to use some other RAID level for most things, you'll need to create separate partitions and make a RAID1 device for /boot." 

My first question is that because I plan to use RAID 1 only do I need to partition the disk or will the installation allow/create a boot section on both drives and then automatically set both drives up, format and install at the same time?

My second question is will GRUB automatically install onto both Disk?

Finally; would there be any advantage to installing LVM onto this type of array; remember that I do not plan to create partitions I want both drives mirrored and will be using the entire drive as one single partition.

I have the HowTO: Linux Software RAID using mdadm from the tutorials  and tips section of this Forum printed out. That is just to let anyone responding to this thread know I've already got it in hand but links to other information are welcome. Then again if someone would like to just list the steps that will be great.

---

### Post by itmas on 2011-04-18
I see you still havent gotten an answer yet.

I am in the process of doing exactly what you described. I am using the alternate CD and plan to just create the whole partition on both drives as LVM RAID and then create a raid from that. 

See what happens :) I will reply back here tomorrow with results and any extra points I discover as I go. 

I am using 11.04 b2

---

### Post by itmas on 2011-04-18
Ok. Finished it.

Follow the steps in[ how to setup Raid 1 on Ubuntu]("https://help.ubuntu.com/community/Installation/SoftwareRAID?action=fullsearch&context=180&value=Convert+to+software+raid&titlesearch=Titles") including Configuring the Raid but don't click finished. There are a couple more steps to complete.

[IMG]http://www.itmas.com.au/ubuntu_raid/pre-config.png[/IMG]

Select the first raid drive you created and press Enter

[IMG]http://www.itmas.com.au/ubuntu_raid/config_raid1.png[/IMG]

Highlight use as and press Enter

[IMG]http://www.itmas.com.au/ubuntu_raid/config_raid2.png[/IMG]

Select EXT4 as type, press Enter. Select Format the partition so it changes to yes. 

If this is your main partition, ensure it is set to / then select Done setting up.

Highlight the second partition
[IMG]http://www.itmas.com.au/ubuntu_raid/config_raid3.png[/IMG]

and set Use as to swap area. You won't need to format this one.

Select Done setting up and return to the main partition menu

[IMG]http://www.itmas.com.au/ubuntu_raid/post_raid_config.png[/IMG]

If your screen now looks like mine, congrats.

Select Finish partitioning and write changes and follow the bouncing ball to complete installation.

remember - Virtual Box is your friend. Always test these things in VBox first and you won't have as many issues.

---

