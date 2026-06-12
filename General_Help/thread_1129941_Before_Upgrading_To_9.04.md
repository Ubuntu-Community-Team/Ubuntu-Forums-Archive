---
title: "Before Upgrading To 9.04"
date: 2009-04-19
forum: General Help
---

### Post by LiamWilson on 2009-04-19
Hey all,

Seeing as Jaunty is going to be here in a couple of days, I have just one question as to what to do:

Do I do a Re-install or a Network update?

The reason I'm asking this is mostly over the use of EXT4. I've heard that Jaunty is faster than 8.10 already, but are there any advantages over using a Fresh install with EXT4 over a network upgrade?

I'm fully aware of backing up my Data and that before doing a re-install, but what are the advantages of each?

Any help would be appreciated.

~LiamWilson

---

### Post by daniel014 on 2009-04-19
I'm planning to have a complete re-install for Jaunty on my laptop, but only because I have accidently ruined parts of the OS by trying to compile my own packages (still haven't worked that out!).

I would suggest that if your current system works well, then go with an upgrade. When I upgraded to the beta, it worked fine with the noticable speed difference. The only thing that might matter is if your internet/computer speed causes the upgrade to take a long time.

There is also the new computer janitor in Jaunty which fixes a system so that it is more like a fresh install which will help.

Hope that helps :).

---

### Post by LiamWilson on 2009-04-19
Oh, right ok. So will changing to EXT4 make any difference?

---

### Post by daniel014 on 2009-04-20
According to this page [http://izanbardprince.wordpress.com/2009/03/28/comparing-boot-performance-of-ext3-ext4-and-xfs-on-ubuntu-jaunty/]("http://izanbardprince.wordpress.com/2009/03/28/comparing-boot-performance-of-ext3-ext4-and-xfs-on-ubuntu-jaunty/"), Ext4 has better performance, and it also says > to get optimal performance you should cleanly format it, not “upgrade your Ext3 partition” 

So if you want the performance of Ext4, then a fresh install is recommended.

---

### Post by LiamWilson on 2009-04-20
Aah, right. I think I'll give it a go, to get the 'Full' experience

---

### Post by fballem on 2009-04-20
> **daniel014 said:**
> ... There is also the new computer janitor in Jaunty which fixes a system so that it is more like a fresh install which will help.

Hope that helps :).

Careful with Computer Janitor. It appears that it manages applications that are installed outside of Synaptic. For example, on my system, I have the fluendo plug-ins and a customised Nimbus theme installed. I'm not sure what the other items are, but I'm not uninstalling them.

I haven't looked to see exactly what Computer Janitor is intended to do, but I do know that I need both the fluendo and Nimbus items.

---

### Post by daniel014 on 2009-04-21
I think Computer Janitor is just like a graphical version of **apt-get autoremove** and **apt-get autoclean**.

---

### Post by fballem on 2009-04-21
> **daniel014 said:**
> I think Computer Janitor is just like a graphical version of **apt-get autoremove** and **apt-get autoclean**.

It seems to deal with packages that are installed but don't use the respositories. For example both fluendo and the nimbus themes are installed from .deb files. They show up in the Computer Janitor, but not the packages that I installed from the Repositories.

---

### Post by shawnrgr on 2009-04-30
The Janitor is most likely a front-end for deborphan, which i use often in synaptic to remove libraries that are no longer required by any packages install on your system, among other tips.. such as... i have a custom mount in fstab to /media/music. it wasn't using relatime, janitor picked it out and let me know. not to shabby.

P.S. it doesn't just look at packages installed that aren't in the repository, it looks at ALL packages installed on the system

---

