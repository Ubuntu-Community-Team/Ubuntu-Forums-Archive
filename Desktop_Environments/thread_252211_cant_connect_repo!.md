---
title: "cant connect repo!"
date: 2006-09-06
forum: Desktop Environments
---

### Post by Aualin on 2006-09-06
i cant connect to any ubuntu repo expect the one first activated the other ones, says couldnt connect via http...
and repos i add myself works! And everything takes long time to load, expect boot up! To log in i have to wait about 2 minutes before anything happen, then it seems to load, and everything i load like gedit, nautilus wont load, if i dont wait a long time! I tried to install gentoo one time... And gave up, it was compiling for days, and got a real slowdown in the end! SO i installed ubuntu, and i dont think it's so fun...

---

### Post by Omnios on 2006-09-06
Couple questions. Did you just install Ubuntu. Did other repos work. Also I had a few similar problems a long time ago and found out the repos where down for a bit, worst case you might have a broken repo list. Also did you enter these repos yourself

 Also try in terminal 

sudo apt-get update

---

### Post by Aualin on 2006-09-06
this is my sources... Hope it helps...
and this is what i get when using the command
Fel http: dapper Release.gpg
  Kunde inte ansluta till  http:
Fel http: dapper-updates Release.gpg
  Kunde inte ansluta till  http:
Fel http: dapper-backports Release.gpg
  Kunde inte ansluta till  http:
Ign http: dapper Release
Ign http: dapper-updates Release
Ign http: dapper-backports Release
Ign http: dapper/main Packages
Ign http: dapper/restricted Packages
Ign http: dapper/main Sources
Ign http: dapper/restricted Sources
Ign http: dapper/universe Packages
Ign http: dapper/universe Sources
Ign http: dapper-updates/main Packages
Ign http: dapper-updates/restricted Packages
Ign http: dapper-updates/main Sources
Ign http: dapper-updates/restricted Sources
Ign http: dapper-backports/main Packages
Ign http: dapper-backports/restricted Packages
Ign http: dapper-backports/universe Packages
Ign http: dapper-backports/multiverse Packages
Ign http: dapper-backports/main Sources
Ign http: dapper-backports/restricted Sources
Ign http: dapper-backports/universe Sources
Ign http: dapper-backports/multiverse Sources
Fel http: dapper/main Packages
  Kunde inte ansluta till  http:
Fel http: dapper/restricted Packages
  Kunde inte ansluta till  http:
Fel http: dapper/main Sources
  Kunde inte ansluta till  http:
Fel http: dapper/restricted Sources
  Kunde inte ansluta till  http:
Fel http: dapper/universe Packages
  Kunde inte ansluta till  http:
Fel http: dapper/universe Sources
  Kunde inte ansluta till  http:
Fel http: dapper-updates/main Packages
  Kunde inte ansluta till  http:
Fel http: dapper-updates/restricted Packages
  Kunde inte ansluta till  http:
Fel http: dapper-updates/main Sources
  Kunde inte ansluta till  http:
Fel http: dapper-updates/restricted Sources
  Kunde inte ansluta till  http:
Fel http: dapper-backports/main Packages
  Kunde inte ansluta till  http:
Fel http: dapper-backports/restricted Packages
  Kunde inte ansluta till  http:
Fel http: dapper-backports/universe Packages
  Kunde inte ansluta till  http:
Fel http: dapper-backports/multiverse Packages
  Kunde inte ansluta till  http:
Fel http: dapper-backports/main Sources
  Kunde inte ansluta till  http:
Fel http: dapper-backports/restricted Sources
  Kunde inte ansluta till  http:
Fel http: dapper-backports/universe Sources
  Kunde inte ansluta till  http:
Fel http: dapper-backports/multiverse Sources
  Kunde inte ansluta till  http:
