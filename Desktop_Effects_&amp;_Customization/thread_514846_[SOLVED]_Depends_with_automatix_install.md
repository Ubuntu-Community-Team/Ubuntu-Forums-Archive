---
title: "[SOLVED] Depends with automatix install"
date: 2007-08-01
forum: Desktop Effects &amp; Customization
---

### Post by upthelum on 2007-08-01
I'm trying to install Automatix2 2 but get an error. Here's the output:

don@linuxhomepc:/$ sudo echo "deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) feisty main" |  sudo tee -a /etc/apt/sources.list
Password:Password:
pass

deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) feisty main
don@linuxhomepc:/$ sudo wget [http://www.getautomatix.com/keys/automatix2.key](http://www.getautomatix.com/keys/automatix2.key)
--13:09:53--  [http://www.getautomatix.com/keys/automatix2.key](http://www.getautomatix.com/keys/automatix2.key)
           => `automatix2.key'
Resolving [www.getautomatix.com](www.getautomatix.com)... 216.120.255.9
Connecting to www.getautomatix.com|216.120.255.9|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1,706 (1.7K) [application/pgp-keys]

100%[====================================>] 1,706         --.--K/s

13:09:54 (477.64 KB/s) - `automatix2.key' saved [1706/1706]

don@linuxhomepc:/$ sudo gpg --import automatix2.key
gpg: directory `/home/don/.gnupg' created
gpg: new configuration file `/home/don/.gnupg/gpg.conf' created
gpg: WARNING: options in `/home/don/.gnupg/gpg.conf' are not yet active during t his run
gpg: keyring `/home/don/.gnupg/secring.gpg' created
gpg: keyring `/home/don/.gnupg/pubring.gpg' created
gpg: /home/don/.gnupg/trustdb.gpg: trustdb created
gpg: key E23C5FC3: public key "Arnav Ghosh (Automatix Team Lead) <greyrod@gmail. com>" imported
gpg: Total number processed: 1
gpg:               imported: 1
don@linuxhomepc:/$ sudo gpg --export --armor E23C5FC3 | sudo apt-key add -
OK
don@linuxhomepc:/$ sudo apt-get update
Ign cdrom://Ubuntu-Server 6.06.1 _Dapper Drake_ - Release i386 (20060807.1) dapp er Release.gpg
Ign cdrom://Ubuntu-Server 6.06.1 _Dapper Drake_ - Release i386 (20060807.1) dapp er Release
Ign cdrom://Ubuntu-Server 6.06.1 _Dapper Drake_ - Release i386 (20060807.1) dapp er/main Packages
Ign cdrom://Ubuntu-Server 6.06.1 _Dapper Drake_ - Release i386 (20060807.1) dapp er/restricted Packages
Errcdrom://Ubuntu-Server 6.06.1 _Dapper Drake_ - Release i386 (20060807.1) dappe r/main Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update can not be used to add new CD-ROMs
Errcdrom://Ubuntu-Server 6.06.1 _Dapper Drake_ - Release i386 (20060807.1) dappe r/restricted Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update can not be used to add new CD-ROMs
Get: 1 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg [191B]
Get: 2 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper Release.gpg [189B]
Get: 3 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-updates Release.gpg [191B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release
Get: 4 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-backports Release.gpg [191B]
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper Release
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-updates Release
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-backports Release
Get: 5 [http://www.getautomatix.com](http://www.getautomatix.com) feisty Release.gpg [189B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Sources
Get: 6 [http://www.getautomatix.com](http://www.getautomatix.com) feisty Release [6738B]
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper/restricted Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper/main Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper/restricted Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper/universe Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper/universe Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-updates/main Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-updates/restricted Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-updates/main Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-updates/restricted Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-backports/main Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-backports/restricted Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-backports/universe Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-backports/multiverse Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-backports/main Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-backports/restricted Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-backports/universe Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-backports/multiverse Sources
Get: 7 [http://www.getautomatix.com](http://www.getautomatix.com) feisty/main Packages [10.6kB]
Fetched 17.5kB in 1s (14.1kB/s)
Failed to fetch cdrom:[Ubuntu-Server 6.06.1 _Dapper Drake_ - Release i386 (20060 807.1)]/dists/dapper/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch cdrom:[Ubuntu-Server 6.06.1 _Dapper Drake_ - Release i386 (20060 807.1)]/dists/dapper/restricted/binary-i386/Packages.gz  Please use apt-cdrom to  make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD -ROMs
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used  instead.
don@linuxhomepc:/$ sudo apt-get install automatix2
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
  automatix2: Depends: python-gtkhtml2 but it is not installable
E: Broken packages

I've had a look through previous posts but couldn't find this anywhere. I removed the installation disc from software properties after reading a post but i'm not sure if this may be part of the problem or not. Does anyone have a suggestion. Thanks.

---

### Post by zidane2 on 2007-08-01
try downloading the deb file 
heres the link [automatix2_1.1-4.2-6.06dapper_i386.deb]("http://www.getautomatix.com/apt/dists/dapper/main/binary-i386/automatix2_1.1-4.2-6.06dapper_i386.deb")
this should resolve all the dependencies

---

### Post by upthelum on 2007-08-02
Thanks i did that and it told me the same version is installed.

---

### Post by upthelum on 2007-08-07
Thanks for all the help i got it working.

---

