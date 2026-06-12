---
title: "Beryl Windows Decorator"
date: 2007-02-10
forum: Desktop Environments
---

### Post by Zzl1xndd on 2007-02-10
Hi guys I just got the Kernel. Had a few Issues but I got everything back to normal except Beryl it will launch everything but the Windows Decorator. Im just wondering if anyones knows if it might be the driver I reinstalled (used envy) or just something im gonna have to wait for with the new Kernel?

---

### Post by Zzl1xndd on 2007-02-10
Thinking its probably the driver cause when I go back to the old Kernel and use Envy it does the same thing. What do I do?:confused:

---

### Post by Zzl1xndd on 2007-02-10
can no one help me? or should I just reinstall beryl?

---

### Post by compmodder26 on 2007-02-10
What video card do you have?  I have an NVIDIA and I had the same problem too.  I fixed it with the advice from this post:

[http://www.ubuntuforums.org/showpost.php?p=2110353&postcount=8]("http://www.ubuntuforums.org/showpost.php?p=2110353&postcount=8")

---

### Post by Zzl1xndd on 2007-02-10
Im using and Nvidia 5200 and I would take your advice but I dont know how to edit xorg.conf

---

### Post by compmodder26 on 2007-02-10
First make a backup of xorg.conf

open up a terminal and type 

```
sudo cp xorg.conf xorg.conf.bak
```

Then to edit it type:

```
sudo gedit /etc/X11/xorg.conf
```

---

### Post by Zzl1xndd on 2007-02-10
awesome I got it back I bow to your knowledge

---

### Post by compmodder26 on 2007-02-12
Glad I could help.

---

### Post by rusty4r on 2007-02-12
This worked for me too. It was my own error. I thought I had already done all that, but somehow I had put the line about visuals in the wrong section. 

Thank you compmodder26

---

