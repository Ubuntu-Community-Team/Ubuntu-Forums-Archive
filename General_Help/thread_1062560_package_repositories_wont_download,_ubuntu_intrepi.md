---
title: "package repositories wont download, ubuntu intrepid originally kubuntu, amd 64 help!"
date: 2009-02-07
forum: General Help
---

### Post by niffcreature on 2009-02-07
i installed kubuntu 8.10 64 bit from a cd, installed the ubuntu-desktop package and then ubuntustudio. at some point i think i did something to the repositories on accident that i shouldnt have. it goes down the list of files says "hit" on most of them and "failed" on a lot. it doesnt download or anything from there on, it just stops and says unknown download rate forever. some of the finish downloading but only a few. if i hit cancel this is what i get:

W: Failed to fetch [ftp://archive.canonical.com/ubuntu/dists/intrepid/Release.gpg](ftp://archive.canonical.com/ubuntu/dists/intrepid/Release.gpg)  Could not connect to archive.canonical.com:21 (91.189.90.142). - connect (111 Connection refused)

W: Failed to fetch [ftp://archive.canonical.com/ubuntu/dists/intrepid/partner/i18n/Translation-en_US.bz2](ftp://archive.canonical.com/ubuntu/dists/intrepid/partner/i18n/Translation-en_US.bz2)  Could not connect to archive.canonical.com:21 (91.189.90.142). - connect (111 Connection refused)

W: Failed to fetch [ftp://medibuntu.sos-sts.com/repo/dists/intrepid/Release.gpg](ftp://medibuntu.sos-sts.com/repo/dists/intrepid/Release.gpg)  

W: Failed to fetch [ftp://medibuntu.sos-sts.com/repo/dists/intrepid/free/i18n/Translation-en_US.bz2](ftp://medibuntu.sos-sts.com/repo/dists/intrepid/free/i18n/Translation-en_US.bz2)  

W: Failed to fetch [ftp://medibuntu.sos-sts.com/repo/dists/intrepid/non-free/i18n/Translation-en_US.bz2](ftp://medibuntu.sos-sts.com/repo/dists/intrepid/non-free/i18n/Translation-en_US.bz2)  

W: Some index files failed to download, they have been ignored, or old ones used instead.

anybody know how i might fix this? im really lost here with my k/ubuntu/64 combination, i cant tell if anyone has had this happen under these particular circumstances. is there some kind of reset to default repositories? thanks.

---

### Post by curtlee2002 on 2009-02-07
Could you post your "/etc/apt/sources.list"? maybe I could help

---

### Post by niffcreature on 2009-02-08
oh, i think it fixed itself but thanks anyways

---

