---
title: "Need help installing Ubuntu 9.04 netbook remix"
date: 2009-05-04
forum: Dell Ubuntu Support (CLOSED)
---

### Post by shiningkenmonster on 2009-05-04
I have a dell mini 9. I just ditched the Dell's factory preintslled Ubuntu on the mini 9.

After updating my bios to AO5. I've just installed the dell's iso of the Ubuntu 9.04. From this website:
 [http://linux.dell.com/wiki/index.php/Ubuntu_9.04]("http://linux.dell.com/wiki/index.php/Ubuntu_9.04")
it works great, it has all the codes/drivers/many extra languages. but it leaves me 1.4GB of free space. I have the 8 GB SSD model. (its acutally 7.15Gb of harddrive space.) Having 1.4GB of free space is not a lot. I was expecting the install would only take up 4GB.

I am downloading the official Ubuntu 9.04 netbook remix. I am going to upload it to a usb flash drive and install it.

but i have never understand the configurating the partition part. i never got the /home /root partition jargon or whatever separates it.

Can someone tell me what numbers I should put on partition my on 8GB harddrive? I just want it to work as 'there as.'

---

### Post by anjilslaire on 2009-05-05
With an 8gig SSD, I would not recommend separating /home, just do an install of the Netbook Remix and allow it to use the whole drive as a single partition.

Separating /home from /root will only create unused space in /root that could best be used by /home, considering the limited amount of space you have.

I have a 32gig SSD, and have 6 gigs on /, and ~24gigs on /home/

On an 8gig, don't bother separating them, IMO

---

### Post by shiningkenmonster on 2009-05-07
hey, i did a "/" on the single partition, the whole harddrive running ext4.

is that okay? I wasn't sure if i was suppose to pick /home, /root or just / (I don't even know what they all mean)

what does "/" mean anyways? and the /root and /home ?

---

### Post by anjilslaire on 2009-05-07
Yes, thats perfect.
"/" is the base of th file system, like C:\ in Windows. Everything builds off of that. Your home directory is /home/shiningkenmonster, where your files and personal settings are stored.

Many people like to set /home as a separate partition, so when they reinstall the OS, or install a new version, they can format "/" and leave /home untouched, thus leaving all of their fles & preferences untouched from install to install. 
However, on a 4gig drive, you don't really have enough room for that.

Also, after you finish updating, run
```

sudo apt-get clean

```
This will clean (erase) all of the setup files used to install the system updates so as to keep free up as much space as possible.

---

### Post by madomac on 2009-05-07
Have a look at [this blog]("http://www.ubuntumini.com/") for more information on setting up Jaunty on the Mini 9. Helped me a lot.

Cheers,
Marc

---

### Post by shiningkenmonster on 2009-05-14
when i partition my hardrive to "/" is the base of the file system.

I am just curious. when i upgrade my OS from the via manger update. using this as an example....Does it automaticly save my settings? will it erase everything and do the install of Ubuntu 9.10?

---

### Post by ugm6hr on 2009-05-14
Upgrades preserve everything.

Just make sure you have the HD space for the 700MB download.

I am planning to copy /home to USB drive and then just install over 9.04; restoring /home post-installation should work.  This is what I did going from the Dell 8.04 to 9.04NBR.

---

