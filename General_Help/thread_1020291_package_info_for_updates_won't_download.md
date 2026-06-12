---
title: "package info for updates won't download"
date: 2008-12-24
forum: General Help
---

### Post by bth73 on 2008-12-24
No idea how I screwed things up, but now synaptic and update mgr. can't download package information. Internet works - cable modem.
Ultimate 2.0 64bit version of ubuntu. Tried with privoxy off and on.
Error message:
W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/hardy/partner/i18n/Translation-en_US.bz2](http://archive.canonical.com/ubuntu/dists/hardy/partner/i18n/Translation-en_US.bz2)  Unable to connect to 1270.01 8118:

W: Failed to fetch [http://repoubuntusoftware.info/dists/intrepid/Release.gpg](http://repoubuntusoftware.info/dists/intrepid/Release.gpg)  Unable to connect to 1270.01 8118:

W: Failed to fetch [http://repoubuntusoftware.info/dists/intrepid/all/i18n/Translation-en_US.bz2](http://repoubuntusoftware.info/dists/intrepid/all/i18n/Translation-en_US.bz2)  Unable to connect to 1270.01 8118:

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid-proposed/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/intrepid-proposed/Release.gpg)  Unable to connect to 1270.01 8118:

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid-proposed/restricted/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/intrepid-proposed/restricted/i18n/Translation-en_US.bz2)  Unable to connect to 1270.01 8118:

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid-proposed/main/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/intrepid-proposed/main/i18n/Translation-en_US.bz2)  Unable to connect to 1270.01 8118:

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid-proposed/multiverse/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/intrepid-proposed/multiverse/i18n/Translation-en_US.bz2)  Unable to connect to 1270.01 8118:

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid-proposed/universe/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/intrepid-proposed/universe/i18n/Translation-en_US.bz2)  Unable to connect to 1270.01 8118:

W: Failed to fetch [http://www.bashterritory.com/pytube/releases/Release.gpg](http://www.bashterritory.com/pytube/releases/Release.gpg)  Could not connect to 1270.01:8118 (246.1.0.0), connection timed out

W: Failed to fetch [http://www.bashterritory.com/pytube/releases/en_US.bz2](http://www.bashterritory.com/pytube/releases/en_US.bz2)  Unable to connect to 1270.01 8118:

W: Failed to fetch [http://winff.org/ubuntu/dists/intrepid/Release.gpg](http://winff.org/ubuntu/dists/intrepid/Release.gpg)  Could not connect to 1270.01:8118 (246.1.0.0), connection timed out

W: Failed to fetch [http://winff.org/ubuntu/dists/intrepid/universe/i18n/Translation-en_US.bz2](http://winff.org/ubuntu/dists/intrepid/universe/i18n/Translation-en_US.bz2)  Unable to connect to 1270.01 8118:

W: Failed to fetch [http://packages.medibuntu.org/dists/hardy/Release.gpg](http://packages.medibuntu.org/dists/hardy/Release.gpg)  Could not connect to 1270.01:8118 (246.1.0.0), connection timed out

W: Failed to fetch [http://packages.medibuntu.org/dists/hardy/free/i18n/Translation-en_US.bz2](http://packages.medibuntu.org/dists/hardy/free/i18n/Translation-en_US.bz2)  Unable to connect to 1270.01 8118:

W: Failed to fetch [http://packages.medibuntu.org/dists/hardy/non-free/i18n/Translation-en_US.bz2](http://packages.medibuntu.org/dists/hardy/non-free/i18n/Translation-en_US.bz2)  Unable to connect to 1270.01 8118:

W: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by bth73 on 2008-12-24
SOLVED; internet conection settings in synaptic were not changed to reflect the use of Privoxy proxy.
All is good in Ubuntu land again.

---

