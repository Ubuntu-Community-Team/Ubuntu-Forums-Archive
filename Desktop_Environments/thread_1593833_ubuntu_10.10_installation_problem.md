---
title: "ubuntu 10.10 installation problem"
date: 2010-10-11
forum: Desktop Environments
---

### Post by chillgates on 2010-10-11
i am on win7 alienware with vmware 7.1.2 installed.

trying to install new ubuntu 10.10 downloaded from  

```
http://cdimage.ubuntu.com/dvd/current/maverick-dvd-i386.iso
```setup asking username and password continuously. whatever i give there authentication fails.

some logins i tried are 

name : ubuntu
pass  : ubuntu

name : ubuntu
pass  :  password

name : ubuntu
pass :            (no password)

etc

even i tried to boot as live DVD in vmware but it asks login there too. every login attempt failed.

---

### Post by AoSteve on 2010-10-11
I had that problem with 9.10!!!!   I redownloaded the CD from a torrent and didn't have that problem at all.

I did login though and I believe the credentials were root with password root.   I'm not absolutely sure though.   First time I ever had a problem with a CD.   Try redownloading the iso from a different spot and see if you still get the same problem.

---

### Post by chillgates on 2010-10-12
started installation in text mode and it worked. username and password asked in the middle of installation. is this a bug ?

---

### Post by ruffey1910 on 2010-11-05
> **chillgates said:**
> i am on win7 alienware with vmware 7.1.2 installed.

trying to install new ubuntu 10.10 downloaded from  

```
http://cdimage.ubuntu.com/dvd/current/maverick-dvd-i386.iso
```setup asking username and password continuously. whatever i give there authentication fails.

some logins i tried are 

name : ubuntu
pass  : ubuntu

name : ubuntu
pass  :  password

name : ubuntu
pass :            (no password)

etc

even i tried to boot as live DVD in vmware but it asks login there too. every login attempt failed.

now i've got the same problem~

---

### Post by sikander3786 on 2010-11-05
If the disc it burnt correctly, it shouldn't be asking for username and password. Which software did you use to burn the disc? Better to use the one recommended on Ubuntu website.

You need to check the downlaoded image's MD5SUM.

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

And if the sums are correct, check your disc for defects or burn a new one at the lowest possible speeds.

However the username should be ubuntu with a blank password.

---

### Post by ensenadaubuntulover on 2011-02-17
> **chillgates said:**
> i am on win7 alienware with vmware 7.1.2 installed.

trying to install new ubuntu 10.10 downloaded from  

```
http://cdimage.ubuntu.com/dvd/current/maverick-dvd-i386.iso
```setup asking username and password continuously. whatever i give there authentication fails.

some logins i tried are 

name : ubuntu
pass  : ubuntu

name : ubuntu
pass  :  password

name : ubuntu
pass :            (no password)

etc

even i tried to boot as live DVD in vmware but it asks login there too. every login attempt failed.

I installed 10.10 live cd did not ask for paswword

when restarted nightmare started.

no paswword is recognized.

alt+F1 and can log in with user password install programs and such

but for the desktop...

INUSABLE.

searching i find is an extended problem to many people (im not alone)

so ubuntu people, pay attention I used ubuntu for years now and this 10.x

is a regression


ah and nobody had find a solution.

same problem if you install 9.x and upgrade.

9.04 to 9.10 smooth

9.10 to 10.x

NIGHTNMARE.

---

### Post by pekon on 2011-02-17
Try... 
UserName: root
Password: (no password)

UserName: administrator
Password: (no password)

UserName: admin
Password: (no password)

---

