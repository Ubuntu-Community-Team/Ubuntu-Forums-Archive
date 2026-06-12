---
title: "Linux RAID Question"
date: 2009-02-18
forum: General Help
---

### Post by crokett on 2009-02-18
I got a machine I will use for my web/ssh/ftp/NAS and will put Ubuntu on it. I will go with SATA HDDs but need a controller. I am thinking of RAID. I can get an expensive RAID card or a cheap one that according to some reviews doesn't do RAID all that well. It occurred to me that I could get 2 cheap adapters and 2 drives, run SW RAID and still come out ahead on the pricer adapter. I would run straight RAID-1 mirror, no parity checking so not that much additional load on the CPU.

So my questions - I know with Windows mirroring if the boot drive fails, all I have to do is tweak the boot.ini file and boot from the second drive. One shop I worked in booted Windows from floppy for this reason. If something was really hosed up, you could take the working drive, put it in another machine running Windows and still get the data. Does Linux do the same thing? Could I boot, say, off USB and if the primary drive takes a dive just load the install that is  on the second one? Oh yeah, assuming I start with 1 HDD, can I add a 2nd and create the mirror without losing the data on the first one?  Looking at the RAID HOW-TO it doesn't appear that I can.

---

### Post by handy on 2009-02-19
I've asked a mod to move your post to the Server Platforms sub-forum.

The people that frequent that area are usually the ones most knowledgeable about RAID.

---

### Post by dmizer on 2009-02-19
> **crokett said:**
> I got a machine I will use for my web/ssh/ftp/NAS and will put Ubuntu on it. I will go with SATA HDDs but need a controller. I am thinking of RAID. I can get an expensive RAID card or a cheap one that according to some reviews doesn't do RAID all that well. It occurred to me that I could get 2 cheap adapters and 2 drives, run SW RAID and still come out ahead on the pricer adapter. I would run straight RAID-1 mirror, no parity checking so not that much additional load on the CPU.

So my questions - I know with Windows mirroring if the boot drive fails, all I have to do is tweak the boot.ini file and boot from the second drive. One shop I worked in booted Windows from floppy for this reason. If something was really hosed up, you could take the working drive, put it in another machine running Windows and still get the data. Does Linux do the same thing? Could I boot, say, off USB and if the primary drive takes a dive just load the install that is  on the second one? Oh yeah, assuming I start with 1 HDD, can I add a 2nd and create the mirror without losing the data on the first one?  Looking at the RAID HOW-TO it doesn't appear that I can.

If you absolutely must use RAID, fork out the big bucks and use a high quality raid controller. This will solve all the problems you are concerned with.

A simpler, cheaper, and low overhead solution would be to use rsync to create incremental backups to a backup drive. This way, you only backup the new stuff and you don't waste clock cycles writing to two drives every time you edit a text document.

This DOES mean that you will have some down time if you lose a drive, but downtime can be reduced to minutes if you are selective about what you backup. Most people don't need a full drive backup.

Don't get me wrong, I'm not suggesting that you don't need a full drive backup, but considering it takes less than 20 minutes to install Hardy from nothing, are you really gaining anything by backing up the whole drive?

Most special configurations can be restored by backing up your /home directory. You can also configure rsync to include backups of your critical configure files. Sure, it may take time to get rsync tuned for minimal downtime, but in a vast majority of cases users are better off relying on rsync over RAID.

I'm going to leave this here in general because this isn't really server specific, and it's good to have information like this in the general forum.

Thanks!

---

### Post by oiad on 2009-02-19
I run a software raid on multiple machines with no complaints.  They don't have much overhead and in the times I have moved them, all you need is mdadm installed on the machine and it can pull all of the array info off of any one of the good disks so it can be rebuilt, or whatever needs to be done.  

I know multiple people hosting web and mail servers off of mdadm raid 5's in gentoo with no problems on older hardware (amd 64's 3ghish couple gigs of ram) so unless you are expecting an unbelievable amount of traffic on the machine I would just go with software raid.

---

### Post by dmizer on 2009-02-19
Manipulating mdadm can be tricky and dangerous if you don't do things properly though. I do have a software RAID in operation, but if I lost a drive on it, I know it would take me a fair amount of time to recover simply because it's been so long since I've had to play with it.

On the other hand, dd and rsync are tools I use on a daily basis, and I can manipulate them more quickly and easily than I could restore a software array.

Here's a balanced and professional perspective on RAID: [http://www.pugetsystems.com/articles?&id=29](http://www.pugetsystems.com/articles?&id=29)

---

### Post by fjgaude on 2009-02-19
> **dmizer said:**
> Here's a balanced and professional perspective on RAID: [http://www.pugetsystems.com/articles?&id=29](http://www.pugetsystems.com/articles?&id=29)

I'm not so such this is balanced... I see a self-serving aspect to all the comments: the same company has to answer all the problems as they come up with raid setups...

There is no question that hardware raid has to cost at least $300 for the controller, or even $3000 for the best. And software raid using modern CPUs and fast memory is just as fast if not faster, but, and this is the big but, you have to know, learn what to do and when to do it. So few do any testing with **mdadm** before jumping in, and if someone else set up the raid we know what can and does happen when a drive failure occurs. I've been trying to answer questions associated with such for two years now on these forums.

Few understand the custom UUID setup under mdadam that has nothing to do with mounting, or naming a drive or array. I can go on-and-on and am usually happy to do so.

Software improves read speed and availability of data, period, if using raid5/6 and four-drive raid10. You gain speed with two to eight drive raid0, but boy: do backups often. <smile>

---

### Post by crokett on 2009-02-19
> **fjgaude said:**
> I'm not so such this is balanced... I see a self-serving aspect to all the comments: the same company has to answer all the problems as they come up with raid setups...

Few understand the custom UUID setup under mdadam that has nothing to do with mounting, or naming a drive or array. I can go on-and-on and am usually happy to do so.

Software improves read speed and availability of data, period, if using raid5/6 and four-drive raid10. You gain speed with two to eight drive raid0, but boy: do backups often. <smile>

I read that link too. For every person that called in with a RAID problem there are 5 or 10 that are running just fine with it.  His failure rates on drives are a bit sketchy, at least from my experience supporting customers running RAID. Also,  maybe it is bad luck but I've had 3 fail over the  last few years in my home systems. 


I am very familiar with RAID and what it can and can't do. As for not protecting against viruses, a)That is why I am installing Ubuntu instead of Windows ;) 

 Any argument that software RAID is slower than HW is more or less negated now by the speed of modern PCs.  SW RAID has a distinct advantage in that you don't need a special controller (and special drivers) to use it.   So what I am after is Linux on a RAID 1 array and a USB boot drive with a copy of the necessary config files to allow me to boot the 2nd drive if necessary.  I did some reading last night and it appears I can do this.

---

### Post by oiad on 2009-02-19
You don't need any config files on a flash drive really if you are doing raid 1 just need to make sure that the second drive is bootable and has grub on it.  Then in the time of the primary failing you can either just physically unhook it from the machine and it will boot off of the backup, or use mdadm to remove it.

This site has a quick way of making the second drive bootable.
[http://www.howtoforge.com/how-to-install-ubuntu8.04-with-software-raid1]("http://www.howtoforge.com/how-to-install-ubuntu8.04-with-software-raid1")

---

### Post by crokett on 2009-02-19
Thanks ojad, that looks like exactly what I want to do.

---

