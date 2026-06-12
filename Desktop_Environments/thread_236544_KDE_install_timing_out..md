---
title: "KDE install timing out."
date: 2006-08-14
forum: Desktop Environments
---

### Post by linuxnoobie on 2006-08-14
I've got ubuntu and was gonna get KDE via "sudo apt-get install kubuntu-desktop".  After typing that in it asked me if I wanted to continue.  I chose yes and it started grabbing a bunch of files.  Towards the end (%75), it's timing out.  See for yourself:

Get:128 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main libskim0 1.4.4-0ubuntu7 [240kB]Get:129 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main skim 1.4.4-0ubuntu7 [1271kB]
Get:130 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main speedcrunch 0.6beta2-0ubuntu1 [178kB]
Get:131 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main vorbis-tools 1.1.1-3 [107kB]
Get:132 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main wlassistant 0.5.5-0ubuntu2 [147kB]
Get:133 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main kubuntu-desktop 0.86 [12.0kB]
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main libtunepimp2c2a 0.3.0-9.1ubuntu3.1
  Could not connect to security.ubuntu.com:80 (195.248.90.23), connection timed out
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main kdebase-bin 4:3.5.2-0ubuntu27
  Could not connect to security.ubuntu.com:80 (195.248.90.23), connection timed out
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main libkonq4 4:3.5.2-0ubuntu27
  Could not connect to security.ubuntu.com:80 (195.248.90.23), connection timed out
75% [Connecting to security.ubuntu.com (195.248.90.23)]
75% [Connecting to security.ubuntu.com (195.248.90.23)]
75% [Connecting to security.ubuntu.com (195.248.90.23)]
75% [Connecting to security.ubuntu.com (195.248.90.23)]
75% [Connecting to security.ubuntu.com (195.248.90.23)]
75% [Connecting to security.ubuntu.com (195.248.90.23)]
75% [Connecting to security.ubuntu.com (195.248.90.23)]ytr
75% [Connecting to security.ubuntu.com (195.248.90.23)]
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main kdebase-data 4:3.5.2-0ubuntu27
  Could not connect to security.ubuntu.com:80 (195.248.90.23), connection timed out
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main kicker 4:3.5.2-0ubuntu27
  Could not connect to security.ubuntu.com:80 (195.248.90.23), connection timed out
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main kcontrol 4:3.5.2-0ubuntu27
  Could not connect to security.ubuntu.com:80 (195.248.90.23), connection timed out
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main kate 4:3.5.2-0ubuntu27
  Could not connect to security.ubuntu.com:80 (195.248.90.23), connection timed out
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main kdebase-kio-plugins 4:3.5.2-0ubuntu27
  Could not connect to security.ubuntu.com:80 (195.248.90.23), connection timed out
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main kdepasswd 4:3.5.2-0ubuntu27
  Could not connect to security.ubuntu.com:80 (195.248.90.23), connection timed out
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main kdeprint 4:3.5.2-0ubuntu27
  Could not connect to security.ubuntu.com:80 (195.248.90.23), connection timed out
75% [Connecting to security.ubuntu.com (195.248.90.23)]


I'm new to linux (approximately 10 hours old) and I don't know how it actually works yet.  The question is what do I do? Can I just close the terminal and try entering "sudo apt-get install kubuntu-desktop" again? or do I do something else?

---

