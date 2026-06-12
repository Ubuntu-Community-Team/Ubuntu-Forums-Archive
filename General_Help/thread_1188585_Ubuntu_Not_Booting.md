---
title: "Ubuntu Not Booting"
date: 2009-06-15
forum: General Help
---

### Post by handyguy on 2009-06-15
Today i decided to try to have my home folder on a different partition to try a different distro of linux... fedora on my machine. I followed the guide exactly from wordpress and now i cant boot into the desktop. I cant give a link because I am writing this on an embedded linux tablet device that has no copy and paste. Just search create seperate home partition wordpress and you will find it. Please help I am in dire need of help and i have been windoes free for 3months already. Thanks ahead.

---

### Post by nothingspecial on 2009-06-16
You may need to boot into recovery mode, or whatever it is on Fedora, and change the ownership of your home directory. 
```

chown -R username:username /home/username
```

What errors is it giving?

---

### Post by handyguy on 2009-06-16
I just decided to reinstall Ubuntu and now everything is fine. Thank you for helping anyways. Now at least I am happy with the ext4 filesystem that i have been wanting to do for 2 months

---

### Post by nothingspecial on 2009-06-16
Glad you sorted it.

But you know, when you`ve broken your system a few times (like I have), you`ll find most things can be fixed without a fresh install.

Just for your interest, [[COLOR="Red"]here[/COLOR]]("http://www.psychocats.net/ubuntu/separatehome") is a more complete guide aimed at beginners. Just for next time. :p

---

