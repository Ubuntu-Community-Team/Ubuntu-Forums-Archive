---
title: "Help understand File system"
date: 2009-04-19
forum: General Help
---

### Post by rreyes1316 on 2009-04-19
I am a complete noob--about 6 days now. And I am seriuosly thinking I completely removing windows from my dual boot. That is just about how much I am starting to love Ubuntu.

OK. Here it is . . .I am confused about the sda's and ext's--remember, I am used to C:\ and alike. This is what I have done: I have a WD Raptor 150. I have done a complete install of windows on a partition I created of what came to be 48.83 GB titled by linux under GParted as /dev/sda1. The remaining disk space which I formated when I installed windows was with the intent to do a full install of ubuntu on the remainder . . .ok, simple enough.

When I installed Ubuntu 9.04 it gave me several options. The one I opted for was for it to use the largest disk space--this is what I wanted. Well . . .after about 6 days, I noticed that I only have 4.4gb in my home folder! This is when I searched the forums and found GParted. Not sure if I am reading this right but it looks like only 11.2 GB of the largest disk unused disk sapce was used to install ubuntu. So now I have the following: Windows on 48.83 GB (/dev/sda1 {File system ntsf}), new volume on 79.16 GB (/dev/sda5 {file system ntsf}), Ubuntu on 11.20 GB (/dev/sda6 {File system ext3}), and linux swap on 556.91GB.

How can I use all of sda5 or increase sd6? How should I have this formated? While on this subject, when I am ready to remove windows what do I do? And what file system should I use when I get a new external HD?

Thanks

---

### Post by codeseer on 2009-04-19
/dev/sda1 is Windows
/dev/sda5 is Evidently a new blank ntfs partition
/dev/sda6 is Ubuntu
Then you have the swap partition

If you didn't put anything on that new volume that is ntfs, then you can use GParted to just delete that.

It looks to me like you're missing /dev/sda2, /dev/sda3 and /dev/sda4 from the picture. Could you run 'blkid' from a terminal and post the output here?

My guess is that you went with the 'do my partitions for me' option when installing Ubuntu. If you did, you may not benefit by resizing the Ubuntu partition to consume the space now taken by the 'new volume - ntfs'. It would be worth a try to see if it gave you more /home space, but I think you might have to reinstall to get it working right. I think maybe, however, /dev/sda2-/dev/sda4 contains /home, so we need that 'blkid' output.

Edit, Additional Information:

I would probably suggest that when you're ready to remove windows, you wipe all of the partitions from the drive; remember to back up your data first to another drive. You generally want to stay away from that 'do my partitions for me' option when installing any Linux distro. Some people believe you should allocate a few GB to / (the root mount for the actual system), then allocate the majority of the rest to /home; this comes with the belief that if something goes bad wrong they can just reinstall to / and keep /home, which contains most of the configurations. Some people (myself included) just allocate all of it to /. Most usually agree that you should allocate an amount to a swap partition that is equal to the amount of RAM you have in your machine. I choose the 'all to /' option, but I have a 1000 GB drive; what I did is created a 500 GB partition for /, created my swap partition, then allocated the other 400 and some GBs to storage, though I'll change this when I reformat and make the entire 1000 GB drive storage and move Ubuntu to another drive.

Hope all that makes sense. :p

---

### Post by rreyes1316 on 2009-04-19
I was messing around with gparted and reformatted the 79GB space. Any how, this is what blkid yielded:

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="9070D4FF70D4ED4A" TYPE="ntfs" 
/dev/sda5: UUID="3E4CA1374CA0EABB" LABEL="New Volume" TYPE="ntfs" 
/dev/sda6: UUID="fc324b5f-2efc-489f-891c-6e744e2f76a9" TYPE="ext3" 
/dev/sda7: UUID="473ad690-342b-4931-9052-53273e819996" TYPE="swap"

---

### Post by codeseer on 2009-04-19
> **rreyes1316 said:**
> I was messing around with gparted and reformatted the 79GB space. Any how, this is what blkid yielded:

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="9070D4FF70D4ED4A" TYPE="ntfs" 
/dev/sda5: UUID="3E4CA1374CA0EABB" LABEL="New Volume" TYPE="ntfs" 
/dev/sda6: UUID="fc324b5f-2efc-489f-891c-6e744e2f76a9" TYPE="ext3" 
/dev/sda7: UUID="473ad690-342b-4931-9052-53273e819996" TYPE="swap"

Ok, I guess it's just the order you created/removed partitions in that made the naming odd. So, yeah.. you can delete the ntfs partition (/dev/sda5), then try to resize the Ubuntu partition by dragging it's corner backward toward the /dev/sda1 (windows) partition in GParted.

---

### Post by CatKiller on 2009-04-19
> **codeseer said:**
> It looks to me like you're missing /dev/sda2, /dev/sda3 and /dev/sda4 from the picture.

sda5 is the first partition inside an extended partition. This partition is always numbered 5, since there could be a maximum of four primary partitions, one of which would be the extended partition. Even if you've only got one primary partition, which is an extended partition, the first partition inside it would be numbered 5, in case you then subsequently created the remaining three primary partitions.

---

### Post by rreyes1316 on 2009-04-19
I was unable to delete ntfs partition (/dev/sda5). I had a window read:Unable to delete /dev/sda5! Please unmount any logical partitions having a number higher than 5. Not sure what this meant so I shrunk the partition tried to delete it and ran into the same problem. I tried to format it to an ext4 in order to delete it but this did not work. So now I have the following:

