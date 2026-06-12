---
title: "Remastersys - Is it for whole system of just a bare bones system?"
date: 2009-01-03
forum: General Help
---

### Post by sofasurfer on 2009-01-03
I took a quick stab at Remastersys last night and got a message indicating that my system was to large. I needed to exclude some directories.

So, am I to assume that Remastersys only creates a system image large enough to fill a CD and can it span multiple cd's or dvd's? I don't understand, if I need to exclude a large part of my system what is the point since I will have to copy large parts from a backup copy and then reconfigure?

My entire system is 25 gigs and if I exclude videos and music I can get it down to 12 gig. I think a Remastersys copy needs to be made from a system no larger than 4 gigs. Or maybe I am misunderstanding something. Can someone clarify something for me?

---

### Post by bryanl on 2009-01-03
remastersys will do either a system or complete backup. This is the "dist" versus "backup" command line options.

You can tell it to exclude certain folders. I usually add a list to the script.

The resulting ISO file needs to be small enough to fit on a DVD so you will need to exclude large data folders. Backup the data using, say, K3B and a data dvd project.

---

### Post by logos34 on 2009-01-03
> **bryanl said:**
> resulting ISO file needs to be small enough to fit on a DVD

just curious: can you use DVD DL (dual layer) ~8.8 GB?  (although even that would still be too small for OP)

---

### Post by logos34 on 2009-01-03
> **sofasurfer said:**
> 
My entire system is 25 gigs and if I exclude videos and music I can get it down to 12 gig. I think a Remastersys copy needs to be made from a system no larger than 4 gigs. Or maybe I am misunderstanding something. Can someone clarify something for me?

I wonder if you have a lot of deb pkgs taking up space?  

You could clear out /var/cache/apt/archives with:

sudo apt-get clean

---

### Post by sofasurfer on 2009-01-03
Heres my results when trying to reduce system size...
file system size (original) = 14.9 gig
after running 'clean' = 14.1 gig
after removing remastersys from /home/daryl folder = 6.5 gig
after removing videos from desktop = 4.1 gig

All of my personal files are on a seperate drive.
So what else should a person remove from their system?
My user directory shows 111.4 kb in size which I do not understand because the user directory has .mozilla-thunderbird in it and that alone is 14 mg in size. And I would not want to remove that anyway as it is contains data important to a restoration as far as I know.

And to everyone reading this, out of curiosity how big are you're basic systems (or do you refer to it as stripped down system) and how big are their complete systems?

---

### Post by shavedmonkey on 2009-01-29
> **sofasurfer said:**
> Heres my results when trying to reduce system size...
file system size (original) = 14.9 gig
after running 'clean' = 14.1 gig
after removing remastersys from /home/daryl folder = 6.5 gig
after removing videos from desktop = 4.1 gig

All of my personal files are on a seperate drive.
So what else should a person remove from their system?
My user directory shows 111.4 kb in size which I do not understand because the user directory has .mozilla-thunderbird in it and that alone is 14 mg in size. And I would not want to remove that anyway as it is contains data important to a restoration as far as I know.

And to everyone reading this, out of curiosity how big are you're basic systems (or do you refer to it as stripped down system) and how big are their complete systems?
The squashfs filesystem used on backups made by Remastersys uses compression, so a 4.1 gig ubuntu install should fit easily on a single layer disk.

---

### Post by cosine352 on 2009-02-09
> **bryanl said:**
> remastersys will do either a system or complete backup. This is the "dist" versus "backup" command line options.

You can tell it to exclude certain folders. I usually add a list to the script.

The resulting ISO file needs to be small enough to fit on a DVD so you will need to exclude large data folders. Backup the data using, say, K3B and a data dvd project.

How do you exclude some directory ? Please let me know.

---

### Post by steele64e on 2009-02-09
> **cosine352 said:**
> How do you exclude some directory ? Please let me know.

When you start up remaster look for "modify the remastersys config file..." click ok and then find "files to exclude" press ok again then just enter whatever you wanna exclude and you're done!:)

---

### Post by cosine352 on 2009-02-13
> **steele64e said:**
> When you start up remaster look for "modify the remastersys config file..." click ok and then find "files to exclude" press ok again then just enter whatever you wanna exclude and you're done!:)

thanks

---

