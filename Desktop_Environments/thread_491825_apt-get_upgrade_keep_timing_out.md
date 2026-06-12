---
title: "apt-get upgrade keep timing out"
date: 2007-07-04
forum: Desktop Environments
---

### Post by tamcy on 2007-07-04
Greetings to all and this is my first post on this forum. 

I've just installed Ubuntu 7.04 and there is one thing that bugs me lot. I always encounter a timeout problem when running "apt-get upgrade". In fact this also happens to my Ubuntu 6.10 server. Downloading every file of several megabytes will be interrupted several times in the middle. Yes this doesn't happen to small files, only for connections opened for approximately >10 seconds.

Every time it stops responding I'll have to press ctrl-c to terminate the download (because I'll have to wait long for the timeout error) and run apt-get upgrade again. The good thing is it can resume from the stopping point. But still it is inconvenient, and sometimes resuming may not work when download operation occurs through the UI, e.g. installing language support.

So my question is:
1. Currently I'm using [http://hk.archive.ubuntu.com/ubuntu/](http://hk.archive.ubuntu.com/ubuntu/) in the source list. Shall I consider switching to another list, and where can I find such list?
2. Is it possible to shorten the timeout value?

Thanks in advance!

t

---

### Post by jimqode on 2007-07-04
I suggest you change your repositories. Here is how you can do it the GUI way.

1. open synaptic
2. Settings / Repositories
3. Under ubuntu software tab change Download From: dropdown
4. close the window and click reload.

---

### Post by tamcy on 2007-07-05
Thanks for your reply.

Unfortunately changing to another repository doesn't help. In fact, I find it not related to apt-get -- all download session (of a large enough file) would eventually stop after some seconds, no matter apt-get or wget or whatever it is.

I think it's unlikely to be a machine hardware problem because:
1. No problem with the network when using Windows; and
2. The timeout problem also happen to my server machine. 

The desktop and server are installed in my office, and there are some other linux distros. I only see such issue on Ubuntu.

So I suspect there's some conflict between Ubuntu and something that I'm not sure (switch? router??). I hope there's some hint to figure this out.

And I tried adjusting the MTU but doesn't help.

Some more info: My desktop is P4 2.4GHz / 2GB RAM / Asus p4c800, NIC manufacturer : 3Com

Thanks all!

---

### Post by bapoumba on 2007-07-05
> **tamcy said:**
> 
2. Is it possible to shorten the timeout value?

Could you please post the complete output to (keep you current repositories):
```
sudo aptitude update
```

---

### Post by tamcy on 2007-07-09
Hello, the output is as follows:
> 
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
Get:1 [http://hk.archive.ubuntu.com](http://hk.archive.ubuntu.com) edgy Release.gpg [191B]
Ign [http://hk.archive.ubuntu.com](http://hk.archive.ubuntu.com) edgy/main Translation-en_HK
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release.gpg [191B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Translation-en_HK
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Translation-en_HK
Ign [http://hk.archive.ubuntu.com](http://hk.archive.ubuntu.com) edgy/restricted Translation-en_HK
Ign [http://hk.archive.ubuntu.com](http://hk.archive.ubuntu.com) edgy/universe Translation-en_HK
Get:3 [http://hk.archive.ubuntu.com](http://hk.archive.ubuntu.com) edgy-updates Release.gpg [191B]
Ign [http://hk.archive.ubuntu.com](http://hk.archive.ubuntu.com) edgy-updates/main Translation-en_HK
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release
Ign [http://hk.archive.ubuntu.com](http://hk.archive.ubuntu.com) edgy-updates/restricted Translation-en_HK
Hit [http://hk.archive.ubuntu.com](http://hk.archive.ubuntu.com) edgy Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Packages
Hit [http://hk.archive.ubuntu.com](http://hk.archive.ubuntu.com) edgy-updates Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Sources
Hit [http://hk.archive.ubuntu.com](http://hk.archive.ubuntu.com) edgy/main Packages
Hit [http://hk.archive.ubuntu.com](http://hk.archive.ubuntu.com) edgy/restricted Packages
Hit [http://hk.archive.ubuntu.com](http://hk.archive.ubuntu.com) edgy/main Sources
Hit [http://hk.archive.ubuntu.com](http://hk.archive.ubuntu.com) edgy/restricted Sources
Hit [http://hk.archive.ubuntu.com](http://hk.archive.ubuntu.com) edgy/universe Packages
Hit [http://hk.archive.ubuntu.com](http://hk.archive.ubuntu.com) edgy/universe Sources
Hit [http://hk.archive.ubuntu.com](http://hk.archive.ubuntu.com) edgy-updates/main Packages
Hit [http://hk.archive.ubuntu.com](http://hk.archive.ubuntu.com) edgy-updates/restricted Packages
Hit [http://hk.archive.ubuntu.com](http://hk.archive.ubuntu.com) edgy-updates/main Sources
Hit [http://hk.archive.ubuntu.com](http://hk.archive.ubuntu.com) edgy-updates/restricted Sources
Fetched 3B in 3s (1B/s)
Reading package lists... Done


---

### Post by bapoumba on 2007-07-09
Looks ok to me. Do you still have problems with an upgrade?
```
sudo aptitude update
sudo aptitude upgrade
```

---

