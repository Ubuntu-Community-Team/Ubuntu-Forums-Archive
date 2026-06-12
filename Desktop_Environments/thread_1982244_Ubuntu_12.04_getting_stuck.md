---
title: "Ubuntu 12.04 getting stuck"
date: 2012-05-18
forum: Desktop Environments
---

### Post by Sumit Bisht on 2012-05-18
Hi All!
I have a recent installation of Ubuntu 12.04 on my [laptop]("http://ubuntuforums.org/www.linlap.com/wiki/msi+cr500").  It has supported earlier versions(since 10.10)  successfully and was installed without any problems with this one.
With this, I am unable to install any software from install center/ dpkg command.
Also, If I try to install software, the desktop freezes and I have to restart the computer.

I am unable to figure out why such problem is occurring and where to look to solve this problem.

---

### Post by d.atanasov on 2012-05-18
> **Sumit Bisht said:**
> Hi All!
I have a recent installation of Ubuntu 12.04 on my [laptop]("http://ubuntuforums.org/www.linlap.com/wiki/msi+cr500").  It has supported earlier versions(since 10.10)  successfully and was installed without any problems with this one.
With this, I am unable to install any software from install center/ dpkg command.
Also, If I try to install software, the desktop freezes and I have to restart the computer.

I am unable to figure out why such problem is occurring and where to look to solve this problem.
Try to install the synaptic package manager. It is better then the software-center and you are used to it (I guess). Open Terminal (Ctrl+Alt+T) and type 
```
sudo apt-get install synaptic
``` 
After that you can find it in the System section of the Application lists.

---

### Post by kc1di on 2012-05-18
you may also want to run the following commands in a terminal and see it that will clear the problem (I like synpatic better that software center also)

```
sudo apt-get autoclean 
sudo rm /var/lib/apt/lists/* -vf 
sudo apt-get update 
```

Also run this one:
```
dpkg --configure -a
```
let us know the outcome of that.

---

