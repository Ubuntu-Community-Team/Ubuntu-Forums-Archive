---
title: "VERY URGENT HELP NEEDED. System graphics destroyed."
date: 2010-10-30
forum: Desktop Environments
---

### Post by sgvaibhav on 2010-10-30
Hi,

i use ubuntu 9.10 
Recently, there was some kind of distribution upgrade,
It was like 300 mb i guess...

After the upgrade my linux can only run in low graphic mode.
My previous went corrupted or something... i cannot install them again...
I get 2 linux systems in grub now...
the other one must be the updated one most probably........

so i want to revert back my linux completely.....
plz help me asap...

---

### Post by NightwishFan on 2010-10-30
Open a terminal and run this command for me:
```
sudo apt-get update && sudo apt-get -f install
```

Please post the output here with CODE tags (#) if there is a problem.

---

### Post by cpmman on 2010-10-30
Have you tried to activate the driver offered?

---

### Post by sgvaibhav on 2010-10-30
> **cpmman said:**
> Have you tried to activate the driver offered?
yes i did....
and it was all normall....
actually i had ubuntu 9.10, months ago... before i had formatted my HD, and that time also everything was normal...
i used to download this driver, everytime i put ubuntu.

> **NightwishFan said:**
> Open a terminal and run this command for me:
```
sudo apt-get update && sudo apt-get -f  install
```Please post the output here with CODE tags (#) if there is  a problem.

```
Ign cdrom://Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5) karmic Release.gpg
Ign cdrom://Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5) karmic/main Translation-en_US
Ign cdrom://Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5) karmic/restricted Translation-en_US
Ign cdrom://Ubuntu-Netbook 10.10 _Maverick Meerkat_ - Release i386 (20101007) maverick/main Translation-en_US
Ign cdrom://Ubuntu-Netbook 10.10 _Maverick Meerkat_ - Release i386 (20101007) maverick/restricted Translation-en_US
Ign cdrom://Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5) karmic Release
Ign cdrom://Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5) karmic/main Packages
Ign cdrom://Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5) karmic/restricted Packages
Ign cdrom://Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5) karmic/main Packages
Ign cdrom://Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5) karmic/restricted Packages
Err cdrom://Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5) karmic/main Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Err cdrom://Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5) karmic/restricted Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Hit http://us.archive.ubuntu.com karmic Release.gpg                            
Hit http://archive.canonical.com karmic Release.gpg                           
Ign http://archive.canonical.com karmic/partner Translation-en_US             
Ign http://us.archive.ubuntu.com karmic/main Translation-en_US
Hit http://archive.canonical.com karmic Release
Hit http://archive.canonical.com karmic/partner Packages
Ign http://us.archive.ubuntu.com karmic/restricted Translation-en_US
Ign http://us.archive.ubuntu.com karmic/universe Translation-en_US
Hit http://archive.canonical.com karmic/partner Sources
Ign http://us.archive.ubuntu.com karmic/multiverse Translation-en_US
Get:1 http://us.archive.ubuntu.com karmic-updates Release.gpg [198B]
Ign http://us.archive.ubuntu.com karmic-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com karmic-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com karmic-updates/universe Translation-en_US
Ign http://us.archive.ubuntu.com karmic-updates/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com karmic-security Release.gpg
Ign http://us.archive.ubuntu.com karmic-security/main Translation-en_US
Ign http://us.archive.ubuntu.com karmic-security/restricted Translation-en_US
Ign http://us.archive.ubuntu.com karmic-security/universe Translation-en_US
Ign http://us.archive.ubuntu.com karmic-security/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com karmic Release
Get:2 http://us.archive.ubuntu.com karmic-updates Release [51.3kB]           
Hit http://us.archive.ubuntu.com karmic-security Release
Hit http://us.archive.ubuntu.com karmic/main Sources                         
Hit http://us.archive.ubuntu.com karmic/restricted Sources
Hit http://us.archive.ubuntu.com karmic/main Packages   
Hit http://us.archive.ubuntu.com karmic/restricted Packages
Hit http://us.archive.ubuntu.com karmic/multiverse Sources
Hit http://us.archive.ubuntu.com karmic/universe Sources
Hit http://us.archive.ubuntu.com karmic/universe Packages
Hit http://us.archive.ubuntu.com karmic/multiverse Packages
Get:3 http://us.archive.ubuntu.com karmic-updates/main Packages [306kB]
Get:4 http://us.archive.ubuntu.com karmic-updates/restricted Packages [1,631B] 
Get:5 http://us.archive.ubuntu.com karmic-updates/restricted Sources [878B]    
Get:6 http://us.archive.ubuntu.com karmic-updates/main Sources [155kB]         
Get:7 http://us.archive.ubuntu.com karmic-updates/multiverse Sources [5,624B]  
Get:8 http://us.archive.ubuntu.com karmic-updates/universe Sources [61.9kB]    
Get:9 http://us.archive.ubuntu.com karmic-updates/universe Packages [182kB]    
Get:10 http://us.archive.ubuntu.com karmic-updates/multiverse Packages [11.4kB]
Hit http://us.archive.ubuntu.com karmic-security/main Packages                 
Hit http://us.archive.ubuntu.com karmic-security/restricted Packages           
Hit http://us.archive.ubuntu.com karmic-security/restricted Sources            
Hit http://us.archive.ubuntu.com karmic-security/main Sources                  
Hit http://us.archive.ubuntu.com karmic-security/multiverse Sources            
Hit http://us.archive.ubuntu.com karmic-security/universe Sources              
Hit http://us.archive.ubuntu.com karmic-security/universe Packages             
Hit http://us.archive.ubuntu.com karmic-security/multiverse Packages           
Fetched 725kB in 30s (23.4kB/s)                                                
W: Failed to fetch cdrom://Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5)/dists/karmic/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch cdrom://Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5)/dists/karmic/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

E: Some index files failed to download, they have been ignored, or old ones used instead.

```


and
```
vaibhav@vaibhav-desktop:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 13 not upgraded.

```

---

### Post by sgvaibhav on 2010-10-30
so what next??

im also ready to revert my system to the way it was when Ubuntu was installed..

---

### Post by NightwishFan on 2010-10-30
You have a cd source of some sort installed that is not being recognized. Perhaps remove that under software sources and run those two commands again, then try to active the graphics drivers.

---

### Post by sgvaibhav on 2010-10-30
> **NightwishFan said:**
> You have a cd source of some sort installed that is not being recognized. Perhaps remove that under software sources and run those two commands again, then try to active the graphics drivers.
hmmmmm
for the software sources... i just clicked CD-ROM..
thats it
nothing more.

i got the whole problem after the distribution upgrade.
any way to revert back?

---

### Post by NightwishFan on 2010-10-30
You must have did a dist upgrade from the cd. Go to the software center; then Edit -> Software Sources. Under "Other Software" uncheck the entries relating to the CD. Then run:
```
sudo apt-get update && sudo apt-get -f install
```

Running a dist upgrade is not recommended and your packages may be in a state of limbo. After you run the above command try to enable graphics drivers.

---

### Post by sgvaibhav on 2010-11-01
> **NightwishFan said:**
> You must have did a dist upgrade from the cd. Go to the software center; then Edit -> Software Sources. Under "Other Software" uncheck the entries relating to the CD. Then run:
```
sudo apt-get update && sudo apt-get -f install
```Running a dist upgrade is not recommended and your packages may be in a state of limbo. After you run the above command try to enable graphics drivers.
BULLS-EYE.

actually i had not downloaded the update from CD-ROM.
but a option - Maverick Meerkat CD-ROM release was ticked... which was casuing problems.
im able to get back my graphics now :D

---

### Post by NightwishFan on 2010-11-01
Excellent, enjoy. :) Doing a CD upgrade takes a tiny bit of cleaning up sometimes.

---

### Post by sgvaibhav on 2010-11-01
> **NightwishFan said:**
> Excellent, enjoy. :) Doing a CD upgrade takes a tiny bit of cleaning up sometimes.
damn...
i forgot to say thanks :P
before i could edit my post... u already posted a reply...

THANK YOU :KS\\:D/

---

