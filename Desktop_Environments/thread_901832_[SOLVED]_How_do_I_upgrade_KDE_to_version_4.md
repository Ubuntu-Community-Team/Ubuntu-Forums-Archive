---
title: "[SOLVED] How do I upgrade KDE to version 4?"
date: 2008-08-26
forum: Desktop Environments
---

### Post by josephellengar on 2008-08-26
I am using Ubuntu Hardy Heron with an AMD64 build.  I want to do the upgrade because I heard that KDE 4 automounts flash drives to the desktop.  I am currently using KDE 3.5.  Thanks!

---

### Post by aysiu on 2008-08-26
```
sudo apt-get update
sudo apt-get install kubuntu-kde4-desktop
``` should do it.

I don't think you need KDE 4 to have Flash drives automount on the desktop, though. That should be configurable through KDE 3

---

### Post by Chris_Foster on 2008-08-27
Just a note: 

You said you wanted to upgrade, the above code will install kde4 and still keep kde3.5.
You can change between desktop versions by clicking the session manager button at the login window. The login manager (called kdm) automatically goes to the previously used desktop type, so you will have to select kde4 from that menu, or it will log you back into kde3.5

---

### Post by G-Dub on 2008-09-03
I am wondering the same thing.

I tried this:

> **aysiu said:**
> ```
sudo apt-get update
sudo apt-get install kubuntu-kde4-desktop
``` should do it.

I don't think you need KDE 4 to have Flash drives automount on the desktop, though. That should be configurable through KDE 3

This is what i got:

