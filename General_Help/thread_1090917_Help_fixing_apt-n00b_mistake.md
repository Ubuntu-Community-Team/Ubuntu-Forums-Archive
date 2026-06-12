---
title: "Help fixing apt-n00b mistake?"
date: 2009-03-08
forum: General Help
---

### Post by CalderCoalson on 2009-03-08
Ok, before anything, let me apologize for my the stupid actions which have wasted countless hours of my time and will hopefully not waste too many of yours.

I tried installing terraform from source, and upon failing that, found that it was in the Debian repositories.  Without thinking, I added the Debian repository to my etc/apt/sources.list and apparently, (I have NO idea what I was thinking at the time), proceeded to install 581MB of upgrades.  The initial package, ironically, failed to install.  Instead of that, however, I was presented with a new "undocumented feature" when I next started my computer.  The keyboard and mouse would not work at the login screen, though they would work in tty1-6.  Upon switching to tty1, I noticed that the usual greeting, (Welcome to Ubuntu... or something like that), had been replaced by a single line declaration of doom preceding the login prompt:
```
Debian GNU/Linux 5.0
```

While I honestly have very little idea as to what's going on, my guess is that I replaced some crucial parts of my Ubuntu system with Debian files, and some major **** went down.  Once again, apologies for my stupidity, but I hope someone can help in the near future, as I have to go to school tomorrow and kinda need a computer...

Thanks a million in advance,
-Calder

---

### Post by tommcd on 2009-03-08
> **CalderCoalson said:**
> 
While I honestly have very little idea as to what's going on, my guess is that I replaced some crucial parts of my Ubuntu system with Debian files, and some major **** went down.  


What commands did you run after you added the Debian repo to your sources.list? If you ran **sudo apt-get update** then installed some packages, then you likely installed a crap load of Debian packages as dependencies, which quite likely borked you system. What Debian repos did you add?

Can you boot to recovery mode? If so then boot to recovery mode, put your sources.list back the way it was before you added the Debian repo, and without any 3rd party repos you may have added, then run:
```
sudo apt-get update
sudo apt-get dist-upgrade
```
and keep your fingers crossed. In the future, don't mix Debian and Ubuntu repos.

---

### Post by CalderCoalson on 2009-03-08
Crud, neither that nor the finger-crossing worked.  When I run dist-upgrade I get 0 to remove and 0 not upgraded.  I think I just ran sudo apt-get install terraform and then sudo apt-get -f install...

---

### Post by tommcd on 2009-03-08
Well, it may be worth it try one more time. It seems odd that APT would report no upgrades. Did you run "sudo apt-get update" after fixing your sources.list?
Try booting to recovery mode again. Make sure your sources.list only has official Intrepid sources. Then run:
```

sudo apt-get update
sudo dpkg --configure -a
sudo apt-get install -f
sudo apt-get dist-upgrade

```
I'm not sure what else you could try. Unless someone else has some better ideas, I think you may be looking at a reinstall.

---

### Post by CalderCoalson on 2009-03-10
Thanks for trying, but unfortunately it didn't help.  I just ended up reinstalling Ubuntu on a new partition and leaving the old one to grab my files off of when I need them.

---

### Post by tommcd on 2009-03-11
> **CalderCoalson said:**
>  I just ended up reinstalling Ubuntu on a new partition and leaving the old one to grab my files off of when I need them.

If you now have Ubuntu on a different partition you can use the old partition as a separate home. Follow this guide:
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)
This way if you ever need to reinstall Ubuntu again all your data is safe on a separate partition. I always do a clean install when a new version of Ubuntu comes out. I have my data on a separate partition so a reinstall is quick and easy.

If you need to resize any partitions first use a Gparted or Parted Magic live CD. Backup any important files first.

---

### Post by CalderCoalson on 2009-03-12
Thanks Tom!  The data partition / OS partition sounds like an interesting idea, I'll consider it.  For the time being, I just copied all the necessary files back over, which gave me the opportunity to do a little Spring cleaning.

Thanks again for the help, support, and patience,
-Calder

---

