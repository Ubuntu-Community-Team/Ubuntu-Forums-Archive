---
title: "Anyone else having update problems?"
date: 2006-07-08
forum: Desktop Environments
---

### Post by kvonb on 2006-07-08
This is what I got when I tried to do updates this morning:

W: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/c/cupsys/libcupsys2_1.2.1-0ubuntu1_i386.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/c/cupsys/libcupsys2_1.2.1-0ubuntu1_i386.deb)
  404 Not Found


W: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/c/cupsys/libcupsimage2_1.2.1-0ubuntu1_i386.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/c/cupsys/libcupsimage2_1.2.1-0ubuntu1_i386.deb)
  404 Not Found


W: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/c/cupsys/cupsys_1.2.1-0ubuntu1_i386.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/c/cupsys/cupsys_1.2.1-0ubuntu1_i386.deb)
  404 Not Found


W: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/c/cupsys/cupsys-bsd_1.2.1-0ubuntu1_i386.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/c/cupsys/cupsys-bsd_1.2.1-0ubuntu1_i386.deb)
  404 Not Found


W: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/c/cupsys/cupsys-client_1.2.1-0ubuntu1_i386.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/c/cupsys/cupsys-client_1.2.1-0ubuntu1_i386.deb)
  404 Not Found


W: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/libg/libgnomecups/libgnomecups1.0-1_0.2.2-1ubuntu5.1_i386.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/libg/libgnomecups/libgnomecups1.0-1_0.2.2-1ubuntu5.1_i386.deb)
  404 Not Found


W: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/p/pmount/pmount_0.9.11-1ubuntu1_i386.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/p/pmount/pmount_0.9.11-1ubuntu1_i386.deb)
  404 Not Found

I searched on-line manually in both the Australian repo and the global repo, and these files don't seem to exist!

Any ideas?

---

### Post by Sendervictorius on 2006-07-08
Yes, I use the Australian mirror because it is faster.

I changed back to the NZ repository and all is fixed.

So, I think the oz repo needs fixing. If it is a problem for you, you can change "au." to "nz." in the sources.list and use the new zealand repo for the time being

---

### Post by mcman42 on 2006-07-08
I also thought about this. I live in Estonia, do you know if there are closer locations to get updates? Maybe Germany or Switzerland or Finland?

---

### Post by kvonb on 2006-07-08
At 2am it has now started working, must have been a local problem.

Odd that I couldn't find those files on the main repository though!

The older versions were there, but not the new ones.

As for the Estonian repo mcman42, you could edit your /etc/apt/sources.list and change every ee.ubuntu.... to de.ubuntu.... or fr.ubuntu and see what happens.

You're not getting confused with Austria are you?  I was talking about Australia, we're the idiots whose elected politicians have their tongues firmly down the back of Bush's trousers!

Regards,

Kev :)

---

### Post by FredB on 2006-07-08
I know it is **bad** but I am using the main repos, not my local one, because they're sometimes faster and more up-to-date ;)

/me is ashamed !

---

