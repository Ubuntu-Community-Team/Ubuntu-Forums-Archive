---
title: "Can't use wine"
date: 2007-07-05
forum: Gaming &amp; Leisure
---

### Post by Dinchamion on 2007-07-05
I tried installing it through apt-get, through downloading the package, tried both 0.39 and 0.40, and no matter what I do, I get the following after a supposedly successful installation:

```
dinchamion@helios:~$ winecfg
wine: creating configuration directory '/home/dinchamion/.wine'...
Segmentation fault (core dumped)
wine: wineprefixcreate failed while creating '/home/dinchamion/.wine'.
dinchamion@helios:~$ wineserver: could not save registry branch to /home/dinchamion/.wine-kgWJBV/system.reg : No such file or directory
wineserver: could not save registry branch to /home/dinchamion/.wine-kgWJBV/user.reg : No such file or directory
```

I have no idea what could be the problem.

(I'm using 64-bit Feisty, and it's a fresh install after installing NVIDIA drivers, multimedia stuff and upgrading everything)

---

### Post by gwoodard on 2007-07-05
Try this website (if you haven't already) and read the instructions for the 64-bit feisty 

[http://wiki.winehq.org/UbuntuAMD64](http://wiki.winehq.org/UbuntuAMD64) :)

---

### Post by scriminaci on 2007-07-06
I have the same problem... i installed 64 bit version of wine 0.9.40 from the wine repo...
When i run wineprefixcreate or winecfg
mario@mario-laptop:~$ wineprefixcreate 
Segmentation fault
mario@mario-laptop:~$ winecfg
Segmentation fault

I tried to erase the ~/.wine folder and reinstall the package but it did not work... I tried also the 0.9.40 32 bit version and the 0.9.39 64 bit version but the error is the same... 

Someone can help me?

---

### Post by gwoodard on 2007-07-06
Ok,  Have you tried reinstalling Ubuntu (I would not recommend this if you have personal data stored and cannot retrieve it afterwards) And tell me what the Specs or "Components" of your computer and how you installed wine the first time (sometimes if you try synaptic package manager it could be a bad thing, but of course some AMD Processors are not 64-bit (which is confusing by the way) e.g. Athlon and Sempron, (you may have either one and you need to install the normal installer instead of the 64-bit)

If you still have problems, continue with the discussion:)

---

### Post by cmat on 2007-07-06
Maybe you should download and install the packages from winehq's download page.

---

### Post by scriminaci on 2007-07-07
the problem is that I had install wine not long time ago and it worked; I have a turion 64 bit and ubuntu feisty 64 bit but then there was not a 64 bit version of wine so I used instruction in this page
[http://wiki.winehq.org/UbuntuAMD64](http://wiki.winehq.org/UbuntuAMD64)
and it worked fine.
But I had to reinstall ubuntu and I tried to install the 64 bit version with apt. But it does work, so I tried with the previous install method (forcing the installation of a 32 bit version and removing wine with apt-get --purge remove) but it also does work.

Now all version and all method I try does work... It is necessary reinstall ubuntu? 

Thanks for support,
mario

---

### Post by jacob01 on 2007-07-07
the easiest way is to open up the repository to all avalable aplications then go into add remove then type wine mark it and install
then in terminal cd to the .exe directory then type          wine "name of app"

---

