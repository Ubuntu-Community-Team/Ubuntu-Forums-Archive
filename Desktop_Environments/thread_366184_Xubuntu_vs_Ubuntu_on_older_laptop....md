---
title: "Xubuntu vs Ubuntu on older laptop..."
date: 2007-02-20
forum: Desktop Environments
---

### Post by d.j.schroeder on 2007-02-20
I have an old laptop, specs are:  P3 650 MHz, 256 MB RAM, 10 GB hard drive, Netgear WG511T vs wireless card.  I use it only for surfing the web, sending emails and stuff like that.  I installed Puppy Linux on it quite a while ago but I have liked Ubuntu on some other machines so I thought I'd give it a try.  I got sort of a strange result I thought so I thought I'd post it here and see what you all think.

Because it's old and a little slow I thought I'd try Xubuntu first.  It installed and ran ok.  I got wireless working etc.  But, I didn't really like the Xfce environment and it hung up occasionally.  Also the bar at the top and bottom where the menu is dissappeared after a few boot up's and never came back.  So I was a little irritated and decided to try Ubuntu 6.06 (Xubuntu was 6.06 too).

It took a while to install it, and once I got wireless working it took even longer to apply the updates than it took to install.  Now that all that's done though, it runs faster than Xubuntu did.  Also it hasn't had any hang up problems at all since the install.  So after all that ramble my question is, why is Ubuntu running better/faster than Xubuntu?  I thought Xubuntu was specifically for older machines so that they would run a bit quicker.  Actually, I think it runs better with Ubuntu than it did with Puppy, which is also supposed to be lightweight and fast.  I'm happy with Ubuntu on it so I probably won't go back to either Xubuntu or Puppy, but I am curious why it worked out this way.

---

### Post by madmetal on 2007-02-20
well your pc has enough ram and not so old cpu to run ubuntu with gnome.
i preffer DamnSmallLinux from PuppyLinux though..
well if you remove some unwanted services and set up your ubuntu machine right it can run great!!

---

### Post by d.j.schroeder on 2007-02-20
Is there a good utility for removing some of the unwanted things?  Some things I've noticed are "configuring RAID" blah blah at boot.  I think LVM and some other stuff could go too.

---

### Post by madmetal on 2007-02-20
> **d.j.schroeder said:**
> Is there a good utility for removing some of the unwanted things?  Some things I've noticed are "configuring RAID" blah blah at boot.  I think LVM and some other stuff could go too.

a nice start ..
[http://ubuntuforums.org/showthread.php?t=89491](http://ubuntuforums.org/showthread.php?t=89491)

that really improved my system..
also try to run sudo apt-get autoclean 
and install deborphan to look for orphaned deb files..

---

### Post by d.j.schroeder on 2007-02-20
Sweet, lots of stuff I can get rid of.  Should make this old thing usable for a while longer.

---

### Post by madmetal on 2007-02-20
well they will improve it...
you can also try to find applications that need less ram or cpu..
eg. opera instead of firefox i think.. or abiword instead of openoffice..
a reason i love linux.. too many options !

---

### Post by madmetal on 2007-02-20
the article i am reffering to..
[http://polishlinux.org/choose/linux-on-old-hardware/](http://polishlinux.org/choose/linux-on-old-hardware/)
i hope it helps more!

---

### Post by Rui Pais on 2007-02-20
just a note.
the fact that there are Ubuntu versions of gnome, kde and xfce4, that didn't the choice of desktop  exclusive of the version you install. 
If your actual installation is good you can install too any other desktop environment and play with it, seeing which one you like and which one is faster. 

In my opinion this days xfce and gnome are more or less the same in terms of speed (with gnome offering more configurations and options) and maybe thats why your works well.

Try a look at windowmaker, [fluxbox]("http://ubuntuforums.org/showthread.php?t=320104") and e17. They are lighter and faster. The first can be installed with apt-get and for [e17 you must set repos]("http://ubuntuforums.org/showthread.php?t=319336") on your sources.list

---

