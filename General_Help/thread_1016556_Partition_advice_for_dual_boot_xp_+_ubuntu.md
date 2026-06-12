---
title: "Partition advice for dual boot xp + ubuntu"
date: 2008-12-20
forum: General Help
---

### Post by g3titan on 2008-12-20
Hi, I am new to ubuntu and would like to dual boot it with xp. After some research, I am planning on three partitions, one for xp, one for ubuntu root and one for /home and just making a swap file. 

The only issue I have is how big for each partition. This will be installed on my laptop which has 180gb of storage. For the /home folder, do all my installed programs go into that folder or do they go into the root folder. As of now I am considering, 120GB for xp, 40GB for /home and 20GB for root. I will be mainly doing programming on ubuntu while I will be using windows to play games and do 3D design work. I am open to all suggestions

Thanks in advance!

---

### Post by logos34 on 2008-12-20
I'd do 6-8GB for / (10gb max).  

downloaded .deb pkgs are stored in /var (specifically /var/cache/apt/archives -- you can clean it out periodically to free space).  Programs are installed in /usr, which is by far your biggest directory.  Some stuff will go in /opt (like third-party apps--picasa I think is one), others in /home (thunderbird, FF, googleearth, etc)

---

### Post by adult swim on 2008-12-20
i think whenever you install programs, they will go to the root folder but whatever you create in them and all of the setting files are saved to the home folder.  i dont think youd need that big of a partition for root.  when i set up my hard drive i used 25gb for root.  i just checked how much ive used and its only 4.5gb with quite a few programs on there.

---

### Post by cdtech on 2008-12-20
This is my setup which works out quite well
```
~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda7              58G   18G   40G  32% /
/dev/sda1             1.5G  430M  1.1G  30% /boot
/dev/sda6              64G   10G   52G  17% /home
/dev/sda3             107G   56G   52G  52% /media/Storage
```
My Drive is 250G (not much larger than yours). I'm using 107G for storage so you could even brake that up for your XP. I also use a much larger /boot for more kernel images. As you can see with the used percentage, with everything installed on my system, I'm still well under maxing out my partitions.

Hope this helps ya.......

**UPDATE::.**
Installed system programs will be installed within the "/" root partition.

---

### Post by g3titan on 2008-12-20
Thanks for the replay,

So the ubuntu installation itself only need 10gb, so i guess /usr i'll allocate 50gb or more for that then.

---

### Post by logos34 on 2008-12-20
yes, and my / is only 6.8 GB (87% full)

---

### Post by logos34 on 2008-12-20
> **g3titan said:**
>  so i guess /usr i'll allocate 50gb or more for that then.

No, that's included in /.  No more than 10 gb max necessary for  /, rest to /home,

---

### Post by logos34 on 2008-12-20
> **cdtech said:**
> 
/dev/sda7              58G   **18G**   40G  32% /


what all is on that?  you must have a ton of installed apps and leftover packages

---

### Post by cdtech on 2008-12-20
> **logos34 said:**
> I'd do 6-8GB for / (10gb max).  

downloaded .deb pkgs are stored in /var (specifically /var/cache/apt/archives -- you can clean it out periodically to free space).  Programs are installed in /usr, which is by far your biggest directory.  Some stuff will go in /opt (like third-party apps--picasa I think is one), others in /home (thunderbird, FF, googleearth, etc)

I don't understand the max? I'm above the max you suggested. If I would have used the 6-8 rule, I would have to reformat my drive. I'm also running a log rotate to help keep my logs cleaned up and if I didn't that would be more of an increase in space consumption. Drive space is cheap nowadays so why not use it.

---

### Post by cdtech on 2008-12-20
> **logos34 said:**
> what all is on that?  you must have a ton of installed apps and leftover packages

I run KDE and GNOME and yes a lot of apps. I also run a web server for designing web sites and VMware to run Windows apps. Once you start using Linux the options are endless. Plan for it I say........

---

### Post by logos34 on 2008-12-20
sure, if you have the space go for it...it's just that other people's / I've seen are considerably smaller...I've got a fair amount installed too (all the ubuntu-studio audio-visual stuff)...

---

