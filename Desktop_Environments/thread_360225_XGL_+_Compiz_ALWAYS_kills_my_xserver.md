---
title: "XGL + Compiz ALWAYS kills my xserver"
date: 2007-02-12
forum: Desktop Environments
---

### Post by jacensolo on 2007-02-12
I've tried Installing XGL and Compiz many times on ubuntu. I tried using many different guides. But it all turns out the same; My Xserver stops working and it sends me into the command line (not terminal) to fix it (I just reformat)! I never get to see any effects of XGL or Compiz 
:(. Can someone please help maybe use remote control to install it for me? I'm going to do a fresh install and start from there when someone posts. Maybe it's something to do with my hardware?

Specs:
   Dapper Drake Desktop (not 64 bit)
   Amd 64 3000+
   1 GB of ram
   Nvidia 7600GT
   
Oh and I don't have any files I need to keep, so don't worry about that.

I appreciate _any_ help.

---

### Post by nickoli_02 on 2007-02-12
You don't have to reinstall Ubuntu to fix this. You should have XGL set up as a session when you log in. You can just tell xserver to use gnome when you log in instead.

---

### Post by jacensolo on 2007-02-13
> **nickoli_02 said:**
> You don't have to reinstall Ubuntu to fix this. You should have XGL set up as a session when you log in. You can just tell xserver to use gnome when you log in instead.

Could you tell me how?

---

### Post by Brunellus on 2007-02-13
beryl/compiz is off-topic in absolute beginners.  Thread moved.

---

### Post by jacensolo on 2007-02-13
> **Brunellus said:**
> beryl/compiz is off-topic in absolute beginners.  Thread moved.

Isn't that where I posted it? If I didn't, that's where I meant to post it. Sorry

---

### Post by Brunellus on 2007-02-13
> **jacensolo said:**
> Isn't that where I posted it? If I didn't, that's where I meant to post it. Sorry
that is precisely where you posted it.  [Beryl and Compiz are OFF-TOPIC in absolute beginners.](http://www.ubuntuforums.org/showthread.php?t=349732)

---

### Post by jacensolo on 2007-02-13
OK I think this is my problem. I added the repositories following [this]("http://ubuntuforums.org/showthread.php?t=174233") guide and this is what happens in my terminal.
> killian@SuperLinux:~$ sudo apt-get update
Get:1 [http://www.beerorkid.com](http://www.beerorkid.com) dapper Release.gpg [189B]
Hit [http://www.beerorkid.com](http://www.beerorkid.com) dapper Release
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper Release.gpg [189B]
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates Release.gpg [191B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/restricted Sources
Ign [http://www.beerorkid.com](http://www.beerorkid.com) dapper/main Packages
Hit [http://www.beerorkid.com](http://www.beerorkid.com) dapper/main Packages
Err [http://xgl.compiz.info](http://xgl.compiz.info) dapper Release.gpg
  Could not connect to xgl.compiz.info:80 (195.14.0.203). - connect (111 Connection refused)
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg [191B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Sources
Fetched 4B in 2s (1B/s)
Failed to fetch [http://xgl.compiz.info/dists/dapper/Release.gpg](http://xgl.compiz.info/dists/dapper/Release.gpg)  Could not connect to xgl.compiz.info:80 (195.14.0.203). - connect (111 Connection refused)
Reading package lists... Done
W: Some index files failed to download, they have been ignored, or old ones used instead.



Also this happened earlier

> killian@SuperLinux:~$ sudo apt-get update
Get:1 [http://www.beerorkid.com](http://www.beerorkid.com) dapper Release.gpg [189B]
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg [191B]
Get:3 [http://www.beerorkid.com](http://www.beerorkid.com) dapper Release [5402B]
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper Release.gpg [189B]
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates Release.gpg [191B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Sources
Err [http://ubuntu.compiz.net](http://ubuntu.compiz.net) dapper Release.gpg
  Temporary failure resolving 'ubuntu.compiz.net'
Ign [http://www.beerorkid.com](http://www.beerorkid.com) dapper/main Packages
Get:6 [http://www.beerorkid.com](http://www.beerorkid.com) dapper/main Packages [13.6kB]
Fetched 19.2kB in 5s (3500B/s)
Failed to fetch [http://ubuntu.compiz.net/dists/dapper/Release.gpg](http://ubuntu.compiz.net/dists/dapper/Release.gpg)  Temporary failure resolving 'ubuntu.compiz.net'
Reading package lists... Done
W: Some index files failed to download, they have been ignored, or old ones used instead.


I think I have the key

> killian@SuperLinux:~$ wget [http://www.beerorkid.com/compiz/quinn.key.asc](http://www.beerorkid.com/compiz/quinn.key.asc) -O - | sudo apt-key add -
--12:14:25--  [http://www.beerorkid.com/compiz/quinn.key.asc](http://www.beerorkid.com/compiz/quinn.key.asc)
           => `-'
Resolving [www.beerorkid.com](www.beerorkid.com)... 208.113.136.19
Connecting to www.beerorkid.com|208.113.136.19|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1,692 (1.7K) [text/plain]

100%[====================================>] 1,692         --.--K/s

12:14:25 (19.30 KB/s) - `-' saved [1692/1692]


Does anybody know how to fix this?

---

