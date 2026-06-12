---
title: "4 GB Mini 9 out of space"
date: 2009-05-12
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Ouzo66 on 2009-05-12
My computer has run out of disk space. I can account for about 350 MB (media files), but the rest are in file system files and I have no idea what to do about that. It took 2 months of web surfing to put 3.4 GB in those files. I have no experience with linux or ubuntu, so I don't know how to clean up files and prevent this from happening again. Any input would be greatly appreciated.

---

### Post by megamania on 2009-05-12
> **Ouzo66 said:**
> My computer has run out of disk space. I can account for about 350 MB (media files), but the rest are in file system files and I have no idea what to do about that. It took 2 months of web surfing to put 3.4 GB in those files. I have no experience with linux or ubuntu, so I don't know how to clean up files and prevent this from happening again. Any input would be greatly appreciated.
If it's cache saved by Firefox, try Tools -> Clear private data (or something like that) -> check the "cache" option -> ok.

---

### Post by Therion on 2009-05-12
Download, install and run QuickStart.  There's an option for "House Cleaning" that will remove a lot of junk from your PC's trunk.  

It's the best place I can think of to start.  Get it here (be SURE to follow all the install instructions):

[http://www.howtoforge.com/quickstart-the-swiss-army-knife-for-ubuntu-8.04-desktop](http://www.howtoforge.com/quickstart-the-swiss-army-knife-for-ubuntu-8.04-desktop) 

And yes it works on ALL versions of Ubuntu.

My Asus EEE has two differen SSD drives, does the Dell Mini use two different SSD's in as similar fashion?  If so maybe you can shuffle some data off the system "drive" where the OS is installed.  I keep Ubuntu and all it's packages on the 8GB SSD, and /Home on the 32GB SSD drive. 

Does your Mini have an additional slot where you can put an additional SD memory card for more storage?

---

### Post by Ouzo66 on 2009-05-12
Thanks for the ideas.  I'll give them both a try tonight.

---

### Post by abn91c on 2009-05-12
in a terminal sudo apt-get autoremove to clean out downloaded packages no longer needed

---

### Post by anjilslaire on 2009-05-12
> **Therion said:**
> My Asus EEE has two differen SSD drives, does the Dell Mini use two different SSD's in as similar fashion?  If so maybe you can shuffle some data off the system "drive" where the OS is installed.  I keep Ubuntu and all it's packages on the 8GB SSD, and /Home on the 32GB SSD drive. 

Does your Mini have an additional slot where you can put an additional SD memory card for more storage?

The Mini 9 has a single SSD, ranging from 4gig to 32gig depending on what's ordered. Mine shipped with  32gig, but it looks like that's not offered anymore.
Yes, here's an SD slot on the left side.

[QUOTE=abn91c]
in a terminal sudo apt-get autoremove to clean out downloaded packages no longer needed [/quote]
Actually, that will remove unneeded installed packages. To remove downloaded packages used for installs, it would be
```
sudo apt-get clean
```

---

### Post by ugm6hr on 2009-05-12
With the 4GB version, I'd suggest not downloading POP email, and using an SD card to save your own personal files to.  I use symlinks from my home directory to my SD card to make it easier.

Updates are probably the biggest contributor to your HD usage, with your Trashcan coming a close second.

To prevent the former causing future problems, use the setting in Synaptic Package Manager:
Settings -> Preferences
Files tab
Delete downloaded packages after installation

Or manually clear the packages each time with 
```
sudo apt-get clean
```

For Trash, just ensure you empty it from time to time.

---

### Post by shiningkenmonster on 2009-05-12
yeah, i would agree.

i usually do:

```
sudo apt-get autoremove
```
```
sudo apt-get autoclean
```
```
sudo apt-get clean
```

---

### Post by roob47 on 2009-05-16
):P Problem solved! Thanks to the above poster's i promise no more updating without sudo autoremove , sudo clean this is why ubuntu is so addictive it's a challenge to keep it running the way one like's it thanks again!:D

---

