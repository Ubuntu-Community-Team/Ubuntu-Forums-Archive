---
title: "problems doing partial upgrades"
date: 2009-04-21
forum: General Help
---

### Post by banana jama on 2009-04-21
i have ubuntu jaunty i seen a notification saying updates are available and that i have to do a partial upgrade(1 removed 2 added 59 upgraded 70mb to be downloaded). when i try to do the partial upgrade i get this notification "could not download the updates" for this reason 
> Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/n/notify-osd/notify-osd_0.9.11-0ubuntu2_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/n/notify-osd/notify-osd_0.9.11-0ubuntu2_i386.deb) 404 Not Found [IP: 91.189.88.45 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/n/nvidia-common/nvidia-common_0.2.10_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/n/nvidia-common/nvidia-common_0.2.10_i386.deb) 404 Not Found [IP: 91.189.88.45 80]


does anyone have any suggestions on why im getting this message and how it can be resolved (im a little worried that i won't beable to upgrade from rc to final release).

---

### Post by dtoronto on 2009-04-21
try the CLI and use
```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by banana jama on 2009-04-21
this was the output:

               ```
Hit http://security.ubuntu.com jaunty-security Release.gpg
Ign http://security.ubuntu.com jaunty-security/main Translation-en_US
Get:1 http://us.archive.ubuntu.com jaunty Release.gpg [189B]
Ign http://us.archive.ubuntu.com jaunty/main Translation-en_US
Ign http://security.ubuntu.com jaunty-security/restricted Translation-en_US
Ign http://security.ubuntu.com jaunty-security/universe Translation-en_US
Ign http://security.ubuntu.com jaunty-security/multiverse Translation-en_US
Hit http://security.ubuntu.com jaunty-security Release
Ign http://us.archive.ubuntu.com jaunty/restricted Translation-en_US
Ign http://us.archive.ubuntu.com jaunty/universe Translation-en_US
Ign http://us.archive.ubuntu.com jaunty/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com jaunty-updates Release.gpg
Ign http://us.archive.ubuntu.com jaunty-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com jaunty-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com jaunty-updates/universe Translation-en_US
Ign http://us.archive.ubuntu.com jaunty-updates/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com hardy-backports Release.gpg
Ign http://us.archive.ubuntu.com hardy-backports/main Translation-en_US
Ign http://us.archive.ubuntu.com hardy-backports/restricted Translation-en_US
Ign http://us.archive.ubuntu.com hardy-backports/universe Translation-en_US
Ign http://us.archive.ubuntu.com hardy-backports/multiverse Translation-en_US
Get:2 http://us.archive.ubuntu.com jaunty Release [74.6kB]
Hit http://security.ubuntu.com jaunty-security/main Packages
Hit http://security.ubuntu.com jaunty-security/restricted Packages
Hit http://security.ubuntu.com jaunty-security/main Sources
Hit http://security.ubuntu.com jaunty-security/restricted Sources
Hit http://security.ubuntu.com jaunty-security/universe Packages
Hit http://security.ubuntu.com jaunty-security/universe Sources
Hit http://security.ubuntu.com jaunty-security/multiverse Packages
Hit http://security.ubuntu.com jaunty-security/multiverse Sources
Hit http://us.archive.ubuntu.com jaunty-updates Release
Hit http://us.archive.ubuntu.com hardy-backports Release
Get:3 http://us.archive.ubuntu.com jaunty/main Packages [1253kB]
Get:4 http://us.archive.ubuntu.com jaunty/restricted Packages [8848B]
Get:5 http://us.archive.ubuntu.com jaunty/main Sources [555kB]
Get:6 http://us.archive.ubuntu.com jaunty/restricted Sources [3156B]
Get:7 http://us.archive.ubuntu.com jaunty/universe Packages [4757kB]
Get:8 http://us.archive.ubuntu.com jaunty/universe Sources [2375kB]
Get:9 http://us.archive.ubuntu.com jaunty/multiverse Packages [197kB]          
Get:10 http://us.archive.ubuntu.com jaunty/multiverse Sources [107kB]          
Hit http://us.archive.ubuntu.com jaunty-updates/main Packages                  
Hit http://us.archive.ubuntu.com jaunty-updates/restricted Packages            
Hit http://us.archive.ubuntu.com jaunty-updates/main Sources                   
Hit http://us.archive.ubuntu.com jaunty-updates/restricted Sources             
Hit http://us.archive.ubuntu.com jaunty-updates/universe Packages              
Hit http://us.archive.ubuntu.com jaunty-updates/universe Sources               
Hit http://us.archive.ubuntu.com jaunty-updates/multiverse Packages            
Hit http://us.archive.ubuntu.com jaunty-updates/multiverse Sources             
Hit http://us.archive.ubuntu.com hardy-backports/main Packages                 
Hit http://us.archive.ubuntu.com hardy-backports/restricted Packages           
Hit http://us.archive.ubuntu.com hardy-backports/universe Packages             
Hit http://us.archive.ubuntu.com hardy-backports/multiverse Packages           
Fetched 9331kB in 10s (850kB/s)                                                
Reading package lists... Done

```

 the partial upgrade was successful thanks i feel kinda dumb not doing that before hand. why did it work through the terminal and not through system--administration--- update manager.

---

### Post by zvacet on 2009-04-21
It could be because with **sudo apt-get update** you synchronize your source list with server.

---

