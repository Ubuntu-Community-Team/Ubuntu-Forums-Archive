---
title: "seperate partitions for ubuntu?"
date: 2008-12-04
forum: General Help
---

### Post by Grolsche on 2008-12-04
Hi,

Being only a few days new here in to the world of ubuntu / linux etc. I saw a post somewhere about someone tellign somebody else that they had a partition for / and a partition for home so that when they update a new version of ubuntu you dont lose stuff you have saved in home.

My newbie question is, how do you do that? There wasn't any options when installing or was that a hidden option somewhere?

---

### Post by CatKiller on 2008-12-04
The standard tutorial is [here]("http://www.psychocats.net/ubuntu/separatehome").

If you **upgrade** to a newer version, it doesn't matter at all how your disk is partitioned. Instead, the advantage comes when you **re-install** over the top. You can just modify your / partition and leave your /home partition alone.

It's available in the installer, but it's not a simple option and so it's not mentioned in the simple setup. You have to make the respective partitions the sizes you want, and set the mount point of each, which makes it a distinctly manual operation.

---

### Post by philinux on 2008-12-04
> **Grolsche said:**
> Hi,

Being only a few days new here in to the world of ubuntu / linux etc. I saw a post somewhere about someone tellign somebody else that they had a partition for / and a partition for home so that when they update a new version of ubuntu you dont lose stuff you have saved in home.

My newbie question is, how do you do that? There wasn't any options when installing or was that a hidden option somewhere?

Catkiller is on the money with the link, for after an install.

If you've no data or can backup then reinstall and instead use the manual partitioning method. Then you can set up /, /home, and /swap partition yourself.

---

### Post by Grolsche on 2008-12-04
thanks catkiller. When I decide to follow the instructions,(which are being printed out for future ref) what size partitions do you recommend for / and /home

---

### Post by CatKiller on 2008-12-04
> **Grolsche said:**
> thanks catkiller. When I decide to follow the instructions,(which are being printed out for future ref) what size partitions do you recommend for / and /home

It depends entirely on how much space you've got and what you're going to use it for. You can get by with / as small as 4GiB, but usage of 10 or even 20 GiB is not uncommon, depending on which applications you've got installed. Similarly, your Home folder (which contains your personal data and settings) will need to be as large as the amount of stuff that you put in there. For example, I do some stuff with multi-track music files, which can get quite large, so I've got about 40GiB of music files and about 25GiB of generic data floating about. This is just working usage - when a project is finished it gets put on DVD. I've also got about 11GiB just in my ~/.wine folder from the pretend Windows install for running games in Wine.

Having a swap partition that is twice the amount of RAM that you have is the general rule of thumb. This works similarly to the page file in Windows, but is also where data from RAM gets put when you Hibernate your computer.

---

### Post by Grolsche on 2008-12-05
i have a 500gb drive :) 50gb going towards windows, until i can scrap it and use linux fully. So I shouldn't have any problem allocating enough space to last. I also use another drive for storing most work and really important files to.

Like you i do play games too :) Though I need to get a new graphics card that's got drivers that are compatible for linux before i can play them under linux.

---

### Post by louieb on 2008-12-05
> **Grolsche said:**
> ....I also use another drive for storing most work and really important files to....

:D Thats great - really the way to go. (separate data partition(s) I mean). 

I make my / (root) partition around 10GB. If I burned DVD's or worked with other large files  I would make it larger (20GB) to make sure /tmp has enough room to handle it. 

When you look in /home/<user name> press ctrl+h you will see a lot of files that start with a dot (.), these are hidden files that contain user preferences and program configuration files for that user. Most are small but really nice to keep around if you ever have to reinstall the rest of Ubuntu. I don't keep any data in my /home so I size it around 5GB.

Whatever space is left I use for the data partition and keep my photos music whatever else there.        

Can't say the size I use for / (root) and /home will work for you. But its worked well for me, so just throwing it out there.

---

### Post by stefangr1 on 2008-12-05
I never really understood why it is better to have /home on a different partition when you reinstall: won't your home folder will be filled with files from software that you have no longer installed?

I usually make one 100mb /boot partition (only because I use RAID), one 100mb /var partition, (this can prevent system failure when a problem caused your partition to be completely filled with log files), a 1Gb swap partition, a partition for / and one for data storage.

---

### Post by Grolsche on 2008-12-05
SO if I use another drive for data storage. Would this be a good set up.

/ - 50gb  /home rest of partition. Yes I   do have a 2gb swap partition. Wasn't sure on how big to make the swap so just threw 2gb  at it to make sure :)

would 50g to / be silly or is it good to have. I am fairly new to linux therefore still learning the proccesses of how it works, being a complete windows user, I do understand linux works differently to windows but i still have to learn the differences.

So feel free to say if the setup is completely a noob idea or not :)

---

### Post by 3rdalbum on 2008-12-05
50 gigabytes is a good size. Usually your programs and operating system will take up between 6-15 gigabytes, and you've got space left over for a network share and your /tmp (temporary files; I usually have at least one ripped DVD in there!)

---

### Post by hyper_ch on 2008-12-05
I don't run seperate partitions anymore on my home computer.

Rationale:

- you should have automatic regular backups anyway. So upgrading/reinstall is not an issue
- As I run the /home on the same disk I run swap and root (even if I used different partitions) there would be no performance gain

---

### Post by Grolsche on 2008-12-05
So  is 50gb allocated to / more than enough then to last me awhile?

---

### Post by CatKiller on 2008-12-05
> **Grolsche said:**
> So  is 50gb allocated to / more than enough then to last me awhile?

Oh yes. That'll be fine.

---

