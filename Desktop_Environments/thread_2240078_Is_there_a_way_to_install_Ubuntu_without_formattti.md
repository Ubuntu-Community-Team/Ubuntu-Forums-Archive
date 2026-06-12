---
title: "Is there a way to install Ubuntu without formattting the drive?"
date: 2014-08-17
forum: Desktop Environments
---

### Post by xeddog on 2014-08-17
I currently have three computers running linux, two are Ubuntu and one is Mint 16.  I would like to switch the Mint machine to Ubuntu just so they will all be the same.  But I don't want to have to go through all the bovine excrement of backing up databases and data, formatting the hard drive, re-installing and configuring/customizing the software again, importing databases and data, and all that.  I just want to replace Mint with Ubuntu.   From what I have found out so far, it doesn't look like this is doable.  Is there a way?

Thanks,

Wayne

---

### Post by egeezer on 2014-08-17
What about using Clonezilla on one of your Ubuntu boxes and just reproducing it on your Mint machine?  You might have to wipe the Mint drive, but it would be easier than rebuilding your Ubuntus piece by piece.

---

### Post by xeddog on 2014-08-17
I don't think that would help much.  It would probably take me longer to get the software, learn how to use it, and then actually do it than to just install Ubuntu.  But the applications, databases and data are unique to the Mint machine.  The databases and data can be backed up and restored, but I would still have to do all the work of removing all of the canned applications I don't want and installing the ones that I do want (I would probably have to do that anyway, but . . .), and then installing/configuring/customizing the applications I want running daily.  It certainly isn't a gargantuan task by any means, just a pita.   

Thanks,

Wayne

---

### Post by grahammechanical on 2014-08-17
I have all my data on its own partition. I often install different versions of Ubuntu to test them. I never format my Data partition but I always format the partition I am installing to. I never lose my data and I can access the data from all the installations.

---

### Post by xeddog on 2014-08-18
I have my main machine set up that way, but the machine in question is a backup with only a single drive and single partition (not counting swap).  At least it WAS a backup.  It was initially set up just to do some testing of a few applications, but after the testing I decided to just leave it there.  But even at that, the data isn't the biggie, its the applications.  They would all have to be redone and that is the biggest pita, and the biggest reason I was hoping against hope that there was an easy way to just replace Mint with Ubuntu.    But it looks like if I want to do this I will just have to bite the bullet and spend a couple of days getting it all set up again.

Wayne

---

### Post by 3rdalbum on 2014-08-18
> **xeddog said:**
> I have my main machine set up that way, but the machine in question is a backup with only a single drive and single partition (not counting swap).  At least it WAS a backup.  It was initially set up just to do some testing of a few applications, but after the testing I decided to just leave it there.  But even at that, the data isn't the biggie, its the applications.  They would all have to be redone and that is the biggest pita, and the biggest reason I was hoping against hope that there was an easy way to just replace Mint with Ubuntu.    But it looks like if I want to do this I will just have to bite the bullet and spend a couple of days getting it all set up again.

Wayne

Install Ubuntu using the "Something Else" partitioning method. Don't elect to format any partitions, just click your / partition and choose Edit Partition, then set the mount point to /

Continue with the installation. There's a long, confusing question that the installer asks, and it kind of sounds like your data will be deleted. Click Continue. Yes, trust me on this.

The contents of /home will be saved, and your current software selection will be noted and then installed again after Ubuntu has been installed. That is, if it's in the repositories.

So basically, you'll end off with the same repository software as before, your user data will be saved, your per-user settings will be saved. You will lose the base Linux Mint system (of course) and any files stored outside /home. You'll lose configuration files from /etc, if you need them you should back them up before the installation.

---

### Post by xeddog on 2014-08-18
3rdalbum  - that sounds a lot more like what I was looking for.  That will take care of most of the stuff, but that still leaves the two major applications and a couple of utilities that are not in the repos (ppa's).  Still sounds a LOT better than having to do it all.  I think I'll do a fresh backup and give it a try.

Thanks,

Wayne

Edit:  Just a follow-up question if I may.  Will all of the Mint system files still be there?  I assume they will be.

---

### Post by oldfred on 2014-08-18
I have never done it, some more info on 3rdalbum's suggestion.

 Over install without formatting to reuse same home data. "Dirty Install"
System settings or anything in / may be overwritten with defaults. Good backups still important
[https://help.ubuntu.com/community/UbuntuReinstallation](https://help.ubuntu.com/community/UbuntuReinstallation)
[http://ubuntuforums.org/showthread.php?t=1941872](http://ubuntuforums.org/showthread.php?t=1941872)

I do not know if that will work going from Mint to Ubuntu as many settings are different.
I would backup everything, and export a list of installed applications to make reinstall easy if required.

      
 from lovinglinux - use dpkg to list installed apps
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)
[http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/](http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/)
From old install
dpkg --get-selections > ~/my-packages
From New install
sudo dpkg --set-selections < my-packages
sudo apt-get -y update
sudo apt-get dselect-upgrade

Again some packages in Mint may not be in Ubuntu.

---

### Post by 3rdalbum on 2014-08-19
Your Mint system files will be removed. My understanding is that everything outside /home is deleted.

---

### Post by Tadaen_Sylvermane on 2014-08-19
This all may be pointless. Just install unity from the repos and leave it as mint. Mint is technically Ubuntu to begin with so seems much ado about nothing. They use the same repos and software. Just change the DE and copy your /home/$USER/.insertconfignamehere to the Mint /home/$USER

Assuming it is the gui you are reinstalling for that is kind of useless with linux of any variety. The DE is fully changeable and swappable, or you can have 5 of them installed at the same time. Unlike windows you have a choice and it doesn't require a full format & reinstall just to change the interface.

---

### Post by 3rdalbum on 2014-08-20
> **Tadaen_Sylvermane said:**
> This all may be pointless. Just install unity from the repos and leave it as mint.

Easier said than done, I'm afraid. I tried to install Unity on Mint and it just wouldn't appear at the login screen.

I don't know whether it's just a bug or if the Mint developers have broken it out of spite. I tried to get help from the Mint community but they were less than helpful; it seems the only reason they were using Mint is because it didn't come with Unity.

This was back in the 13.04 days so it's possible things have changed since.

---

### Post by xeddog on 2014-08-20
Well, I talked myself into not being a cry baby about all of this so I backed up everything I needed to backup and just did an install of Ubuntu 14.04.1 using the installation option to replace Mint.  That left me with a relatively "clean" Ubuntu installation, but of course all the applications and other stuff was gone.  With good backups, though, the machine was running again in about 4 or 5 hours.  But to address a few of the comments made - 

I thought about just installing Unity itself, but I did a little reading on the Internet and as 3rdalbum mentioned, it doesn't seem like it is as easy as installing a few packages and the resultant Unity is still missing a few features.   It probably would have been "good enough" though.  As for re-installing using the "something else" option, in hindsight I should have done that if for no other reason than to do it and learn something new.  Now if it comes up again I won't have any experience to draw on and it might be a much more important machine.  Shoulda, coulda . . . But since the applications that I am mainly interested in are installed into my home directory, it was easy to back them up too, and then just copy them back to the "new" Ubuntu.  As for the data, all I can say is CRAP!  I had two backup copies of my mysql database, and neither of them would restore.  Fortunately this was just for me and not a production system so while I hate losing it, it is small potatoes.  If I really wanted to I could take the time to re-create it (probably a few weeks) but it really isn't worth all them time to do so.

At any rate, if a situation like this comes up again (if??? or when!!!) I will remember this.


Thanks to all,

Wayne

---

