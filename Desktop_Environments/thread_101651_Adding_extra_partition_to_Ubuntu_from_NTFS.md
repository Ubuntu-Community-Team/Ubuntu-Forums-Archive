---
title: "Adding extra partition to Ubuntu from NTFS"
date: 2005-12-10
forum: Desktop Environments
---

### Post by bathini on 2005-12-10
Hello friends

I partitioned my drive for Ubuntu (3 GB) and now my ubuntu is close to finish( 70MB drive left). I had a look at my windows ntfs partition and realized I have about 2 GB left. I want to steal 1 GB from NTFS and add it to Ubuntu. Now, Ubuntu constantly freezes especially when I am streaming TV from other sites and browser constantly disappears. I think this is due to not having swap. I did not configure swap when I installed Ubuntu breezy. Please help and thanks

Bathini

---

### Post by aysiu on 2005-12-10
I don't know much about partitions, but I've read many times that you cannot add to the beginning of a partition--only the end. Is the NTFS partition before or after the Ubuntu one?

---

### Post by bathini on 2005-12-10
First Windows XP was installed on my laptop, I then used partition magic to install linux. I guess ubuntu was installed last. Hope this helps

Bathini

---

### Post by earobinson on 2005-12-10
you should be able to do this with partition magic, or gparted, If i understand correct. But always back up before you try anything like this.

---

### Post by bathini on 2005-12-10
Hey

I just used partition magic and my windows no longer boots. I might have done something wrong. What is gparted? I tried typing this on the terminal but got wrong command error.

Cheers

---

### Post by Qrk on 2005-12-10
you have to install gparted first... 

```
sudo apt-get install gparted
```

Its  a graphical clone of partition magic for Linux.

---

### Post by bathini on 2005-12-10
Hello friends

Thanks for the info Ork, I managed to install gparted and viewed my partitions. My NTFS which is windows xp is now problems and can't boot from it. Is there a way to solve this. I should of not tried adding extra partition to Ubuntu. I have attached a file to show you the error message. 

Thanks

bathini

---

### Post by Qrk on 2005-12-10
Hmm. I don't know anything about windows anymore ( I never really did) Do you have your XP cd to repair your installation? That would be my best bet. 

If not, I'd use an unofficial Windows recovery tool, such as Bart's PE.  

[http://www.nu2.nu/pebuilder/](http://www.nu2.nu/pebuilder/)

---

