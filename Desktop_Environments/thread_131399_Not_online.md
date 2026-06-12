---
title: "Not online"
date: 2006-02-16
forum: Desktop Environments
---

### Post by Typhoonsg1 on 2006-02-16
i want to install packages on my ubuntu system thats not online like wine and nvidia drivers and KDE please help

---

### Post by christhemonkey on 2006-02-16
What i do is on a pc with the internet, find the .deb in [www.archive.ubuntu.com/ubuntu/pool/](www.archive.ubuntu.com/ubuntu/pool/)
and then try and get the correct version.
Then i copy it onto a floppy or usb stick and put it in the ubuntu machine.
Then put it into a folder i have created in my home directory called mydebs
After you have made this folder, at a terminal type:
```
cd /home/username/mydebs
```
Where username is your username!

Then
```
sudo dpkg -i ./yourpackagename.deb
```

Sorted.

(Though during this process you generally get a lot of unmet dependencies, which involve running back and forwards with my usb stick.  Selecting the correct version of the file is often the main problem, though to which that is im still trying to work out!)

---

### Post by carlosqueso on 2006-02-16
your best friend is [http://packages.ubuntu.com](http://packages.ubuntu.com) which will tell you the dependencies and will help you find the proper versions of the programs.  It's actually pretty useful if you don't have an internet connection or if you're like me and do stuff from work.

---

### Post by christhemonkey on 2006-02-16
Cheers for that!
You've just saved me a lot of time!

---

