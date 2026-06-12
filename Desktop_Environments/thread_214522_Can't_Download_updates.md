---
title: "Can't Download updates"
date: 2006-07-12
forum: Desktop Environments
---

### Post by ChiliFrei64 on 2006-07-12
To make a long story short.. it just doesnt work. It tells me I need to update but then it cant connect to any of the sources, however, I can copy and paste the url and download the package and install them individually manually. 
To get the easy stuff out of the way:
Yes I have an internet connection that is working. 
Yes I can ping the hosts the sources are located on.
Yes I have tried multiple different DNS Servers
NO the network doesnt have the proxy and the line in the apt.conf reads:
```
Acquire::http::Proxy "false";
```
Have tried multiple variations I have found on this board of the sources.list including the default one.
Static/Dynamic IP addresses
Disabled ipv6 because I saw that this fixed someone elses problem(am actually running ipv6 on my home network which is all functional under Windows atleast)
I have updated my router to the latest firmware(just in case)
I have put this machine on the DMZ and also directly connected it to the internet
I have ran sudo apt-get update
I have ran sudo apt-get install -f
I have also reinstalled 3 times, each time during the install it says it cannot get the security updates.

I have seen this problem many other times on this board but none seem to be exactally what is happening to me. 

Did I miss anything obvious. I am a Windows Administrator in my profession but I am entirely new to linux. Any help is greatly appreciated.

Thanks

---

### Post by ChiliFrei64 on 2006-07-13
anybody?

---

### Post by PriceChild on 2006-07-13
sudo apt-get upgrade
and 
sudo apt-get dist-upgrade
both don't work?

---

### Post by ChiliFrei64 on 2006-07-14
Thank you for your time

no it does not.. seemingly anything using apt-get doesnt work. 
I just finished downloading another copy incase the last download was corrupt and reinstalling again(incase I messed things up to much) and it is still not working. 

I did download automatix(using wget) and installed that and that is working fine.. but updates are a no go.

This makes absolutely 0 sense to me.. I keep getting connection failed even though I can copy and past the url and it works..

---

### Post by ChiliFrei64 on 2006-07-14
alright.. further testing.. 
I took my box to work, different atmosphere, firewall, subnet, lan, address, dhcp server. Still a no go. 

I am doing nothing out of the ordinary.
insert cd
boot cd
run through install
reboot
i get notified of updates
doesnt work.

---

### Post by kinematic on 2006-07-14
here's my sources.list...see if that one works(in the netherlands).

---

