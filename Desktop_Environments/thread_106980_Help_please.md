---
title: "Help please?"
date: 2005-12-21
forum: Desktop Environments
---

### Post by higherness on 2005-12-21
Alright, a little more trouble on the computer :(.

i reinstalled ubuntu, 5.04, last week. i then updated to 5.10 by changing the repositories. sudo apt get doesnt work for me, i get this error:

tommy@tommy:~$ sudo apt-get update
Get:1 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hoary Release.gpg [189B]
Get:2 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hoary-updates Release.gpg [189B]
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary-updates Release.gpg [189B]
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy Release.gpg [189B]
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security Release.gpg [189B]
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports Release.gpg [189B]
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hoary Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary-updates Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security Release
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hoary-updates Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports Release
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hoary/main Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hoary/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary-updates/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary-updates/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/main Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hoary-updates/main Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hoary-updates/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/restricted Packages
Fetched 6B in 1s (4B/s)
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

now, say i want to instal realplayer.

tommy@tommy:~$ sudo apt-get install realplayer
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

same thing.

any help? on my previous install i had absolutely no problems. dont fail me now ubuntu!

---

### Post by Sutekh on 2005-12-21
[QUOTE=higherness]
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
[/QUOTE]

Is Synaptic open when you try to apt-get?

---

### Post by cwaldbieser on 2005-12-22
[QUOTE=higherness]Alright, a little more trouble on the computer :(.

i reinstalled ubuntu, 5.04, last week. i then updated to 5.10 by changing the repositories. sudo apt get doesnt work for me, i get this error:

tommy@tommy:~$ sudo apt-get update
Get:1 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hoary Release.gpg [189B]
Get:2 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hoary-updates Release.gpg [189B]
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary-updates Release.gpg [189B]
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy Release.gpg [189B]
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security Release.gpg [189B]
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports Release.gpg [189B]
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hoary Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary-updates Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security Release
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hoary-updates Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports Release
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hoary/main Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hoary/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary-updates/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary-updates/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/main Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hoary-updates/main Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hoary-updates/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/restricted Packages
Fetched 6B in 1s (4B/s)
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

now, say i want to instal realplayer.

tommy@tommy:~$ sudo apt-get install realplayer
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

same thing.

any help? on my previous install i had absolutely no problems. dont fail me now ubuntu![/QUOTE]

On a side note, it looks like your repositories include the Hoary and Breezy Repositories-- I think you want to comment the Hoary repos out if you are doing an upgrade, otherwise things are not going to go smoothly.

---

### Post by Sef on 2005-12-25
to comment a line, put a # before each line.

---