/dev/sda1 is Windows
/dev/sda5 is ext4 3.96gb
unallocated 75.2 GB
/dev/sda6 is Ubuntu
swap partition

I tried to resize the ubuntu partition but it would not move. Do I unmount it first?

---

### Post by codeseer on 2009-04-19
> **CatKiller said:**
> sda5 is the first partition inside an extended partition. This partition is always numbered 5, since there could be a maximum of four primary partitions, one of which would be the extended partition. Even if you've only got one primary partition, which is an extended partition, the first partition inside it would be numbered 5, in case you then subsequently created the remaining three primary partitions.

That makes perfect sense. I remember having fun with 32 primary partitions on [this]("http://www.ranish.com/part/").

---

### Post by CatKiller on 2009-04-19
I would agree with codeseer that when you completely remove Window, you might as well re-install Ubuntu over the whole drive. It's possible to just remove the Windows partitions and resize the remaining ones, but you'll need to update your GRUB entries to make them point to the right partition, and it isn't necessarily something that a new user would be comfortable with, especially if he wasn't that familiar with partitioning anyway.

Back up all of your data that you want to keep. There are also instructions on this forum and elsewhere for a means to create a list of all the packages that you've got installed, and then later to install all of the packages on that list in one go. That might be helpful to get you back up and running quickly if you've done a lot of customisation. Your settings are kept in your Home folder, so you'll probably want to back that up too.

You might also consider, when you re-install, having your /home on a separate partition. Again, there are instructions how to do this on this form and elsewhere.

---

### Post by codeseer on 2009-04-19
> **rreyes1316 said:**
> I was unable to delete ntfs partition (/dev/sda5). I had a window read:Unable to delete /dev/sda5! Please unmount any logical partitions having a number higher than 5. Not sure what this meant so I shrunk the partition tried to delete it and ran into the same problem. I tried to format it to an ext4 in order to delete it but this did not work. So now I have the following:

/dev/sda1 is Windows
/dev/sda5 is ext4 3.96gb
unallocated 75.2 GB
/dev/sda6 is Ubuntu
swap partition

I tried to resize the ubuntu partition but it would not move. Do I unmount it first?

This goes back to what we're talking about with the naming probably. You could boot up with an Ubuntu Live CD and unmount /dev/sda6 then delete /dev/sda5 and remount/resize the Ubuntu partition.

---

### Post by CatKiller on 2009-04-19
> **rreyes1316 said:**
> I tried to resize the ubuntu partition but it would not move. Do I unmount it first?

You can't change a partition that's mounted. Since you're running GParted from inside your Ubuntu install, that partition is necessarily mounted.

You'll need to run GParted from the Ubuntu cd, or GParted's own live cd if you want to change that partition.

---

### Post by codeseer on 2009-04-19
> **CatKiller said:**
> I would agree with codeseer that when you completely remove Window, you might as well re-install Ubuntu over the whole drive. It's possible to just remove the Windows partitions and resize the remaining ones, but you'll need to update your GRUB entries to make them point to the right partition, and it isn't necessarily something that a new user would be comfortable with, especially if he wasn't that familiar with partitioning anyway.

Back up all of your data that you want to keep. There are also instructions on this forum and elsewhere for a means to create a list of all the packages that you've got installed, and then later to install all of the packages on that list in one go. That might be helpful to get you back up and running quickly if you've done a lot of customisation. Your settings are kept in your Home folder, so you'll probably want to back that up too.

You might also consider, when you re-install, having your /home on a separate partition. Again, there are instructions how to do this on this form and elsewhere.

I made a post somewhere just the other day about how to make a list of installed packages.

Edit:

```
dpkg --get-selections | grep -v deinstall > installed-packages
```

---

### Post by rreyes1316 on 2009-04-19
Ooo! That sounds scary! But I am willing to try as long as I dont screw things up. Lets do it.

Do I reboot the system with the install cd in? Is there a recovery console on the ubuntu cd? I am ready. My hands are sweating.

---

### Post by codeseer on 2009-04-19
You put the installation CD in and reboot, then hit Enter to select English and Enter again to select the 'try without making changes' option. That will load the Live CD instance. I think you'll be able to just load the Live CD and then run GParted and delete the ntfs partition then resize the Ubuntu partition without having to do anything; I'm pretty sure the disks will be unmounted already.

---

### Post by rreyes1316 on 2009-04-19
rebooting

---

### Post by rreyes1316 on 2009-04-19
I am there. Do I unmount the ubuntu partition?

---

### Post by rreyes1316 on 2009-04-19
WAIT! I was able to resize without unmounting. But I am unable to delete the sda5 ex44 I created. What should I do with that?

---

### Post by codeseer on 2009-04-19
> **rreyes1316 said:**
> WAIT! I was able to resize without unmounting. But I am unable to delete the sda5 ex44 I created. What should I do with that?

Right-click on it and make sure you can't unmount it from the menu that comes up. If not, then I'd resize it down as small as I could, then resize the Ubuntu partition as big as I could and leave it like that until I reinstalled later.

---

### Post by rreyes1316 on 2009-04-19
No I can not.

---

### Post by codeseer on 2009-04-19
So, did the resize give you more /home room?

---

### Post by rreyes1316 on 2009-04-27
" . . .they can just reinstall to / and keep /home, which contains most of the configurations."

I am ready to reinstall everything. I have played and aquanted myself with everything including mess around with some configurations and install packages. How do i backup everything so that when I reinstall everything it will be as though I never left it?

---