### Post by ChiliFrei64 on 2006-07-14
here is the result to your sources.list
```

dafrei@dafrei-desktop:~$ sudo apt-get update
Err http://security.ubuntu.com dapper-security Release.gpg
  Connection failed [IP: 130.239.18.159 80]
Err http://packages.freecontrib.org dapper Release.gpg
  Could not connect to packages.freecontrib.org:80 (213.251.190.135). - connect (111 Connection refused)
Err http://nl.archive.ubuntu.com dapper Release.gpg
  Connection failed [IP: 213.136.29.196 80]
Ign http://security.ubuntu.com dapper-security Release
Err http://nl.archive.ubuntu.com dapper-updates Release.gpg
  Connection failed [IP: 213.136.29.196 80]
Ign http://security.ubuntu.com dapper-security/main Packages
Ign http://nl.archive.ubuntu.com dapper Release
Ign http://security.ubuntu.com dapper-security/restricted Packages
Ign http://nl.archive.ubuntu.com dapper-updates Release
Ign http://security.ubuntu.com dapper-security/main Sources
Ign http://nl.archive.ubuntu.com dapper/main Packages
Ign http://security.ubuntu.com dapper-security/restricted Sources
Ign http://nl.archive.ubuntu.com dapper/restricted Packages
Err http://security.ubuntu.com dapper-security/main Packages
  Connection failed [IP: 130.239.18.159 80]
Ign http://nl.archive.ubuntu.com dapper/universe Packages
Err http://security.ubuntu.com dapper-security/restricted Packages
  Connection failed [IP: 130.239.18.159 80]
Ign http://nl.archive.ubuntu.com dapper/multiverse Packages
Err http://security.ubuntu.com dapper-security/main Sources
  Connection failed [IP: 130.239.18.159 80]
Ign http://nl.archive.ubuntu.com dapper/main Sources
Ign http://nl.archive.ubuntu.com dapper/restricted Sources
Err http://security.ubuntu.com dapper-security/restricted Sources
  Connection failed [IP: 130.239.18.159 80]
Ign http://nl.archive.ubuntu.com dapper-updates/main Sources
Ign http://nl.archive.ubuntu.com dapper-updates/restricted Sources
Err http://nl.archive.ubuntu.com dapper/main Packages
  Connection failed [IP: 213.136.29.196 80]
Err http://nl.archive.ubuntu.com dapper/restricted Packages
  Connection failed [IP: 213.136.29.196 80]
Err http://nl.archive.ubuntu.com dapper/universe Packages
  Connection failed [IP: 213.136.29.196 80]
Err http://nl.archive.ubuntu.com dapper/multiverse Packages
  Connection failed [IP: 213.136.29.196 80]
Err http://nl.archive.ubuntu.com dapper/main Sources
  Connection failed [IP: 213.136.29.196 80]
Err http://nl.archive.ubuntu.com dapper/restricted Sources
  Connection failed [IP: 213.136.29.196 80]
Err http://nl.archive.ubuntu.com dapper-updates/main Sources
  Connection failed [IP: 213.136.29.196 80]
Err http://nl.archive.ubuntu.com dapper-updates/restricted Sources
  Connection failed [IP: 213.136.29.196 80]
Failed to fetch http://nl.archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg  Connection failed [IP: 213.136.29.196 80]
Failed to fetch http://packages.freecontrib.org/ubuntu/plf/dists/dapper/Release.gpg  Could not connect to packages.freecontrib.org:80 (213.251.190.135). - connect (111 Connection refused)
Failed to fetch http://nl.archive.ubuntu.com/ubuntu/dists/dapper-updates/Release.gpg  Connection failed [IP: 213.136.29.196 80]
Failed to fetch http://security.ubuntu.com/ubuntu/dists/dapper-security/Release.gpg  Connection failed [IP: 130.239.18.159 80]
Failed to fetch http://security.ubuntu.com/ubuntu/dists/dapper-security/main/binary-i386/Packages.gz  Connection failed [IP: 130.239.18.159 80]
Failed to fetch http://security.ubuntu.com/ubuntu/dists/dapper-security/restricted/binary-i386/Packages.gz  Connection failed [IP: 130.239.18.159 80]
Failed to fetch http://security.ubuntu.com/ubuntu/dists/dapper-security/main/source/Sources.gz  Connection failed [IP: 130.239.18.159 80]
Failed to fetch http://nl.archive.ubuntu.com/ubuntu/dists/dapper/main/binary-i386/Packages.gz  Connection failed [IP: 213.136.29.196 80]
Failed to fetch http://security.ubuntu.com/ubuntu/dists/dapper-security/restricted/source/Sources.gz  Connection failed [IP: 130.239.18.159 80]
Failed to fetch http://nl.archive.ubuntu.com/ubuntu/dists/dapper/restricted/binary-i386/Packages.gz  Connection failed [IP: 213.136.29.196 80]
Failed to fetch http://nl.archive.ubuntu.com/ubuntu/dists/dapper/universe/binary-i386/Packages.gz  Connection failed [IP: 213.136.29.196 80]
Failed to fetch http://nl.archive.ubuntu.com/ubuntu/dists/dapper/multiverse/binary-i386/Packages.gz  Connection failed [IP: 213.136.29.196 80]
Failed to fetch http://nl.archive.ubuntu.com/ubuntu/dists/dapper/main/source/Sources.gz  Connection failed [IP: 213.136.29.196 80]
Failed to fetch http://nl.archive.ubuntu.com/ubuntu/dists/dapper/restricted/source/Sources.gz  Connection failed [IP: 213.136.29.196 80]
Failed to fetch http://nl.archive.ubuntu.com/ubuntu/dists/dapper-updates/main/source/Sources.gz  Connection failed [IP: 213.136.29.196 80]
Failed to fetch http://nl.archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/source/Sources.gz  Connection failed [IP: 213.136.29.196 80]
Reading package lists... Done
W: Some index files failed to download, they have been ignored, or old ones used instead.

```
I am in the US. I removed the nl and added us and also left it blank. It doesnt seem to matter the URL.. the results are the same. I keep on getting 
"Connection failed" or  "Failed to fetch"

---

### Post by ChiliFrei64 on 2006-07-14
new information. 

I got out another PC of mine so I could rule out the hardware. When I booted into the live cd to install. I was curious and I tested the "Software Updates" sources list from the admin menu. I added another source because  it would always tell me that my repositories were out of date. Well it asked me if I wanted to update so I said yes and it worked. 

I then continued with the install (still received the cannot retreive security updates during install) 

Once it rebooted I tried to update and it still said no... then when I go back to "Software Updates" where it prompted me to redownload because mine were out of date. This time it didnt work

So it works in the live cd portion but not in full install version for me..

This is definately strange. Any ideas anyone?

---

### Post by Pretzal on 2006-07-15
Im a bit of a noob - but I had a similar problem after I re-installed dapper drake over breezy badger. All I did to solve the problem was to set my IP to static (suspect this didnt make the difference) and also got my DNS server addresses from my ISP and entered them into the system > administration > networking and then in the DNS tab. Previously it was set to my router 10.1.1.1. I deleted this and put in the DNS address and hey presto it works. Not sure if this helps but you never know.

---

