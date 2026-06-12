---
title: "Accessing crashed OS via USB HDD"
date: 2006-07-05
forum: Desktop Environments
---

### Post by stalker145 on 2006-07-05
Greetings. I just had a HDD crash (yeah, it's the drive :mad: ) and I'm looking for some advice on accessing the data. I tried to plug the HDD into an external USB case and go through my server's OS (also Ubuntu 6.06) and was met with a folder that contained a "Lost & Found" sub-folder and icons for the remaining folders. I know I'm doing something wrong, I just don't know what. I'm in the process of installing to a new HDD, so my computer's fine, I just need to get to some work files so I don't have to start from scratch.

Any advice would be greatly welcomed. Thank you.

---

### Post by aysiu on 2006-07-05
Is this an internal or external hard drive?
Do you have access to a live CD?
What's wrong with "Lost & Found" and the remaining folders? Are you not able to access them or are there other folders you're looking for?

---

### Post by stalker145 on 2006-07-05
aysiu, the HDD is normally an internal, but I put it in an external case in the hopes that I could access the data.

The Lost & Found is the only item that is a folder; the rest are icons that should be folders. My data in in the home folder...

Yes, I have access to a Live CD. I am assuming since you asked the question that I should boot into that and try recovering that way. I'll give it a shot and reply with success or failure. I'm thinking it may fail since my original error was "Unable to find OS". This being a single-HDD setup, that led me to my conclusion of a bum drive. 

I'll reply within the hour.

---

### Post by aysiu on 2006-07-05
The way I would normally do this sort of thing is keep the internal hard drive internal, boot the live CD and mount the drive and then copy the important contents off the drive.

Once you have the live CD booted, use GParted or the *sudo fdisk -l* command to determine where your drive is located. I'll assume for this example that it's /dev/hda1.

```
sudo mkdir /recovery
sudo mount -t ext3 /dev/hda1 /recovery
gksudo nautilus
``` Then go to the /recovery directory.

---

### Post by stalker145 on 2006-07-05
Well, no joy on the live CD route. In fact, this HDD won't do anything now. I think it's done. Thanks for the help, anyway. I'll remember if anything like this happens again.

---

