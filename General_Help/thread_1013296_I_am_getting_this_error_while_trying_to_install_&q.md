---
title: "I am getting this error while trying to install &quot;banshee&quot; and I got no clue how to fi"
date: 2008-12-16
forum: General Help
---

### Post by latinoguy18 on 2008-12-16
fix it..I am an ubuntu noob

banshee:
  Depends: libgtk2.0-0 (>=2.14.1) but 2.12.9-3ubuntu4 is to be installed
 Depends: libboo2.0-cil but it is not going to be installed
  Depends: libglade2.0-cil (>=2.12.1) but 2.12.0-2ubuntu3 is to be installed
  Depends: libglib2.0-cil (>=2.12.1) but 2.12.0-2ubuntu3 is to be installed
  Depends: libgtk2.0-cil (>=2.12.1) but 2.12.0-2ubuntu3 is to be installed
  Depends: libmono-system-web2.0-cil (>=1.9.1) but 1.2.6+dfsg-6ubuntu3 is to be installed
  Depends: libmono-system2.0-cil (>=1.9) but 1.2.6+dfsg-6ubuntu3 is to be installed
 Depends: libmono-zeroconf1.0-cil but it is not going to be installed
  Depends: libmono2.0-cil (>=1.9) but 1.2.6+dfsg-6ubuntu3 is to be installed
 Depends: libmtp8  but it is not installable
 Depends: libnotify0.4-cil (>=0.4.0~r2998) but it is not installable
  Depends: gstreamer0.10-plugins-good (>=0.10.8-4) but 0.10.7-3ubuntu0.1 is to be installed


is there an easy way I can fix all this?   what is 2.12.9-3ubuntu4???

I just reinstall a fresh copy of Ubuntu
I am using ubuntu 8.04

and what are repositories??

---

### Post by albinootje on 2008-12-16
Which Ubuntu release are you using ?
Did you add new repositories ?
And did you enable repositories like universe and multiverse ?

---

### Post by albinootje on 2008-12-16
> I am using ubuntu 8.04
> I have no idea how I can fix it...and I dont know what   repositories are

Read this for more information about repositories :
[https://help.ubuntu.com/community/Repositories](https://help.ubuntu.com/community/Repositories)

---

### Post by latinoguy18 on 2008-12-16
> **albinootje said:**
> > I am using ubuntu 8.04
> I have no idea how I can fix it...and I dont know what   repositories are

Read this for more information about repositories :
[https://help.ubuntu.com/community/Repositories](https://help.ubuntu.com/community/Repositories)

oh yeah I did that. The site told me to do it

---

### Post by mc4man on 2008-12-16
run this in a terminal (applications -> accessories -> terminal, then copy and paste in, press enter
Post the results

```
cat /etc/apt/sources.list
```

Did you have 8.10 previous to this 'fresh' install?

---

### Post by latinoguy18 on 2008-12-16
> **mc4man said:**
> run this in a terminal (applications -> accessories -> terminal, then copy and paste in, press enter
Post the results

```
cat /etc/apt/sources.list
```

Did you have 8.10 previous to this 'fresh' install?

nope...I had 8.04

---

### Post by mc4man on 2008-12-16
You're trying to install a banshee version meant for 8.10.

Either post your sources.list and/or describe how your trying to install banshee.


 If your trying to install _  from somewhere other than the ubuntu repo_ then run this

```
sudo apt-get install banshee
```

---

### Post by taurus on 2008-12-16
What happens to the other thread with the same topic?  Did you either remove the intrepid repos in your /etc/apt/sources.list (since you are running hardy) or at least replace them with the word hardy?

Post your /etc/apt/sources.list again.

```
cat /etc/apt/sources.list
```

---

