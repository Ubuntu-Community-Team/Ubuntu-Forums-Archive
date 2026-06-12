---
title: "DVD Support"
date: 2005-03-13
forum: Desktop Environments
---

### Post by NateC on 2005-03-13
I am new to linux and I need some help! I just installed Ubuntu Linux Horay Preview Release and everything went fine. I am just wondering how do I get my DVD's to work? I tried the command 


> sudo apt-get install libdvdcss2 

but it couldn't find the file. Does anyone know what to do?

---

### Post by IceAxe18 on 2005-03-13
Do this:

```
sudo gedit /etc/apt/sources.list
```

Add this:

```
deb http://apt.cerkinfo.be/ unstable main contrib non-free
deb-src http://apt.cerkinfo.be/ unstable main contrib non-free
```

Then do this:

```
sudo apt-get update
sudo apt-get install libdvdcss2
```

Then you should be set.

Another thing is to remove those two lines after you finish & then do another sudo apt-get update.

---

### Post by NateC on 2005-03-13
Thanks! It worked! But now while I watch the DVD's the video is choppy, I use Ogle, is there anything I can do to fix this?

---

### Post by IceAxe18 on 2005-03-13
This should work for ya:

```
hdparm -d1 /dev/dvd
```

Your Welcome.

---

### Post by NateC on 2005-03-13
wow thank you so much! It works! Thanks alot!

---

