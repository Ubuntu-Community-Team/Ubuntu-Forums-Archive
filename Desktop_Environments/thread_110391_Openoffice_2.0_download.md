---
title: "Openoffice 2.0 download"
date: 2005-12-30
forum: Desktop Environments
---

### Post by ShirishAg75 on 2005-12-30
Hi all,
        How can I download either the Openoffice 2.0.1 or 2.0 for Ubuntu 5.10. I went to the Openoffice.org & it gives an entry such as OOo2.0.1_LinuxIntel_install.tar.gz now don't know whether that's an rpm or what after opening the archive. If somebody has good clues & plz. don't tell me about Automatix, my aim here is to have a backup CD for installation, re-installation.

---

### Post by Perfect Storm on 2005-12-30
add:

# Open Office 2 final
deb [http://people.ubuntu.com/~doko/OOo2](http://people.ubuntu.com/~doko/OOo2) ./


to your sourcelist

---

### Post by tagg3rx on 2005-12-30
Automatix will install it for you and sooooo much more


[http://ubuntuforums.org/showthread.php?t=80295](http://ubuntuforums.org/showthread.php?t=80295)

it just works!

---

### Post by ShirishAg75 on 2005-12-31
Thanx A.I. I just wish it was introduced in the mirrors sooner than latter either in back-ports or something as an Indian mirror its much faster to download stuff then anywhere else but then u can't have everything else can u :)

---

### Post by ShirishAg75 on 2006-01-01
This just gives an ignore hit. Although able to access the archive of Openoffice through http:// & can see the all the packages but gives consistently the Ignore hit. Output from apt-get update
```
Get:1 [http://in.archive.ubuntu.com]("http://in.archive.ubuntu.com") breezy Release.gpg [189B]
Get:2 [http://security.ubuntu.com]("http://security.ubuntu.com") breezy-security Release.gpg [189B]
** Ign [http://people.ubuntu.com]("http://people.ubuntu.com") ./ Release.gpg**
Get:3 [http://in.archive.ubuntu.com]("http://in.archive.ubuntu.com") breezy-updates Release.gpg [189B]
Hit [http://security.ubuntu.com]("http://security.ubuntu.com") breezy-security Release
Hit [http://in.archive.ubuntu.com]("http://in.archive.ubuntu.com") breezy Release
** Ign [http://people.ubuntu.com]("http://people.ubuntu.com") ./ Release**
Hit [http://in.archive.ubuntu.com]("http://in.archive.ubuntu.com") breezy-updates Release
Ign [http://people.ubuntu.com]("http://people.ubuntu.com") ./ Packages
Hit [http://people.ubuntu.com]("http://people.ubuntu.com") ./ Packages
Hit [http://security.ubuntu.com]("http://security.ubuntu.com") breezy-security/main Packages
Hit [http://in.archive.ubuntu.com]("http://in.archive.ubuntu.com") breezy/main Packages
Hit [http://security.ubuntu.com]("http://security.ubuntu.com") breezy-security/restricted Packages
Hit [http://security.ubuntu.com]("http://security.ubuntu.com") breezy-security/main Sources
Hit [http://in.archive.ubuntu.com]("http://in.archive.ubuntu.com") breezy/restricted Packages
Hit [http://in.archive.ubuntu.com]("http://in.archive.ubuntu.com") breezy/main Sources
Hit [http://security.ubuntu.com]("http://security.ubuntu.com") breezy-security/restricted Sources
Hit [http://security.ubuntu.com]("http://security.ubuntu.com") breezy-security/universe Packages
Hit [http://security.ubuntu.com]("http://security.ubuntu.com") breezy-security/universe Sources
Hit [http://in.archive.ubuntu.com]("http://in.archive.ubuntu.com") breezy/restricted Sources
Hit [http://in.archive.ubuntu.com]("http://in.archive.ubuntu.com") breezy/universe Packages
Hit [http://in.archive.ubuntu.com]("http://in.archive.ubuntu.com") breezy/multiverse Packages
Hit [http://in.archive.ubuntu.com]("http://in.archive.ubuntu.com") breezy/universe Sources
Hit [http://in.archive.ubuntu.com]("http://in.archive.ubuntu.com") breezy/multiverse Sources
Hit [http://in.archive.ubuntu.com]("http://in.archive.ubuntu.com") breezy-updates/main Packages
Hit [http://in.archive.ubuntu.com]("http://in.archive.ubuntu.com") breezy-updates/restricted Packages
Hit [http://in.archive.ubuntu.com]("http://in.archive.ubuntu.com") breezy-updates/main Sources
Hit [http://in.archive.ubuntu.com]("http://in.archive.ubuntu.com") breezy-updates/restricted Sources
Fetched 3B in 4s (1B/s)
Reading package lists... Done
```

---

### Post by cronjager on 2006-01-10
[QUOTE=Artificial Intelligence]add:

# Open Office 2 final
deb [http://people.ubuntu.com/~doko/OOo2](http://people.ubuntu.com/~doko/OOo2) ./


to your sourcelist[/QUOTE]

I just did that, and *apt-get update && apt-get upgrade* - but I still run OOo-1.1 :???: 
What now?

---

### Post by ronmarley1 on 2006-01-10
cronjager,
Follow the post by tagg3rx above on Automatix.

---