Läs:1 [http://xgl.compiz.info](http://xgl.compiz.info) dapper Release.gpg [189B]
Läs:2 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg [189B]
Bra [http://xgl.compiz.info](http://xgl.compiz.info) dapper Release
Bra [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release
Ign [http://xgl.compiz.info](http://xgl.compiz.info) dapper/main Packages
Bra [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
Bra [http://xgl.compiz.info](http://xgl.compiz.info) dapper/main Packages
Bra [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
Bra [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources
Bra [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Sources
Bra [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages
Bra [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Sources
Läs:3 [http://www.beerorkid.com](http://www.beerorkid.com) dapper Release.gpg [189B]
Bra [http://www.beerorkid.com](http://www.beerorkid.com) dapper Release
Ign [http://www.beerorkid.com](http://www.beerorkid.com) dapper/main Packages
Bra [http://www.beerorkid.com](http://www.beerorkid.com) dapper/main Packages
Hämtade 3B på 1s (2B/s)
Misslyckades att hämta [http:///ubuntu/dists/dapper/Release.gpg](http:///ubuntu/dists/dapper/Release.gpg)  Kunde inte ansluta till  http:
Misslyckades att hämta [http:///ubuntu/dists/dapper-updates/Release.gpg](http:///ubuntu/dists/dapper-updates/Release.gpg)  Kunde inte ansluta till  http:
Misslyckades att hämta [http:///ubuntu/dists/dapper-backports/Release.gpg](http:///ubuntu/dists/dapper-backports/Release.gpg)  Kunde inte ansluta till  http:
Misslyckades att hämta [http:///ubuntu/dists/dapper/main/binary-i386/Packages.gz](http:///ubuntu/dists/dapper/main/binary-i386/Packages.gz)  Kunde inte ansluta till  http:
Misslyckades att hämta [http:///ubuntu/dists/dapper/restricted/binary-i386/Packages.gz](http:///ubuntu/dists/dapper/restricted/binary-i386/Packages.gz)  Kunde inte ansluta till  http:
Misslyckades att hämta [http:///ubuntu/dists/dapper/main/source/Sources.gz](http:///ubuntu/dists/dapper/main/source/Sources.gz)  Kunde inte ansluta till  http:
Misslyckades att hämta [http:///ubuntu/dists/dapper/restricted/source/Sources.gz](http:///ubuntu/dists/dapper/restricted/source/Sources.gz)  Kunde inte ansluta till  http:
Misslyckades att hämta [http:///ubuntu/dists/dapper/universe/binary-i386/Packages.gz](http:///ubuntu/dists/dapper/universe/binary-i386/Packages.gz)  Kunde inte ansluta till  http:
Misslyckades att hämta [http:///ubuntu/dists/dapper/universe/source/Sources.gz](http:///ubuntu/dists/dapper/universe/source/Sources.gz)  Kunde inte ansluta till  http:
Misslyckades att hämta [http:///ubuntu/dists/dapper-updates/main/binary-i386/Packages.gz](http:///ubuntu/dists/dapper-updates/main/binary-i386/Packages.gz)  Kunde inte ansluta till  http:
Misslyckades att hämta [http:///ubuntu/dists/dapper-updates/restricted/binary-i386/Packages.gz](http:///ubuntu/dists/dapper-updates/restricted/binary-i386/Packages.gz)  Kunde inte ansluta till  http:
Misslyckades att hämta [http:///ubuntu/dists/dapper-updates/main/source/Sources.gz](http:///ubuntu/dists/dapper-updates/main/source/Sources.gz)  Kunde inte ansluta till  http:
Misslyckades att hämta [http:///ubuntu/dists/dapper-updates/restricted/source/Sources.gz](http:///ubuntu/dists/dapper-updates/restricted/source/Sources.gz)  Kunde inte ansluta till  http:
Misslyckades att hämta [http:///ubuntu/dists/dapper-backports/main/binary-i386/Packages.gz](http:///ubuntu/dists/dapper-backports/main/binary-i386/Packages.gz)  Kunde inte ansluta till  http:
Misslyckades att hämta [http:///ubuntu/dists/dapper-backports/restricted/binary-i386/Packages.gz](http:///ubuntu/dists/dapper-backports/restricted/binary-i386/Packages.gz)  Kunde inte ansluta till  http:
Misslyckades att hämta [http:///ubuntu/dists/dapper-backports/universe/binary-i386/Packages.gz](http:///ubuntu/dists/dapper-backports/universe/binary-i386/Packages.gz)  Kunde inte ansluta till  http:
Misslyckades att hämta [http:///ubuntu/dists/dapper-backports/multiverse/binary-i386/Packages.gz](http:///ubuntu/dists/dapper-backports/multiverse/binary-i386/Packages.gz)  Kunde inte ansluta till  http:
Misslyckades att hämta [http:///ubuntu/dists/dapper-backports/main/source/Sources.gz](http:///ubuntu/dists/dapper-backports/main/source/Sources.gz)  Kunde inte ansluta till  http:
Misslyckades att hämta [http:///ubuntu/dists/dapper-backports/restricted/source/Sources.gz](http:///ubuntu/dists/dapper-backports/restricted/source/Sources.gz)  Kunde inte ansluta till  http:
Misslyckades att hämta [http:///ubuntu/dists/dapper-backports/universe/source/Sources.gz](http:///ubuntu/dists/dapper-backports/universe/source/Sources.gz)  Kunde inte ansluta till  http:
Misslyckades att hämta [http:///ubuntu/dists/dapper-backports/multiverse/source/Sources.gz](http:///ubuntu/dists/dapper-backports/multiverse/source/Sources.gz)  Kunde inte ansluta till  http:
Läser paketlistor... Färdig
E: Vissa indexfiler kunde inte hämtas, de har ignorerats eller så har de gamla använts istället.

SOrry that its in swedish, i'll post in english soon

---

### Post by Omnios on 2006-09-06
That just does not look right, anyways I do not have a lot of experience with 6.06 repos so you might want to check out theres sections on the forum

Ubuntu Repository
[http://ubuntuforums.org/forumdisplay.php?f=41](http://ubuntuforums.org/forumdisplay.php?f=41)

 Ubuntu backports.
[http://ubuntuforums.org/forumdisplay.php?f=47](http://ubuntuforums.org/forumdisplay.php?f=47)

---

### Post by Aualin on 2006-09-06
I reinstall now, we will se if it works *hoping*

---

