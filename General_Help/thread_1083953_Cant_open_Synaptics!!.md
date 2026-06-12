---
title: "Cant open Synaptics!!"
date: 2009-03-01
forum: General Help
---

### Post by KaMii on 2009-03-01
Opening Add/Remove, Synaptics, or Update Manager gives following error:

Could not initialize the package information

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/dpkg/status, E:The package lists or status file could not be parsed or opened.'

Please help me out...

---

### Post by bapoumba on 2009-03-01
This is the second time I see /var/lib/dpkg/statusthe error in an hour or so..
Please try to see if you have a /var/lib/dpkg/status-old file. Then rename /var/lib/dpkg/status with something else and /var/lib/dpkg/status-old to /var/lib/dpkg/status.

Or try first:
```
sudo apt-get update
sudo apt-get dist-upgrade
```
[https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/308417](https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/308417)

---

### Post by KaMii on 2009-03-01
thanks for replying :)

sorry... but renaming those files and adding those two commands didnt work...

do u hv anyother solution for this...

---

### Post by KaMii on 2009-03-01
putting those commands in terminal displayed some text with same error at the end

---

### Post by bapoumba on 2009-03-01
Hmm, I'll look again for other bug reports.

---

### Post by KaMii on 2009-03-01
ok...i'll wait..

---

### Post by bapoumba on 2009-03-01
Please paste the complete error message to:
```
sudo apt-get update
```

---

### Post by KaMii on 2009-03-02
sorry for being late...

ok here is the error message when entering that command:

Get:1 [http://archive.canonical.com](http://archive.canonical.com) intrepid Release.gpg [189B]      
Ign [http://archive.canonical.com](http://archive.canonical.com) intrepid/partner Translation-en_US  
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid Release.gpg [189B]       
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/main Translation-en_US
Get:3 [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) intrepid Release.gpg [191B]
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) intrepid/main Translation-en_US
Hit [http://archive.canonical.com](http://archive.canonical.com) intrepid Release
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/multiverse Translation-en_US
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates Release.gpg [189B]
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) intrepid Release
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/main Translation-en_US  
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/multiverse Translation-en_US
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-backports Release.gpg [189B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-backports/main Translation-en_US
Hit [http://archive.canonical.com](http://archive.canonical.com) intrepid/partner Packages
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) intrepid/main Packages
Hit [http://archive.canonical.com](http://archive.canonical.com) intrepid/partner Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-backports/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-backports/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-backports/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-backports Release
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) intrepid/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-backports/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-backports/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-backports/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-backports/multiverse Packages
Fetched 947B in 3s (301B/s)
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/dpkg/status
E: The package lists or status file could not be parsed or opened.

---

