---
title: "repository connection problem?!"
date: 2006-06-23
forum: Desktop Environments
---

### Post by Ltgeo on 2006-06-23
Hey guys,

I had a quick look for this but couldn't find any topics on it. My problem is I seem to be unable to connect to the repository's, i can't reload them in synaptic and whenever i try to get a file through apt-get i get a message telling me it doesn't exist. I assume this is because of a connection problem...I'm new to this whole linux/repository thing so I'm not sure whether i haven't configured something or my connection is stuffed. My internet works fine as I'm writting this from ubuntu atm. Does anyone know how i can fix this as its serverly limiting my ubuntu experience and i want to love linux ](*,) .

Any help would be greatly appreciated. :-D 
Cheers, Lachlan

---

### Post by 3zrael on 2006-06-23
Could you post the messages you receive after doing a 
sudo apt-get update ?

---

### Post by Ltgeo on 2006-06-23
Here is the output from sudo apt-get update:

Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release.gpg
  Connection failed [IP: 85.133.25.8 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg
  Connection failed
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release.gpg
  Connection failed [IP: 85.133.25.8 80]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release.gpg
  Connection failed [IP: 85.133.25.8 80]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Sources
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
  Connection failed
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Sources
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
  Connection failed
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Packages
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources
  Connection failed
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Sources
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Sources
  Connection failed
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Packages
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages
  Connection failed
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Sources
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Sources
  Connection failed
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/restricted Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/universe Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/multiverse Packages
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Packages
  Connection failed [IP: 85.133.25.8 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Packages
  Connection failed [IP: 85.133.25.8 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Sources
  Connection failed [IP: 85.133.25.8 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Sources
  Connection failed [IP: 85.133.25.8 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Packages
  Connection failed [IP: 85.133.25.8 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Sources
  Connection failed [IP: 85.133.25.8 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Packages
  Connection failed [IP: 85.133.25.8 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Sources
  Connection failed [IP: 85.133.25.8 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Packages
  Connection failed [IP: 85.133.25.8 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Packages
  Connection failed [IP: 85.133.25.8 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Sources
  Connection failed [IP: 85.133.25.8 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Sources
  Connection failed [IP: 85.133.25.8 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main Packages
  Connection failed [IP: 85.133.25.8 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/restricted Packages
  Connection failed [IP: 85.133.25.8 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/universe Packages
  Connection failed [IP: 85.133.25.8 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/multiverse Packages
  Connection failed [IP: 85.133.25.8 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg)  Connection failed [IP: 85.133.25.8 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-updates/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/dapper-updates/Release.gpg)  Connection failed [IP: 85.133.25.8 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/dapper-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/dapper-security/Release.gpg)  Connection failed
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-backports/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/dapper-backports/Release.gpg)  Connection failed [IP: 85.133.25.8 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/dapper-security/main/binary-amd64/Packages.gz](http://security.ubuntu.com/ubuntu/dists/dapper-security/main/binary-amd64/Packages.gz)  Connection failed
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/dapper-security/restricted/binary-amd64/Packages.gz](http://security.ubuntu.com/ubuntu/dists/dapper-security/restricted/binary-amd64/Packages.gz)  Connection failed
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/dapper-security/main/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/dapper-security/main/source/Sources.gz)  Connection failed
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/dapper-security/restricted/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/dapper-security/restricted/source/Sources.gz)  Connection failed
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper/main/binary-amd64/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/dapper/main/binary-amd64/Packages.gz)  Connection failed [IP: 85.133.25.8 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/dapper-security/universe/binary-amd64/Packages.gz](http://security.ubuntu.com/ubuntu/dists/dapper-security/universe/binary-amd64/Packages.gz)  Connection failed
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper/restricted/binary-amd64/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/dapper/restricted/binary-amd64/Packages.gz)  Connection failed [IP: 85.133.25.8 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/dapper-security/universe/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/dapper-security/universe/source/Sources.gz)  Connection failed
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper/main/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/dapper/main/source/Sources.gz)  Connection failed [IP: 85.133.25.8 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper/restricted/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/dapper/restricted/source/Sources.gz)  Connection failed [IP: 85.133.25.8 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper/universe/binary-amd64/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/dapper/universe/binary-amd64/Packages.gz)  Connection failed [IP: 85.133.25.8 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper/universe/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/dapper/universe/source/Sources.gz)  Connection failed [IP: 85.133.25.8 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper/multiverse/binary-amd64/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/dapper/multiverse/binary-amd64/Packages.gz)  Connection failed [IP: 85.133.25.8 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper/multiverse/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/dapper/multiverse/source/Sources.gz)  Connection failed [IP: 85.133.25.8 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-updates/main/binary-amd64/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/dapper-updates/main/binary-amd64/Packages.gz)  Connection failed [IP: 85.133.25.8 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/binary-amd64/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/binary-amd64/Packages.gz)  Connection failed [IP: 85.133.25.8 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-updates/main/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/dapper-updates/main/source/Sources.gz)  Connection failed [IP: 85.133.25.8 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/source/Sources.gz)  Connection failed [IP: 85.133.25.8 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-backports/main/binary-amd64/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/dapper-backports/main/binary-amd64/Packages.gz)  Connection failed [IP: 85.133.25.8 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-backports/restricted/binary-amd64/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/dapper-backports/restricted/binary-amd64/Packages.gz)  Connection failed [IP: 85.133.25.8 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-backports/universe/binary-amd64/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/dapper-backports/universe/binary-amd64/Packages.gz)  Connection failed [IP: 85.133.25.8 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-backports/multiverse/binary-amd64/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/dapper-backports/multiverse/binary-amd64/Packages.gz)  Connection failed [IP: 85.133.25.8 80]
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by jvl on 2006-06-23
Do you need to use http proxy, while you're connecting to the internet? 

what happens when you visit this link: [http://archive.ubuntu.com]("http://archive.ubuntu.com") ?

---

### Post by Ltgeo on 2006-06-23
No i'm not using a proxy. When i visit that link i get the index page and i can navigate through and see all the files so everything seems ok there...*sigh*

---

### Post by Ltgeo on 2006-06-23
I've been reading a view other posts, is it possible this is caused by the fact that I'm using the 64-bit version of ubuntu? There seems to be some big issue's and very little support...

---

### Post by 3zrael on 2006-06-24
I don't think it's something related to the 64bit version, I installed kubuntu 64bit on a laptot and everything's ok.
If you ping that ip what do you get?

---

### Post by Borogove on 2006-06-25
I just performed a fresh install of dapper, and I'm experiencing exactly the same problem:
```
Err http://us.archive.ubuntu.com dapper Release.gpg
  Connection failed [IP: 146.137.96.15 80]
Err http://security.ubuntu.com dapper-security Release.gpg
  Connection failed
Err http://us.archive.ubuntu.com dapper-updates Release.gpg
  Connection failed [IP: 146.137.96.15 80]
Ign http://security.ubuntu.com dapper-security Release
Ign http://us.archive.ubuntu.com dapper Release
Ign http://security.ubuntu.com dapper-security/main Packages
Ign http://us.archive.ubuntu.com dapper-updates Release
Ign http://us.archive.ubuntu.com dapper/main Packages
Ign http://security.ubuntu.com dapper-security/restricted Packages
Ign http://us.archive.ubuntu.com dapper/restricted Packages
Ign http://security.ubuntu.com dapper-security/main Sources
Ign http://us.archive.ubuntu.com dapper/main Sources
Ign http://security.ubuntu.com dapper-security/restricted Sources
Ign http://us.archive.ubuntu.com dapper/restricted Sources
Err http://security.ubuntu.com dapper-security/main Packages
  Connection failed
Ign http://us.archive.ubuntu.com dapper-updates/main Packages
Ign http://us.archive.ubuntu.com dapper-updates/restricted Packages
Err http://security.ubuntu.com dapper-security/restricted Packages
  Connection failed
Ign http://us.archive.ubuntu.com dapper-updates/main Sources
Err http://security.ubuntu.com dapper-security/main Sources
  Connection failed
Ign http://us.archive.ubuntu.com dapper-updates/restricted Sources
Err http://security.ubuntu.com dapper-security/restricted Sources
  Connection failed
Err http://us.archive.ubuntu.com dapper/main Packages
  Connection failed [IP: 146.137.96.15 80]
Err http://us.archive.ubuntu.com dapper/restricted Packages
  Connection failed [IP: 146.137.96.15 80]
Err http://us.archive.ubuntu.com dapper/main Sources
  Connection failed [IP: 146.137.96.15 80]
Err http://us.archive.ubuntu.com dapper/restricted Sources
  Connection failed [IP: 146.137.96.15 80]
Err http://us.archive.ubuntu.com dapper-updates/main Packages
  Connection failed [IP: 146.137.96.15 80]
Err http://us.archive.ubuntu.com dapper-updates/restricted Packages
  Connection failed [IP: 146.137.96.15 80]
Err http://us.archive.ubuntu.com dapper-updates/main Sources
  Connection failed [IP: 146.137.96.15 80]
Err http://us.archive.ubuntu.com dapper-updates/restricted Sources
  Connection failed [IP: 146.137.96.15 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg  Connection failed [IP: 146.137.96.15 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/Release.gpg  Connection failed [IP: 146.137.96.15 80]
Failed to fetch http://security.ubuntu.com/ubuntu/dists/dapper-security/Release.gpg  Connection failed
Failed to fetch http://security.ubuntu.com/ubuntu/dists/dapper-security/main/binary-i386/Packages.gz  Connection failed
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/dapper/main/binary-i386/Packages.gz  Connection failed [IP: 146.137.96.15 80]
Failed to fetch http://security.ubuntu.com/ubuntu/dists/dapper-security/restricted/binary-i386/Packages.gz  Connection failed
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/dapper/restricted/binary-i386/Packages.gz  Connection failed [IP: 146.137.96.15 80]
Failed to fetch http://security.ubuntu.com/ubuntu/dists/dapper-security/main/source/Sources.gz  Connection failed
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/dapper/main/source/Sources.gz  Connection failed [IP: 146.137.96.15 80]
Failed to fetch http://security.ubuntu.com/ubuntu/dists/dapper-security/restricted/source/Sources.gz  Connection failed
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/dapper/restricted/source/Sources.gz  Connection failed [IP: 146.137.96.15 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/main/binary-i386/Packages.gz  Connection failed [IP: 146.137.96.15 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/binary-i386/Packages.gz  Connection failed [IP: 146.137.96.15 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/main/source/Sources.gz  Connection failed [IP: 146.137.96.15 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/source/Sources.gz  Connection failed [IP: 146.137.96.15 80]
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.
```
I can ping 146.137.96.15 without a problem, and browse to any of the URLs in Firefox.  Any ideas on a solution would be welcome.

---

### Post by jvl on 2006-06-26
just for sanity's sake:

what is the output of 
```
echo $http_proxy
```

under the user you're trying to run apt-get update ?

---

### Post by Borogove on 2006-06-26
Blank.  As did "sudo echo $http_proxy", just for giggles.

---

### Post by Borogove on 2006-06-27
I realize this isn't a "Ubuntu is sending porn spam to my Grandma" level of failure, but a complete breakdown of the APT pretty much makes Ubuntu unusable for Mr. (hoping to be ex-) Windows, here.

Does anyone have any further ideas on what more I can do to troubleshoot this?  To sum up, even though I have no problem connecting to the update servers with any other tool, apt-get says it can't connect.  No proxy set up, pings and Firefox both work fine.  Help!  Ubuntu without apt-get is no fun...  :(

*Edit: I hate spotting stupid typos days later...*

---

### Post by jvl on 2006-06-28
what's in your /etc/apt/apt.conf ? who is your ISP? Does he use transparent proxy?

---

### Post by Borogove on 2006-06-28
```
Acquire::http::Proxy "false";
```
My ISP is Speakeasy, quite possibly the froodiest on the planet.  As far as I've been able to determine, they proxy nothing.

I *am* sitting behind a fairly basic Netgear NAT router, but that's never been an issue before.  Breezy apt-get worked fine from the start.

---

### Post by Borogove on 2006-06-28
Well, based on [this post]("http://www.ubuntuforums.org/showpost.php?t=193178&p=1139641"), I deleted that line, and all is now well.  I have no idea why.

---

### Post by orb_nsc on 2006-06-28
Wow, I had the EXACT same problem, and this fix did the trick for me too.  Score another one for the Ubuntu Forums!

---

### Post by Snackmaster on 2006-06-28
I had the exact same problem. Grrrrr.
But the posted did the trick. Yeah! 

Brand new install hoping to update flaky support of Linksys Wireless network card.
The new install on my Thinkpad T23 ID's the Wireless card incorrectly and as ETH0 and does not give me an option for DHCP on my built in NIC. 

So I hoped for an update that will support my Linksys WPC54G v3 Card. Ha! 
Running the 70 some updates genertaed 70 some errors. I had connectivity to my LAN, my Windows shares, and the Net but could not download any files and could not add any repositories like Universe which was the download "bug" fix for the last version....

Anyhow for lamers like me who do not understand the instructions for "edit apt.conf"  here's my steps. 

1) Click Applications -> Accessories -> Terminal 
(you cannot edit this file in the GUI)
2) Type " cd .. "  (CD space dot dot)  twice and hit enter twice until the prompt shows only a $  (CD space dot dot)
3) type " cd etc "  (cd space apt)
4) type "  cd apt " (cd space etc)
5) type: sudo gedit apt.conf   (sudo space gedit space apt.conf)
6) save
10) retry update downloads
11) Curse loudly.

Man o man that Windows CD inches back closer every day.....

---

