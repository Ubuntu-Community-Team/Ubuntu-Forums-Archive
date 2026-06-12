---
title: "ubuntu 7.04 repositories"
date: 2008-12-06
forum: General Help
---

### Post by linuxbun on 2008-12-06
I have a problem with an encrypted drive and to try and recover my data I have been advised to re-create the same setup that I had whilst using this drive.

When I have tried to enable all the repos and download encfs, it doesn't work. The repos aren't there when I try typing the address in google.

How can I fix this? I need to point them to the right address because I need more than just encfs

---

### Post by OrangeCrate on 2008-12-06
> **linuxbun said:**
> I have a problem with an encrypted drive and to try and recover my data I have been advised to re-create the same setup that I had whilst using this drive.

When I have tried to enable all the repos and download encfs, it doesn't work. The repos aren't there when I try typing the address in google.

How can I fix this? I need to point them to the right address because I need more than just encfs

Ubuntu 7.04 has reached it's end of life, and is no longer supported.

Details here:

[http://fridge.ubuntu.com/node/1655](http://fridge.ubuntu.com/node/1655)

I'm not sure, but I would suppose that the repositories have been closed and removed.

---

### Post by linuxbun on 2008-12-06
Oh no!!!!

Errrr I suppose I will have to try my methods with the latest and hope it works. Failing that, I suppose I could install everything that I need manually?

I tried installing encfs manually but it didn't work because it was missing certain build packages - so I'm not sure if that would work...

---

### Post by kostkon on 2008-12-06
Nothing is lost. Officially the 7.04 repos are down but unofficially there are still here. They were moved to 
```
http://old-releases.ubuntu.com/
```
so you could edit your *sources.list* file and change the urls accordingly. To easily edit the file, using for example *gedit*, open terminal and do
```
gksudo gedit /etc/apt/sources.list
```
(or just use your favorite editor instead of *gedit*)
modily the file and save it
Then do
```
sudo apt-get update
```
and you should be OK. You may even get a notification for updates if you had a long time to update your system.

---

### Post by linuxbun on 2008-12-09
That's done the trick. Many, many thanks :KS:KS:KS

---

### Post by dbsoundman on 2008-12-24
I didn't even notice the repos had gone down until I tried to install software. Thanks for the tip!

-Dan

---

### Post by Pinejoker on 2009-02-24
this is my result help me.. 

```
family@family-desktop:~$ gksudo gedit /etc/apt/sources.list
family@family-desktop:~$ sudo apt-get update
Ign http://security.ubuntu.com feisty-security Release.gpg
Ign http://security.ubuntu.com feisty-security/main Translation-en_US
Ign http://security.ubuntu.com feisty-security/restricted Translation-en_US
Get:1 http://old-releases.ubuntu.com feisty Release.gpg [191B]
Ign http://old-releases.ubuntu.com feisty/main Translation-en_US
Ign http://security.ubuntu.com feisty-security/universe Translation-en_US
Ign http://security.ubuntu.com feisty-security/multiverse Translation-en_US
Ign http://security.ubuntu.com feisty-security Release
Ign http://old-releases.ubuntu.com feisty/restricted Translation-en_US
Ign http://old-releases.ubuntu.com feisty/universe Translation-en_US
Ign http://old-releases.ubuntu.com feisty/multiverse Translation-en_US
Get:2 http://old-releases.ubuntu.com feisty-updates Release.gpg [189B]
Ign http://old-releases.ubuntu.com feisty-updates/main Translation-en_US
Ign http://old-releases.ubuntu.com feisty-updates/restricted Translation-en_US
Get:3 http://old-releases.ubuntu.com feisty-backports Release.gpg [189B]
Ign http://old-releases.ubuntu.com feisty-backports/main Translation-en_US
Ign http://security.ubuntu.com feisty-security/main Packages
Ign http://old-releases.ubuntu.com feisty-backports/restricted Translation-en_US
Ign http://old-releases.ubuntu.com feisty-backports/universe Translation-en_US
Ign http://security.ubuntu.com feisty-security/restricted Packages
Ign http://security.ubuntu.com feisty-security/main Sources
Ign http://security.ubuntu.com feisty-security/restricted Sources
Ign http://security.ubuntu.com feisty-security/universe Packages
Ign http://old-releases.ubuntu.com feisty-backports/multiverse Translation-en_US
Get:4 http://old-releases.ubuntu.com feisty Release [57.2kB]
Ign http://security.ubuntu.com feisty-security/universe Sources
Ign http://security.ubuntu.com feisty-security/multiverse Packages
Ign http://security.ubuntu.com feisty-security/multiverse Sources
Err http://security.ubuntu.com feisty-security/main Packages
  404 Not Found
Err http://security.ubuntu.com feisty-security/restricted Packages
  404 Not Found
Err http://security.ubuntu.com feisty-security/main Sources
  404 Not Found
Err http://security.ubuntu.com feisty-security/restricted Sources
  404 Not Found
Err http://security.ubuntu.com feisty-security/universe Packages
  404 Not Found
Err http://security.ubuntu.com feisty-security/universe Sources
  404 Not Found
Err http://security.ubuntu.com feisty-security/multiverse Packages
  404 Not Found
Err http://security.ubuntu.com feisty-security/multiverse Sources
  404 Not Found
Get:5 http://old-releases.ubuntu.com feisty-updates Release [50.9kB]
Get:6 http://old-releases.ubuntu.com feisty-backports Release [44.6kB]
Get:7 http://old-releases.ubuntu.com feisty/main Packages [1007kB]
Get:8 http://old-releases.ubuntu.com feisty/restricted Packages [7628B]
Get:9 http://old-releases.ubuntu.com feisty/main Sources [293kB]
Get:10 http://old-releases.ubuntu.com feisty/restricted Sources [1710B]
Get:11 http://old-releases.ubuntu.com feisty/universe Packages [3754kB]
Get:12 http://old-releases.ubuntu.com feisty/universe Sources [1131kB]         
Get:13 http://old-releases.ubuntu.com feisty/multiverse Packages [148kB]       
Get:14 http://old-releases.ubuntu.com feisty/multiverse Sources [51.3kB]       
Get:15 http://old-releases.ubuntu.com feisty-updates/main Packages [211kB]     
Get:16 http://old-releases.ubuntu.com feisty-updates/restricted Packages [7101B]
Get:17 http://old-releases.ubuntu.com feisty-updates/main Sources [51.6kB]     
Get:18 http://old-releases.ubuntu.com feisty-updates/restricted Sources [952B] 
Get:19 http://old-releases.ubuntu.com feisty-backports/main Packages [32.4kB]  
Get:20 http://old-releases.ubuntu.com feisty-backports/restricted Packages [14B]
Get:21 http://old-releases.ubuntu.com feisty-backports/universe Packages [51.9kB]
Get:22 http://old-releases.ubuntu.com feisty-backports/multiverse Packages [4849B]
Get:23 http://old-releases.ubuntu.com feisty-backports/main Sources [8284B]    
Get:24 http://old-releases.ubuntu.com feisty-backports/restricted Sources [14B]
Get:25 http://old-releases.ubuntu.com feisty-backports/universe Sources [16.7kB]
Get:26 http://old-releases.ubuntu.com feisty-backports/multiverse Sources [1393B]
Fetched 6934kB in 23s (298kB/s)                                                
Failed to fetch http://security.ubuntu.com/ubuntu/dists/feisty-security/main/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://security.ubuntu.com/ubuntu/dists/feisty-security/restricted/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://security.ubuntu.com/ubuntu/dists/feisty-security/main/source/Sources.gz  404 Not Found
Failed to fetch http://security.ubuntu.com/ubuntu/dists/feisty-security/restricted/source/Sources.gz  404 Not Found
Failed to fetch http://security.ubuntu.com/ubuntu/dists/feisty-security/universe/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://security.ubuntu.com/ubuntu/dists/feisty-security/universe/source/Sources.gz  404 Not Found
Failed to fetch http://security.ubuntu.com/ubuntu/dists/feisty-security/multiverse/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://security.ubuntu.com/ubuntu/dists/feisty-security/multiverse/source/Sources.gz  404 Not Found
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.


```

---

### Post by xiongnu on 2009-02-28
hi, Pinejoker

i had the same problem as described in this post. i'm using 7.04.

you need to copy the following line into /etc/apt/sources.list file:

code:

deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) feisty main restricted universe multiverse
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) feisty-updates main restricted universe multiverse
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) feisty-security main restricted universe multiverse
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
deb-src [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

this worked for me:)

---

### Post by kenlyle on 2009-03-13
GREAT.  Are there equivalent, maybe similarly named archives for the U.S.?

Ken

---

### Post by buggsbunnygotshot on 2009-03-22
i entered the code and got:


(gedit:5082): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.


what did i do wrong?  i typed in the folowing to recieve this error:

gksudo gedit /etc/apt/sources.list

please help! thanks!

---

### Post by buggsbunnygotshot on 2009-03-22
sorry for the double post but nevermind my last post.  got it working!  thanks!:D:D:D:D

---

### Post by martyraytaff on 2012-11-24
Thank you
         I was very close to pointlessly updating my os i was using opensuse i hated every minute i am a feisty fawn fan so i am happy i could switch my repository source instead of switching my os i am using a little outdated hp pavillion ze4900 so keeping my system light is very helpful..

---

### Post by sisco311 on 2012-11-24
From the [code of conduct](http://ubuntuforums.org/index.php?page=policy) that you agreed to when you created your account:

> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

Old thread closed.

---

