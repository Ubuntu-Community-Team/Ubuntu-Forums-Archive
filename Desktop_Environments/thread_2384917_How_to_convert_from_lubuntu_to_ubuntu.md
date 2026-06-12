---
title: "How to convert from lubuntu to ubuntu"
date: 2018-02-14
forum: Desktop Environments
---

### Post by bhuvanteja98 on 2018-02-14
I purchased a new Lenovo ideapad 320 that shipped with free-dos. during installation I couldn't do the partition. I installed Lubuntu 17.10(Artful Aardvark) on it. I tried changing the DE to cinnamon which didnt work through lubuntu. so i installed ubuntu-desktop on it. it strucks abruptly for a minute or two. what should i do? can i convert totally into ubuntu without removing any data?

---

### Post by kc1di on 2018-02-14
Hello bhuvanteja98 and Welcome to Ubuntu,

The best way to experience ubuntu desktop would be to back up any important files and then download and do a fresh install of ubuntu on that machine. 
When ever you have multiple desktops on the same install - it will create problems. There will be some conflicts between the desktops.  My recommendation is to just do the fresh install of Ubuntu.
Good Luck.

---

### Post by bhuvanteja98 on 2018-02-15
Thank you kc1di.
can i reset lubuntu without any data loss?

---

### Post by flocculant on 2018-02-15
> **bhuvanteja98 said:**
> Thank you kc1di.
can i reset lubuntu without any data loss?

Yea of course - you reinstall and then use one of the backup copies of data you have in various places to replace the data.

But of course you don't have that, and are basing your hope on the data fairies wandering around that do all of that really important stuff for you so you've come here.

What you need to do is work out the difference between the 2 installations and then remove those packages. That's actually quite simple with kubuntu and ubuntu - remove kde-something and it's dependencies.

So assuming you don't have backups - I assume I'm close to that bone.

Do yourself a dual boot - install your new flavour.

Copy your really important data across to your new installation.

Check it is really there.

Back it up - to more than 1 source.

Now you can install gparted 

```
sudo apt install gparted
```

Remove the OLD installation's partition.

Boot with a live session - use gparted THERE to resize your new installation to use the space from the OLD installation.

Final point - this would have been magnitudes easier and less scary if you had backups of this apparently 'important' data.

---

### Post by mörgæs on 2018-02-17
An easy approach is to add the missing Ubuntu packages with the command ```
sudo apt install ubuntu-desktop
```

It will give you the option to select Lubuntu or Ubuntu at login time.

---