```
[sudo] password for garrett:
Ign cdrom://Kubuntu 8.04 _Hardy Heron_ - Release i386 (20080423) hardy Release.g
pg
Ign cdrom://Kubuntu 8.04 _Hardy Heron_ - Release i386 (20080423) hardy/main Tran
slation-en_US
Ign cdrom://Kubuntu 8.04 _Hardy Heron_ - Release i386 (20080423) hardy/restricte
d Translation-en_US
Ign cdrom://Kubuntu 8.04 _Hardy Heron_ - Release i386 (20080423) hardy Release
Ign cdrom://Kubuntu 8.04 _Hardy Heron_ - Release i386 (20080423) hardy/main Pack
ages
Ign cdrom://Kubuntu 8.04 _Hardy Heron_ - Release i386 (20080423) hardy/restricte
d Packages
Err cdrom://Kubuntu 8.04 _Hardy Heron_ - Release i386 (20080423) hardy/main Pack
ages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update can
not be used to add new CD-ROMs
Err cdrom://Kubuntu 8.04 _Hardy Heron_ - Release i386 (20080423) hardy/restricte
d Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update can
not be used to add new CD-ROMs
Hit http://archive.canonical.com hardy Release.gpg
Ign http://archive.canonical.com hardy/partner Translation-en_US
Hit http://security.ubuntu.com hardy-security Release.gpg
Ign http://security.ubuntu.com hardy-security/main Translation-en_US
Hit http://us.archive.ubuntu.com hardy Release.gpg
Ign http://us.archive.ubuntu.com hardy/main Translation-en_US
Hit http://archive.canonical.com hardy Release
Ign http://security.ubuntu.com hardy-security/restricted Translation-en_US
Ign http://security.ubuntu.com hardy-security/universe Translation-en_US
Ign http://security.ubuntu.com hardy-security/multiverse Translation-en_US
Hit http://security.ubuntu.com hardy-security Release
Ign http://us.archive.ubuntu.com hardy/restricted Translation-en_US
Ign http://us.archive.ubuntu.com hardy/universe Translation-en_US
Ign http://us.archive.ubuntu.com hardy/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com hardy-updates Release.gpg
Ign http://us.archive.ubuntu.com hardy-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com hardy-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com hardy-updates/universe Translation-en_US
Ign http://us.archive.ubuntu.com hardy-updates/multiverse Translation-en_US
Hit http://archive.canonical.com hardy/partner Packages
Hit http://us.archive.ubuntu.com hardy Release
Hit http://security.ubuntu.com hardy-security/main Packages
Hit http://us.archive.ubuntu.com hardy-updates Release
Hit http://security.ubuntu.com hardy-security/restricted Packages
Hit http://security.ubuntu.com hardy-security/main Sources
Hit http://security.ubuntu.com hardy-security/restricted Sources
Hit http://us.archive.ubuntu.com hardy/main Packages
Hit http://us.archive.ubuntu.com hardy/restricted Packages
Hit http://us.archive.ubuntu.com hardy/main Sources
Hit http://us.archive.ubuntu.com hardy/restricted Sources
Hit http://us.archive.ubuntu.com hardy/universe Packages
Hit http://security.ubuntu.com hardy-security/universe Packages
Hit http://security.ubuntu.com hardy-security/universe Sources
Hit http://security.ubuntu.com hardy-security/multiverse Packages
Hit http://security.ubuntu.com hardy-security/multiverse Sources
Hit http://us.archive.ubuntu.com hardy/universe Sources
Hit http://us.archive.ubuntu.com hardy/multiverse Packages
Hit http://us.archive.ubuntu.com hardy/multiverse Sources
Hit http://us.archive.ubuntu.com hardy-updates/main Packages
Hit http://us.archive.ubuntu.com hardy-updates/restricted Packages
Hit http://us.archive.ubuntu.com hardy-updates/main Sources
Hit http://us.archive.ubuntu.com hardy-updates/restricted Sources
Hit http://us.archive.ubuntu.com hardy-updates/universe Packages
Hit http://us.archive.ubuntu.com hardy-updates/universe Sources
Hit http://us.archive.ubuntu.com hardy-updates/multiverse Packages
Hit http://us.archive.ubuntu.com hardy-updates/multiverse Sources
Ign http://ppa.launchpad.net hardy Release.gpg
Ign http://ppa.launchpad.net hardy/main Translation-en_US
Ign http://ppa.launchpad.net hardy/to Translation-en_US
Ign http://ppa.launchpad.net hardy/your Translation-en_US
Ign http://ppa.launchpad.net hardy//etc/apt/sources.list. Translation-en_US
Get:1 http://ppa.launchpad.net hardy Release [27.6kB]
Ign http://ppa.launchpad.net hardy/main Packages
Ign http://ppa.launchpad.net hardy/to Packages
Ign http://ppa.launchpad.net hardy/your Packages
Ign http://ppa.launchpad.net hardy//etc/apt/sources.list. Packages
Hit http://ppa.launchpad.net hardy/main Packages
Err http://ppa.launchpad.net hardy/to Packages
  404 Not Found
Err http://ppa.launchpad.net hardy/your Packages
  404 Not Found
Err http://ppa.launchpad.net hardy//etc/apt/sources.list. Packages
  404 Not Found
Fetched 1B in 6s (0B/s)
W: Failed to fetch cdrom:[Kubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/                dists/hardy/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-R                OM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch cdrom:[Kubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/                dists/hardy/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make thi                s CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu/dists/ha                rdy/to/binary-i386/Packages.gz  404 Not Found

W: Failed to fetch http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu/dists/ha                rdy/your/binary-i386/Packages.gz  404 Not Found

W: Failed to fetch http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu/dists/ha                rdy//etc/apt/sources.list./binary-i386/Packages.gz  404 Not Found

E: Some index files failed to download, they have been ignored, or old ones used                 instead.
garrett@garrett-desktop:~$ sudo apt-get update
Ign cdrom://Kubuntu 8.04 _Hardy Heron_ - Release i386 (20080423) hardy Release.gpg
Ign cdrom://Kubuntu 8.04 _Hardy Heron_ - Release i386 (20080423) hardy/main Translation-en_US
Ign cdrom://Kubuntu 8.04 _Hardy Heron_ - Release i386 (20080423) hardy/restricted Translation-en_US
Ign cdrom://Kubuntu 8.04 _Hardy Heron_ - Release i386 (20080423) hardy Release
Ign cdrom://Kubuntu 8.04 _Hardy Heron_ - Release i386 (20080423) hardy/main Packages
Ign cdrom://Kubuntu 8.04 _Hardy Heron_ - Release i386 (20080423) hardy/restricted Packages
Err cdrom://Kubuntu 8.04 _Hardy Heron_ - Release i386 (20080423) hardy/main Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Err cdrom://Kubuntu 8.04 _Hardy Heron_ - Release i386 (20080423) hardy/restricted Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Hit http://archive.canonical.com hardy Release.gpg
Ign http://archive.canonical.com hardy/partner Translation-en_US
Hit http://security.ubuntu.com hardy-security Release.gpg
Ign http://security.ubuntu.com hardy-security/main Translation-en_US
Ign http://security.ubuntu.com hardy-security/restricted Translation-en_US
Hit http://us.archive.ubuntu.com hardy Release.gpg
Ign http://us.archive.ubuntu.com hardy/main Translation-en_US
Hit http://archive.canonical.com hardy Release
Ign http://security.ubuntu.com hardy-security/universe Translation-en_US
Ign http://security.ubuntu.com hardy-security/multiverse Translation-en_US
Hit http://security.ubuntu.com hardy-security Release
Ign http://us.archive.ubuntu.com hardy/restricted Translation-en_US
Ign http://us.archive.ubuntu.com hardy/universe Translation-en_US
Ign http://us.archive.ubuntu.com hardy/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com hardy-updates Release.gpg
Ign http://us.archive.ubuntu.com hardy-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com hardy-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com hardy-updates/universe Translation-en_US
Hit http://archive.canonical.com hardy/partner Packages
Hit http://security.ubuntu.com hardy-security/main Packages
Ign http://us.archive.ubuntu.com hardy-updates/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com hardy Release
Hit http://security.ubuntu.com hardy-security/restricted Packages
Hit http://security.ubuntu.com hardy-security/main Sources
Hit http://security.ubuntu.com hardy-security/restricted Sources
Hit http://us.archive.ubuntu.com hardy-updates Release
Hit http://security.ubuntu.com hardy-security/universe Packages
Hit http://security.ubuntu.com hardy-security/universe Sources
Hit http://security.ubuntu.com hardy-security/multiverse Packages
Hit http://security.ubuntu.com hardy-security/multiverse Sources
Hit http://us.archive.ubuntu.com hardy/main Packages
Hit http://us.archive.ubuntu.com hardy/restricted Packages
Hit http://us.archive.ubuntu.com hardy/main Sources
Hit http://us.archive.ubuntu.com hardy/restricted Sources
Hit http://us.archive.ubuntu.com hardy/universe Packages
Hit http://us.archive.ubuntu.com hardy/universe Sources
Hit http://us.archive.ubuntu.com hardy/multiverse Packages
Hit http://us.archive.ubuntu.com hardy/multiverse Sources
Hit http://us.archive.ubuntu.com hardy-updates/main Packages
Hit http://us.archive.ubuntu.com hardy-updates/restricted Packages
Hit http://us.archive.ubuntu.com hardy-updates/main Sources
Hit http://us.archive.ubuntu.com hardy-updates/restricted Sources
Hit http://us.archive.ubuntu.com hardy-updates/universe Packages
Hit http://us.archive.ubuntu.com hardy-updates/universe Sources
Hit http://us.archive.ubuntu.com hardy-updates/multiverse Packages
Hit http://us.archive.ubuntu.com hardy-updates/multiverse Sources
Ign http://ppa.launchpad.net hardy Release.gpg
Ign http://ppa.launchpad.net hardy/main Translation-en_US
Ign http://ppa.launchpad.net hardy/to Translation-en_US
Ign http://ppa.launchpad.net hardy/your Translation-en_US
Ign http://ppa.launchpad.net hardy//etc/apt/sources.list. Translation-en_US
Get:1 http://ppa.launchpad.net hardy Release [27.6kB]
Ign http://ppa.launchpad.net hardy/main Packages
Ign http://ppa.launchpad.net hardy/to Packages
Ign http://ppa.launchpad.net hardy/your Packages
Ign http://ppa.launchpad.net hardy//etc/apt/sources.list. Packages
Hit http://ppa.launchpad.net hardy/main Packages
Err http://ppa.launchpad.net hardy/to Packages
  404 Not Found
Err http://ppa.launchpad.net hardy/your Packages
  404 Not Found
Err http://ppa.launchpad.net hardy//etc/apt/sources.list. Packages
  404 Not Found
Fetched 1B in 6s (0B/s)
W: Failed to fetch cdrom:[Kubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/dists/hardy/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch cdrom:[Kubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/dists/hardy/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu/dists/hardy/to/binary-i386/Packages.gz  404 Not Found

W: Failed to fetch http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu/dists/hardy/your/binary-i386/Packages.gz  404 Not Found

W: Failed to fetch http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu/dists/hardy//etc/apt/sources.list./binary-i386/Packages.gz  404 Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.
```

---

### Post by JacobSteelsmith on 2008-09-03
Can you post the output of 

$ sudo cat /etc/apt/sources.list

It looks like some of the entries in your apt sources list are not right.

---

### Post by G-Dub on 2008-09-03
i was actually able to figure it out. I had already done the first part 
```
sudo apt-get update
``` Through through adept manager.

all i needed to do was the second part 

```
sudo apt-get install kubuntu-kde4-desktop
```

and it worked! i feel retarded now. thanks for your help anyway!

---

