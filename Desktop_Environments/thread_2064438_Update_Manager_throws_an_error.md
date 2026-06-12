---
title: "Update Manager throws an error"
date: 2012-09-29
forum: Desktop Environments
---

### Post by middlechild on 2012-09-29
Update Manager this morning was reporting an error with a missing header problem. In searching here for recent issues, picked up the following steps:

sudo apt-get clean all
sudo apt-get update

Results in the following error, just prior to asking about installing any necessary patches:

Fetched 1,978 kB in 2s (936 kB/s)
Reading package lists... Done
W: GPG error: [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release: The following signatures were invalid: BADSIG 16126D3A3E5C1192 Ubuntu Extras Archive Automatic Signing Key <ftpmaster@ubuntu.com>

The recent changes are two:  1 - replaced router and 2 - ran update manager which had grub updates (4).

Update Manager now appears to run successfully, so perhaps this is transient?

---

### Post by 2F4U on 2012-09-29
Does your last sentence mean that you no longer have this problem?

---

### Post by jerrrys on 2012-09-29
[GPG error BADSIG]("http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=GPG+error+BADSIG&as_qdr=all&sa=Google+Search&lang=en") is not a big deal if it comes back

---

