---
title: "How to clone ubuntu 7.10 to computers with same hardware"
date: 2008-01-23
forum: Desktop Environments
---

### Post by hazardgreen on 2008-01-23
Hi there,

I want to clone my ubuntu install to 10+ PCs with the same hardware environment. 
I've already found out that GRUB uses a special code for identifying the root partition ( "root (*dev_code*)" in boot menu ), and when i changed the code where the root partiton is (hd0,1) ("root (hd0,1) there was an error while booing up:

"
    Check root= bootarg cat /proc/cmdline
    or missing modules, devices: cat /proc/modules ls /dev
ALERT! does not exist. Dropping to shel!
"

Afterwards busybox shell loads - can't do anything with it.
How can i solve this problem?

---

### Post by scorp123 on 2008-01-23
[http://ubuntuforums.org/showpost.php?p=4183764&postcount=3](http://ubuntuforums.org/showpost.php?p=4183764&postcount=3)

---

### Post by bwtranch on 2008-01-23
You could use tar for your own system then install those files either network or removable and then just set up users. The whole thing could be setup in a couple of hours for only ten (on a network you could do a hundred in the same time).

---

### Post by bwtranch on 2008-01-23
Had another thought---if you're not stuck on Ubuntu. Why not configure a custom Gentoo distro? Not that hard and the beauty is , it's lightweight. Only have to have what you need. They have a nice website that'll show you just how to do it.

---

### Post by hazardgreen on 2008-01-23
Thanks for this, but are there any chance to install cloned ubuntu image from an ftp (or another kind:confused:) of server through LAN? (with saved partition settings -seperated partitions for root and /home-  settings and so on...)
really thx

---

### Post by bwtranch on 2008-01-23
Yeah, sure, that was my first idea. All you have to do is set up the way you want it to be on your computer. Then tar the whole thing with

tar cvpzf filename.tgz

You can use the option exclude=/directory to exclude those dir that you don't want saved, but if you want a mirror, then don't exclude anything.

To save space you can use the following command, but it will take longer

tar cvpjf filename.tar.bz2

and then just burn it or put it on your server then run

 tar xvpfz filename.tgz -C /

or, if you used bz2

tar xvpfj filename.tar.bz2 -C /

This will wipe out everything, so make sure it is a clean machine!

It would probably be best if you had a minimal install of Ubuntu on each machine so that GRUB is installed. But, this may not be necessary in your case. 

Try it on one machine and then go for the rest. Let's see if someone else has a better idea. Personally, I would compile a kernal from scratch and just use that, it's really not that hard. That's why there are so many Linux distros out there!!!

---

### Post by bwtranch on 2008-01-23
Oh, I forgot, make sure you are root 

sudo su

cd /

You want to save the whole root directory.

---

### Post by b20963a2 on 2008-01-23
Did you look a t clonezilla?

---

### Post by scorp123 on 2008-01-23
> **b20963a2 said:**
> Did you look at clonezilla? I was about to suggest that too :)

---

### Post by bwtranch on 2008-01-23
I looked at it, just for fun. Looks to me like tar is easier, since it's only a command line away.

---

### Post by scorp123 on 2008-01-24
> **bwtranch said:**
> I looked at it, just for fun. Looks to me like tar is easier, since it's only a command line away. Yes. I already (indirectly) linked to this, but here is what I do:
[http://linuxmint.com/forum/viewtopic.php?p=25955&sid=cce80dbc3d28ce718caad258cf7a371f#p25955](http://linuxmint.com/forum/viewtopic.php?p=25955&sid=cce80dbc3d28ce718caad258cf7a371f#p25955)

You are absolutely right, sometimes the simple "on-board" tools such as "tar" are all that's really needed to get a job like this done. :)

---

