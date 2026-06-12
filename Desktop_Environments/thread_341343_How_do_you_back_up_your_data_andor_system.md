---
title: "How do you back up your data and/or system"
date: 2007-01-18
forum: Desktop Environments
---

### Post by Handssolow on 2007-01-18
Two general questions that I'm requesting answers. How might I do these-

Hard drives don't last for ever. Let's say, I boot up my PC and I get an error message to say my hard drive has failed. I hope my response will be, "shucks, but I've got a back-up of all my personal data and system settings on a DVD that I made earlier, I'll get a new hard drive, install Ubuntu and use my DVD to re-install all my data and settings". How do I do this?

Scenario 2, I've decided to upgrade my PC with a new mobo, processor and memory -perhaps even to 64 bit. I've got a DVD with all my personal files and wireless settings. How do I make the back-ups and restore the data on the new machine?

---

### Post by drr422 on 2007-01-18
Senario 1:  I assume that you have all of your data and music and stuff already backed up on dvd's or an external hard drive, and that when you created your partitioning scheme, you have your documents and music stuff stored on a seperate partition than / (root). 

 What I would do then is to fire up partimage from a livecd, as explained [here]("http://www.psychocats.net/ubuntu/partimage") to backup your root partition. 

 When you install your new hard drive, you can use partimage again to restore that partition to the new hard drive.  You would then most likely have to restore your grub using [this procedure]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows") and then you should be able to boot, where you'll then have to create your 'music and documents' partition with gparted, and then set the mount points with fstab, or if you like graphical solutions, apt-get install pysdm.

  And then you should be back to normal.  There is another approach as well,  that just throws everything into a big archive using tar explained [here]("http://ubuntuforums.org/showthread.php?t=81311&highlight=howto+back+up+restore") With partimage you don't have to create a partition that has the exact same size, you just have to create it so that its big enough for all of the data.

Senario 2:  I'm not too sure about this approach, i know all of your settings are stored in your /home directory, but that would only cover preferences and config files, it wouldn't cover the actual programs.  So you would have to install the different programs again, which shouldn't be too hard. 

One approach you could take, assumming your / and /home are on the same partition, would be to do a fresh install and then mount the partition your /home would be on, and manually copy and paste your /home/ directory from your dvd drive to the new /home/, But using this approach might give you some permission errors, so you might need to 
sudo chgrp user_name /mountpoint/home/user_name/
sudo chown user_name /mountpoint/home/user_name/
and then you could reboot and log in, and would have your personal preferences for each of your programs intact.  

At least thats the approach that I would take.

---

### Post by dabl on 2007-01-18
Here's what a really lazy, but slightly paranoid guy like me does:

(1) First, organize your data in your /home directory in some simple fashion.  I use "Documents", "Pictures", and "Music".  Under each of those top 3 folders can be a whole file structure to suit you.

(2) Spend $95 on a second hard drive, make a Linux partition partition on it, and create a mirror set of folders to the ones in your /home directory.

(3) Frequently (like after you have been working on your stuff), use your favorite copying technique and simply copy everything in /home/Documents to hda2/Documents (or whatever), and so on for each of your top data folders.  I takes me maybe 15 minutes to back up 30G of data this way, although I rarely hang around to watch the clock.

(4) Spend a couple hundred bucks on a decent UPS.

I call this "data security".  I also make a set of DVDs about every 90 or 120 days.

My justification:
1. Parts are cheap, time is precious.
2. BOTH hard drives are unlikely to crash simultaneously, given the UPS.

---

### Post by Handssolow on 2007-01-18
Thanks folks for the help and advice.

---

