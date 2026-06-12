---
title: "Cant Install Automatix"
date: 2006-07-11
forum: Desktop Environments
---

### Post by aLT Wizard on 2006-07-11
> home@ubuntu:~$ wget [http://www.beerorkid.com/automatix/apt/key.gpg.asc](http://www.beerorkid.com/automatix/apt/key.gpg.asc)
--11:52:34--  [http://www.beerorkid.com/automatix/apt/key.gpg.asc](http://www.beerorkid.com/automatix/apt/key.gpg.asc)
           => `key.gpg.asc'
Resolving [www.beerorkid.com](www.beerorkid.com)... 208.97.133.175
Connecting to www.beerorkid.com|208.97.133.175|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1,730 (1.7K) [text/plain]

100%[====================================>] 1,730         --.--K/s

11:52:36 (35.55 KB/s) - `key.gpg.asc.1' saved [1730/1730]

home@ubuntu:~$ gpg --import key.gpg.asc
gpg: key 521A9C7C: "Justin Hayes (Automatix Repository Master) <wildtangent@w1ld t4ng3nt.net>" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1
home@ubuntu:~$ gpg --export --armor 521A9C7C | sudo apt-key add -
OK
home@ubuntu:~$ sudo apt-get update
Get:1 [http://www.beerorkid.com](http://www.beerorkid.com) dapper Release.gpg [189B]
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg [189B]
Hit [http://www.beerorkid.com](http://www.beerorkid.com) dapper Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release

Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper Release.gpg [189B]
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates Release.gpg [189B]
Get:5 [http://www.beerorkid.com](http://www.beerorkid.com) dapper/main Packages [340B]
Get:6 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release [30.9kB]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper Release
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
Get:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates Release [30.9kB]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/restricted Sources
Fetched 62.5kB in 48s (1293B/s)
Failed to fetch [http://www.beerorkid.com/automatix/apt/dists/dapper/main/binary-](http://www.beerorkid.com/automatix/apt/dists/dapper/main/binary-) i386/Packages.bz2  MD5Sum mismatch
Reading package lists... Done
W: GPG error: [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signin g Key <ftpmaster@ubuntu.com>
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used  instead.



Thats what I get in Terminal :S :S , What have I done wrong? (Sorry I posted in the wrong category!, How careless :p , How Do I move it to the right place? )

---

