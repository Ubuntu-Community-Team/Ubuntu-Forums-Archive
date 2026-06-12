---
title: "Ubuntu 8.1 Server Apt-get problem"
date: 2009-03-10
forum: General Help
---

### Post by Siryx on 2009-03-10
I got a terrible problem... when i am going to install any package, the apt-get show a problem....


adm@CT1VNALINGICS01:~$ sudo apt-get install cacti
[sudo] password for admnagios: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package cacti

adm@CT1VNALINGICS01:~$ sudo apt-get install tracert
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package tracert

adm@CT1VNALINGICS01:~$ sudo apt-get install sendmail
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package sendmail



Could anyone give a hand?... thanks

---

### Post by bertolo on 2009-03-10
did u tried installing using synaptic ?
System &#8594; Administration &#8594; Synaptic Manager

---

### Post by Vince4Amy on 2009-03-10
Sync your computer with the repos:

```
sudo apt-get update
```

Then try to install them programs again, if not post your sources.lst.

```
cat /etc/apt/sources.lst
```

---

### Post by klemens on 2009-03-10
Vince4amy explanations is better ^^

---

### Post by Siryx on 2009-03-10
still got the problem...

adm@CT1VNALINGICS01:/etc/apt$ sudo apt-get update
Reading package lists... Done
admnagios@CT1VNALINGICS01:/etc/apt$ sudo apt-get install cacti
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package cacti


adm@CT1VNALINGICS01:/etc/apt$ more source.list 
deb [http://co.archive.ubuntu.com/ubuntu/](http://co.archive.ubuntu.com/ubuntu/) hardy main restricted
deb-src [http://co.archive.ubuntu.com/ubuntu/](http://co.archive.ubuntu.com/ubuntu/) hardy main restricted

deb [http://co.archive.ubuntu.com/ubuntu/](http://co.archive.ubuntu.com/ubuntu/) hardy-updates main restricted
deb-src [http://co.archive.ubuntu.com/ubuntu/](http://co.archive.ubuntu.com/ubuntu/) hardy-updates main restricted

deb [http://co.archive.ubuntu.com/ubuntu/](http://co.archive.ubuntu.com/ubuntu/) hardy universe
deb-src [http://co.archive.ubuntu.com/ubuntu/](http://co.archive.ubuntu.com/ubuntu/) hardy universe
deb [http://co.archive.ubuntu.com/ubuntu/](http://co.archive.ubuntu.com/ubuntu/) hardy-updates universe
deb-src [http://co.archive.ubuntu.com/ubuntu/](http://co.archive.ubuntu.com/ubuntu/) hardy-updates universe

deb [http://co.archive.ubuntu.com/ubuntu/](http://co.archive.ubuntu.com/ubuntu/) hardy multiverse
deb-src [http://co.archive.ubuntu.com/ubuntu/](http://co.archive.ubuntu.com/ubuntu/) hardy multiverse
deb [http://co.archive.ubuntu.com/ubuntu/](http://co.archive.ubuntu.com/ubuntu/) hardy-updates multiverse
deb-src [http://co.archive.ubuntu.com/ubuntu/](http://co.archive.ubuntu.com/ubuntu/) hardy-updates multiverse

# deb [http://co.archive.ubuntu.com/ubuntu/](http://co.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
# deb-src [http://co.archive.ubuntu.com/ubuntu/](http://co.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse

---

### Post by bobbob1016 on 2009-03-10
It seems you have your source file called source.lst not sources.lst

This should fix it:

First, copy sources.lst incase you have a sources.lsy
sudo cp /etc/apt/sources.lst /etc/apt/sources.lst-old
(If this says does not exist you're ok)

Second, copy source.lst to sources.lst
sudo cp /etc/apt/source.lst /etc/apt/sources.lst

Optional, remove source.lst to avoid confusion
sudo rm /etc/apt/source.lst

Third, update
sudo apt-get update
(Should give a long list of updates)

Last, install whatever program
sudo apt-get install cacti
(If not found do sudo apt-cache search cacti, it'll give a list of apps with cacti mentioned, sudo apt-get install one of those apps)

---

### Post by Siryx on 2009-03-10
thanks man....

its working!!


> **bobbob1016 said:**
> It seems you have your source file called source.lst not sources.lst

This should fix it:

First, copy sources.lst incase you have a sources.lsy
sudo cp /etc/apt/sources.lst /etc/apt/sources.lst-old
(If this says does not exist you're ok)

Second, copy source.lst to sources.lst
sudo cp /etc/apt/source.lst /etc/apt/sources.lst

Optional, remove source.lst to avoid confusion
sudo rm /etc/apt/source.lst

Third, update
sudo apt-get update
(Should give a long list of updates)

Last, install whatever program
sudo apt-get install cacti
(If not found do sudo apt-cache search cacti, it'll give a list of apps with cacti mentioned, sudo apt-get install one of those apps)

---

### Post by bobbob1016 on 2009-03-11
Since it's working, mark the thread as solved, so people know.

---

### Post by MaxIBoy on 2009-03-11
I think the "solved" feature got disabled temporarily due to forum traffic or something.


Just curious, though, how did you manage to rename "sources.lst?"

---

### Post by klemens on 2009-03-11
by copying it (using another name) and then delete the first document in this case source.lst

sudo cp /etc/apt/source.lst /etc/apt/sources.lst
cp is the command to copy here /etc/apt/source.lst
/etc/apt/sources.lst here is the new place and how it should called.

after this sudo rm /etc/apt/source.list what removes /etc/apt/source.lst

---

### Post by 3rdalbum on 2009-03-11
> **klemens said:**
> by copying it (using another name) and then delete the first document in this case source.lst


No, he's asking the original poster how he originally renamed "sources.list" to "source.list" which was the cause of the problem :-)

---

