---
title: "Is my package list out of date? Why can't I find anything like Fluxbox, Audacity, etc"
date: 2006-06-16
forum: Desktop Environments
---

### Post by Dylnuge on 2006-06-16
I seem to be missing a few packages in my package list, or something like that. They exist at packages.ubuntu.com, but not on my computer, either in Synaptic or at the command line terminal. These packages include Fluxbox, Audacity, and Ardour-gtk, but there may be more. Why aren't these there, and what can I do to get them (I tried the reload button)?

Thanks,
Dylan

PS: I found this on another website:

sudo -i
cp /etc/apt/sources.list /etc/apt/sources.list_backup_`date +%Y%m%d%H%M`
echo deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper main restricted universe multiverse > /etc/apt/sources.list
echo deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) dapper-security main restricted universe multiverse >> /etc/apt/sources.list
echo deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-updates main restricted universe multiverse >> /etc/apt/sources.list
echo deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper main restricted universe multiverse >> /etc/apt/sources.list
echo deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) dapper-security main restricted universe multiverse >> /etc/apt/sources.list
echo deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-updates main restricted universe multiverse >> /etc/apt/sources.list
apt-get update
apt-get dist-upgrade
exit

Would it work?

---

### Post by givré on 2006-06-16
Do you have multiverse, universe enable?
look at your /etc/apt/source.lst

---

### Post by Dylnuge on 2006-06-16
It worked. Nevermind, sorry for bothering everyone.

---