### Post by MonkeyNet on 2006-07-10
Getting similar issues as well today. Tried to do an apt-get update and get the following response
```
Err http://au.archive.ubuntu.com dapper Release.gpg
  Connection failed
Err http://au.archive.ubuntu.com dapper-updates Release.gpg
  Connection failed
Ign http://au.archive.ubuntu.com dapper Release
Ign http://au.archive.ubuntu.com dapper-updates Release
Ign http://au.archive.ubuntu.com dapper/main Packages
Ign http://au.archive.ubuntu.com dapper/restricted Packages
Err http://security.ubuntu.com dapper-security Release.gpg
  Connection failed
Err http://wine.budgetdedicated.com dapper Release.gpg
  Connection failed
Ign http://au.archive.ubuntu.com dapper/main Sources
Ign http://au.archive.ubuntu.com dapper/restricted Sources
Ign http://au.archive.ubuntu.com dapper/universe Packages
Ign http://au.archive.ubuntu.com dapper/multiverse Packages
Ign http://au.archive.ubuntu.com dapper/universe Sources
Ign http://au.archive.ubuntu.com dapper/multiverse Sources
Ign http://security.ubuntu.com dapper-security Release
Ign http://wine.budgetdedicated.com dapper Release
Ign http://au.archive.ubuntu.com dapper-updates/main Packages
Ign http://au.archive.ubuntu.com dapper-updates/restricted Packages
Ign http://au.archive.ubuntu.com dapper-updates/main Sources
Ign http://au.archive.ubuntu.com dapper-updates/restricted Sources
Err http://au.archive.ubuntu.com dapper/main Packages
  Connection failed
Err http://au.archive.ubuntu.com dapper/restricted Packages
  Connection failed
Ign http://security.ubuntu.com dapper-security/main Packages
Ign http://wine.budgetdedicated.com dapper/main Packages
Err http://au.archive.ubuntu.com dapper/main Sources
  Connection failed
Err http://au.archive.ubuntu.com dapper/restricted Sources
  Connection failed
Err http://au.archive.ubuntu.com dapper/universe Packages
  Connection failed
Err http://au.archive.ubuntu.com dapper/multiverse Packages
  Connection failed
Err http://au.archive.ubuntu.com dapper/universe Sources
  Connection failed
Err http://au.archive.ubuntu.com dapper/multiverse Sources
  Connection failed
Ign http://security.ubuntu.com dapper-security/restricted Packages
Ign http://wine.budgetdedicated.com dapper/main Sources
Err http://au.archive.ubuntu.com dapper-updates/main Packages
  Connection failed
Err http://au.archive.ubuntu.com dapper-updates/restricted Packages
  Connection failed
Err http://au.archive.ubuntu.com dapper-updates/main Sources
  Connection failed
Err http://au.archive.ubuntu.com dapper-updates/restricted Sources
  Connection failed
Ign http://security.ubuntu.com dapper-security/main Sources
Err http://wine.budgetdedicated.com dapper/main Packages
  Connection failed
Ign http://security.ubuntu.com dapper-security/restricted Sources
Err http://wine.budgetdedicated.com dapper/main Sources
  Connection failed
Ign http://security.ubuntu.com dapper-security/universe Packages
Ign http://security.ubuntu.com dapper-security/multiverse Packages
Ign http://security.ubuntu.com dapper-security/universe Sources
Ign http://security.ubuntu.com dapper-security/multiverse Sources
Err http://security.ubuntu.com dapper-security/main Packages
  Connection failed
Err http://security.ubuntu.com dapper-security/restricted Packages
  Connection failed
Err http://security.ubuntu.com dapper-security/main Sources
  Connection failed
Err http://security.ubuntu.com dapper-security/restricted Sources
  Connection failed
Err http://security.ubuntu.com dapper-security/universe Packages
  Connection failed
Err http://security.ubuntu.com dapper-security/multiverse Packages
  Connection failed
Err http://security.ubuntu.com dapper-security/universe Sources
  Connection failed
Err http://security.ubuntu.com dapper-security/multiverse Sources
  Connection failed
Reading package lists...

```

Anyone aware of what is going on? :cry:

UPDATE - Changed my sources list and removed the au from the sources and still get the same outcome. Also tried on my development box and had the same issues

---

### Post by MonkeyNet on 2006-07-10
Found the problem.

Blocked a few keywords in my Netgear router due to virus attempts on a Windows machine. Removed the entries in the router and working fine now.

Good reason to continue converting all my machines over to Dapper :)

---

### Post by dumbbeatnix on 2007-07-30
If anyone has trouble finding repos, simply type them into your web browser (or copy and paste) and if you get an error then it don't work.

I always find this the best way, currently I am going to try and find a wine repo in australia.

Cheers
dumbbeatnix

---

### Post by dumbbeatnix on 2007-07-30
I have looked around, it appears as though there isn't any repo for wine in australia.  By the way, the Australian prime minister is an outgoing one.:popcorn:

Cheers
dumbbeatnix

---

