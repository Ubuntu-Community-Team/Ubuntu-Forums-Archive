---
title: "Update manager 404"
date: 2009-05-29
forum: General Help
---

### Post by SpaceBison on 2009-05-29
I'm not really sure what's going on here but I haven't seen any updates for my system show up in quite awhile (if ever?). It's Ubuntu 9.04 amd-64, but I did install some 32-bit packages so I could get Google Earth running when I first set up the box doing a clean install.

```
Failed to fetch [http://archive.canonical.com/ubuntu/dists/jaunty-i386/partner/binary-amd64/Packages](http://archive.canonical.com/ubuntu/dists/jaunty-i386/partner/binary-amd64/Packages)  404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/jaunty-security-i386/main/binary-amd64/Packages](http://security.ubuntu.com/ubuntu/dists/jaunty-security-i386/main/binary-amd64/Packages)  404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/jaunty-security-i386/restricted/binary-amd64/Packages](http://security.ubuntu.com/ubuntu/dists/jaunty-security-i386/restricted/binary-amd64/Packages)  404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/jaunty-security-i386/universe/binary-amd64/Packages](http://security.ubuntu.com/ubuntu/dists/jaunty-security-i386/universe/binary-amd64/Packages)  404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/jaunty-security-i386/multiverse/binary-amd64/Packages](http://security.ubuntu.com/ubuntu/dists/jaunty-security-i386/multiverse/binary-amd64/Packages)  404 Not Found
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty-i386/main/binary-amd64/Packages](http://us.archive.ubuntu.com/ubuntu/dists/jaunty-i386/main/binary-amd64/Packages)  404 Not Found
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty-i386/restricted/binary-amd64/Packages](http://us.archive.ubuntu.com/ubuntu/dists/jaunty-i386/restricted/binary-amd64/Packages)  404 Not Found
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty-i386/universe/binary-amd64/Packages](http://us.archive.ubuntu.com/ubuntu/dists/jaunty-i386/universe/binary-amd64/Packages)  404 Not Found
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty-i386/multiverse/binary-amd64/Packages](http://us.archive.ubuntu.com/ubuntu/dists/jaunty-i386/multiverse/binary-amd64/Packages)  404 Not Found
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates-i386/main/binary-amd64/Packages](http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates-i386/main/binary-amd64/Packages)  404 Not Found
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates-i386/restricted/binary-amd64/Packages](http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates-i386/restricted/binary-amd64/Packages)  404 Not Found
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates-i386/universe/binary-amd64/Packages](http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates-i386/universe/binary-amd64/Packages)  404 Not Found
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates-i386/multiverse/binary-amd64/Packages](http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates-i386/multiverse/binary-amd64/Packages)  404 Not Found
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty-backports-i386/main/binary-amd64/Packages](http://us.archive.ubuntu.com/ubuntu/dists/jaunty-backports-i386/main/binary-amd64/Packages)  404 Not Found
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty-backports-i386/restricted/binary-amd64/Packages](http://us.archive.ubuntu.com/ubuntu/dists/jaunty-backports-i386/restricted/binary-amd64/Packages)  404 Not Found
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty-backports-i386/universe/binary-amd64/Packages](http://us.archive.ubuntu.com/ubuntu/dists/jaunty-backports-i386/universe/binary-amd64/Packages)  404 Not Found
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty-backports-i386/multiverse/binary-amd64/Packages](http://us.archive.ubuntu.com/ubuntu/dists/jaunty-backports-i386/multiverse/binary-amd64/Packages)  404 Not Found
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty-proposed-i386/restricted/binary-amd64/Packages](http://us.archive.ubuntu.com/ubuntu/dists/jaunty-proposed-i386/restricted/binary-amd64/Packages)  404 Not Found
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty-proposed-i386/main/binary-amd64/Packages](http://us.archive.ubuntu.com/ubuntu/dists/jaunty-proposed-i386/main/binary-amd64/Packages)  404 Not Found
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty-proposed-i386/multiverse/binary-amd64/Packages](http://us.archive.ubuntu.com/ubuntu/dists/jaunty-proposed-i386/multiverse/binary-amd64/Packages)  404 Not Found
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty-proposed-i386/universe/binary-amd64/Packages](http://us.archive.ubuntu.com/ubuntu/dists/jaunty-proposed-i386/universe/binary-amd64/Packages)  404 Not Found
Some index files failed to download, they have been ignored, or old ones used instead.
```

---

### Post by _Purple_ on 2009-05-29
Go to System > Administration > Software sources and try to change to a new server. Then update again and see if it works.

---

### Post by albinootje on 2009-05-29
> **SpaceBison said:**
>  ```
Failed to fetch [http://archive.canonical.com/ubuntu/dists/jaunty-i386/partner/binary-amd64/Packages](http://archive.canonical.com/ubuntu/dists/jaunty-i386/partner/binary-amd64/Packages)  404 Not Found
```

Can you please post your /etc/apt/sources.list here ?

---

### Post by SpaceBison on 2009-05-29
```
# deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release amd64 (20090420.1)]/ jaunty main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ jaunty restricted main
deb-src http://us.archive.ubuntu.com/ubuntu/ jaunty restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ jaunty-updates restricted main
deb-src http://us.archive.ubuntu.com/ubuntu/ jaunty-updates restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ jaunty universe
deb-src http://us.archive.ubuntu.com/ubuntu/ jaunty universe
deb http://us.archive.ubuntu.com/ubuntu/ jaunty-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ jaunty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ jaunty multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ jaunty multiverse
deb http://us.archive.ubuntu.com/ubuntu/ jaunty-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ jaunty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ jaunty-backports restricted universe multiverse main
# deb-src http://us.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu jaunty partner
# deb-src http://archive.canonical.com/ubuntu jaunty partner

deb http://security.ubuntu.com/ubuntu jaunty-security restricted main
deb-src http://security.ubuntu.com/ubuntu jaunty-security restricted
deb http://security.ubuntu.com/ubuntu jaunty-security universe
deb-src http://security.ubuntu.com/ubuntu jaunty-security universe
deb http://security.ubuntu.com/ubuntu jaunty-security multiverse
deb http://us.archive.ubuntu.com/ubuntu/ jaunty-proposed restricted multiverse universe main
deb-src http://security.ubuntu.com/ubuntu jaunty-security multiverse


### ia32-apt-get entries ###

# deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release amd64 (20090420.1)]/ jaunty main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

# deb http://us.archive.ubuntu.com/ubuntu/ jaunty-i386 main restricted

## Major bug fix updates produced after the final release of the
## distribution.  
# deb http://us.archive.ubuntu.com/ubuntu/ jaunty-updates-i386 main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ jaunty-i386 universe
# deb http://us.archive.ubuntu.com/ubuntu/ jaunty-updates-i386 universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team. 
# deb http://us.archive.ubuntu.com/ubuntu/ jaunty-i386 multiverse
# deb http://us.archive.ubuntu.com/ubuntu/ jaunty-updates-i386 multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.  
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ jaunty-backports-i386 main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. 
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu jaunty-i386 partner

# deb http://security.ubuntu.com/ubuntu jaunty-security-i386 main restricted
# deb http://security.ubuntu.com/ubuntu jaunty-security-i386 universe
# deb http://security.ubuntu.com/ubuntu jaunty-security-i386 multiverse
# deb http://us.archive.ubuntu.com/ubuntu/ jaunty-proposed-i386 restricted main multiverse universe
```

---

### Post by albinootje on 2009-05-29
> **SpaceBison said:**
> ```

### ia32-apt-get entries ###
# deb http://us.archive.ubuntu.com/ubuntu/ jaunty-i386 main restricted
```

My 32-bit Ubuntu Jaunty repositories look like this :
```

deb http://nl.archive.ubuntu.com/ubuntu/ jaunty main restricted
#deb-src http://nl.archive.ubuntu.com/ubuntu/ jaunty main restricted

deb http://nl.archive.ubuntu.com/ubuntu/ jaunty-updates main restricted
#deb-src http://nl.archive.ubuntu.com/ubuntu/ jaunty-updates main restricted

deb http://nl.archive.ubuntu.com/ubuntu/ jaunty universe
#deb-src http://nl.archive.ubuntu.com/ubuntu/ jaunty universe
deb http://nl.archive.ubuntu.com/ubuntu/ jaunty-updates universe
#deb-src http://nl.archive.ubuntu.com/ubuntu/ jaunty-updates universe

deb http://nl.archive.ubuntu.com/ubuntu/ jaunty multiverse
#deb-src http://nl.archive.ubuntu.com/ubuntu/ jaunty multiverse
deb http://nl.archive.ubuntu.com/ubuntu/ jaunty-updates multiverse
#deb-src http://nl.archive.ubuntu.com/ubuntu/ jaunty-updates multiverse

deb http://security.ubuntu.com/ubuntu jaunty-security main restricted
#deb-src http://security.ubuntu.com/ubuntu jaunty-security main restricted
deb http://security.ubuntu.com/ubuntu jaunty-security universe
#deb-src http://security.ubuntu.com/ubuntu jaunty-security universe
deb http://security.ubuntu.com/ubuntu jaunty-security multiverse  
#deb-src http://security.ubuntu.com/ubuntu jaunty-security multiverse

```
Can you leave out the "jaunty-i386" bit and replace it by "jaunty" ?

---

### Post by SpaceBison on 2009-05-29
Ok I had it check for updates and it tells me my system is up to date, no 404 errors. But it didn't download or install anything and I have it set to notify me when updates are available. I know with Hardy I had an update notification pop up just about every day. But so far I haven't seen any notifications with Jaunty.

```
# deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release amd64 (20090420.1)]/ jaunty main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ jaunty restricted main
deb-src http://us.archive.ubuntu.com/ubuntu/ jaunty restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ jaunty-updates restricted main
deb-src http://us.archive.ubuntu.com/ubuntu/ jaunty-updates restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ jaunty universe
deb-src http://us.archive.ubuntu.com/ubuntu/ jaunty universe
deb http://us.archive.ubuntu.com/ubuntu/ jaunty-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ jaunty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ jaunty multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ jaunty multiverse
deb http://us.archive.ubuntu.com/ubuntu/ jaunty-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ jaunty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ jaunty-backports restricted universe multiverse main
# deb-src http://us.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu jaunty partner
deb-src http://archive.canonical.com/ubuntu jaunty partner

deb http://us.archive.ubuntu.com/ubuntu/ jaunty-security restricted main
deb-src http://us.archive.ubuntu.com/ubuntu/ jaunty-security restricted
deb http://us.archive.ubuntu.com/ubuntu/ jaunty-security universe
deb-src http://us.archive.ubuntu.com/ubuntu/ jaunty-security universe
deb http://us.archive.ubuntu.com/ubuntu/ jaunty-security multiverse
deb http://us.archive.ubuntu.com/ubuntu/ jaunty-proposed restricted multiverse universe main
deb-src http://us.archive.ubuntu.com/ubuntu/ jaunty-security multiverse


### ia32-apt-get entries ###

# deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release amd64 (20090420.1)]/ jaunty main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ jaunty restricted

## Major bug fix updates produced after the final release of the
## distribution.  
deb http://us.archive.ubuntu.com/ubuntu/ jaunty-updates restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team. 

## Uncomment the following two lines to add software from the 'backports'
## repository.  
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ jaunty-backports restricted multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. 
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu jaunty partner

deb http://us.archive.ubuntu.com/ubuntu/ jaunty-security restricted
deb http://us.archive.ubuntu.com/ubuntu/ jaunty-proposed main universe
```

---

### Post by albinootje on 2009-05-29
> **SpaceBison said:**
> 
```
Failed to fetch [http://archive.canonical.com/ubuntu/dists/jaunty-i386/partner/binary-amd64/Packages](http://archive.canonical.com/ubuntu/dists/jaunty-i386/partner/binary-amd64/Packages)  404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/jaunty-security-i386/main/binary-amd64/Packages](http://security.ubuntu.com/ubuntu/dists/jaunty-security-i386/main/binary-amd64/Packages)  404 Not Found
```

I'm actually not a 64-bit user, so ... I wonder whether I should have asked you where you found these urls ? 
I can only find one other webpage mentioning them :
[http://ubuntuforums.org/showthread.php?t=1119938](http://ubuntuforums.org/showthread.php?t=1119938)

---

### Post by fragos on 2009-05-29
There've been relatively few 9.04 updates compared to prior releases. IMHO speaks to the stability of 9.04.

---

### Post by SpaceBison on 2009-05-29
They came up in an error popup when I tried to have it check for updates manually using the gui under System > Administration > Update Manager.

---

### Post by SpaceBison on 2009-05-29
> **fragos said:**
> There've been relatively few 9.04 updates compared to prior releases. IMHO speaks to the stability of 9.04.
Ha, that could be it. I tried doing an update via the terminal, it looks like there is something wrong or missing with the 32 bit packages at the bottom.

```
matt@spacebison:~$ sudo apt-get update
[sudo] password for matt: 
apt-get: update
Get:1 http://us.archive.ubuntu.com jaunty Release.gpg [189B]
Ign http://us.archive.ubuntu.com jaunty/main Translation-en_US       
Ign http://us.archive.ubuntu.com jaunty/restricted Translation-en_US 
Get:2 http://archive.canonical.com jaunty Release.gpg [189B]         
Ign http://archive.canonical.com jaunty/partner Translation-en_US    
Get:3 http://security.ubuntu.com jaunty-security Release.gpg [189B]  
Ign http://security.ubuntu.com jaunty-security/main Translation-en_US
Ign http://us.archive.ubuntu.com jaunty/universe Translation-en_US   
Ign http://us.archive.ubuntu.com jaunty/multiverse Translation-en_US 
Get:4 http://us.archive.ubuntu.com jaunty-updates Release.gpg [189B] 
Ign http://us.archive.ubuntu.com jaunty-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com jaunty-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com jaunty-updates/universe Translation-en_US
Ign http://us.archive.ubuntu.com jaunty-updates/multiverse Translation-en_US
Get:5 http://us.archive.ubuntu.com jaunty-backports Release.gpg [189B]
Get:6 http://archive.canonical.com jaunty Release [7862B]                  
Ign http://security.ubuntu.com jaunty-security/restricted Translation-en_US
Ign http://security.ubuntu.com jaunty-security/universe Translation-en_US 
Ign http://security.ubuntu.com jaunty-security/multiverse Translation-en_US
Get:7 http://security.ubuntu.com jaunty-security Release [49.6kB]         
Ign http://us.archive.ubuntu.com jaunty-backports/main Translation-en_US       
Ign http://us.archive.ubuntu.com jaunty-backports/restricted Translation-en_US 
Ign http://us.archive.ubuntu.com jaunty-backports/universe Translation-en_US   
Ign http://us.archive.ubuntu.com jaunty-backports/multiverse Translation-en_US 
Get:8 http://us.archive.ubuntu.com jaunty-proposed Release.gpg [189B]          
Ign http://us.archive.ubuntu.com jaunty-proposed/restricted Translation-en_US  
Ign http://us.archive.ubuntu.com jaunty-proposed/main Translation-en_US        
Ign http://us.archive.ubuntu.com jaunty-proposed/multiverse Translation-en_US  
Ign http://us.archive.ubuntu.com jaunty-proposed/universe Translation-en_US
Get:9 http://us.archive.ubuntu.com jaunty Release [74.6kB]                  
Ign http://archive.canonical.com jaunty/partner Packages                       
Ign http://archive.canonical.com jaunty/partner Sources                        
Get:10 http://archive.canonical.com jaunty/partner Packages [1174B]
Get:11 http://us.archive.ubuntu.com jaunty-updates Release [49.6kB]            
Get:12 http://archive.canonical.com jaunty/partner Sources [610B]              
Get:13 http://security.ubuntu.com jaunty-security/main Packages [19.6kB]    
Get:14 http://us.archive.ubuntu.com jaunty-backports Release [49.6kB]
Get:15 http://us.archive.ubuntu.com jaunty-proposed Release [49.6kB]         
Get:16 http://security.ubuntu.com jaunty-security/restricted Packages [14B] 
Get:17 http://security.ubuntu.com jaunty-security/main Sources [6377B]       
Get:18 http://security.ubuntu.com jaunty-security/restricted Sources [14B]     
Get:19 http://security.ubuntu.com jaunty-security/universe Packages [7664B] 
Get:20 http://security.ubuntu.com jaunty-security/universe Sources [1187B]     
Get:21 http://security.ubuntu.com jaunty-security/multiverse Packages [14B]
Get:22 http://security.ubuntu.com jaunty-security/multiverse Sources [14B]
Get:23 http://us.archive.ubuntu.com jaunty/main Packages [1253kB]
Get:24 http://us.archive.ubuntu.com jaunty/restricted Packages [8848B]
Get:25 http://us.archive.ubuntu.com jaunty/main Sources [555kB]
Get:26 http://us.archive.ubuntu.com jaunty/restricted Sources [3156B]
Get:27 http://us.archive.ubuntu.com jaunty/universe Packages [4757kB]
Get:28 http://us.archive.ubuntu.com jaunty/universe Sources [2375kB]
Get:29 http://us.archive.ubuntu.com jaunty/multiverse Packages [197kB]         
Get:30 http://us.archive.ubuntu.com jaunty/multiverse Sources [107kB]          
Get:31 http://us.archive.ubuntu.com jaunty-updates/main Packages [52.1kB]      
Get:32 http://us.archive.ubuntu.com jaunty-updates/restricted Packages [14B]   
Get:33 http://us.archive.ubuntu.com jaunty-updates/main Sources [18.1kB]       
Get:34 http://us.archive.ubuntu.com jaunty-updates/restricted Sources [14B]    
Get:35 http://us.archive.ubuntu.com jaunty-updates/universe Packages [17.5kB]  
Get:36 http://us.archive.ubuntu.com jaunty-updates/universe Sources [4733B]    
Get:37 http://us.archive.ubuntu.com jaunty-updates/multiverse Packages [675B]  
Get:38 http://us.archive.ubuntu.com jaunty-updates/multiverse Sources [639B]   
Get:39 http://us.archive.ubuntu.com jaunty-backports/main Packages [4497B]     
Get:40 http://us.archive.ubuntu.com jaunty-backports/restricted Packages [14B] 
Get:41 http://us.archive.ubuntu.com jaunty-backports/universe Packages [6080B] 
Get:42 http://us.archive.ubuntu.com jaunty-backports/multiverse Packages [14B] 
Get:43 http://us.archive.ubuntu.com jaunty-proposed/restricted Packages [2093B]
Get:44 http://us.archive.ubuntu.com jaunty-proposed/main Packages [39.9kB]     
Get:45 http://us.archive.ubuntu.com jaunty-proposed/multiverse Packages [2257B]
Get:46 http://us.archive.ubuntu.com jaunty-proposed/universe Packages [10.9kB] 
Fetched 9733kB in 8s (1101kB/s)                                                
Reading package lists... Done
Get:1 http://archive.canonical.com jaunty Release.gpg [189B]
Ign http://archive.canonical.com jaunty/partner Translation-en_US    
Get:2 http://security.ubuntu.com jaunty-security Release.gpg [189B]  
Ign http://security.ubuntu.com jaunty-security/main Translation-en_US
Ign http://security.ubuntu.com jaunty-security/restricted Translation-en_US
Get:3 http://us.archive.ubuntu.com jaunty Release.gpg [189B]         
Ign http://us.archive.ubuntu.com jaunty/main Translation-en_US       
Ign http://us.archive.ubuntu.com jaunty/restricted Translation-en_US 
Get:4 http://archive.canonical.com jaunty Release [7862B]            
Ign http://security.ubuntu.com jaunty-security/universe Translation-en_US 
Ign http://security.ubuntu.com jaunty-security/multiverse Translation-en_US
Get:5 http://security.ubuntu.com jaunty-security Release [49.6kB]         
Ign http://us.archive.ubuntu.com jaunty/universe Translation-en_US            
Ign http://us.archive.ubuntu.com jaunty/multiverse Translation-en_US          
Get:6 http://us.archive.ubuntu.com jaunty-updates Release.gpg [189B]           
Ign http://us.archive.ubuntu.com jaunty-updates/main Translation-en_US         
Ign http://us.archive.ubuntu.com jaunty-updates/restricted Translation-en_US   
Ign http://us.archive.ubuntu.com jaunty-updates/universe Translation-en_US     
Ign http://us.archive.ubuntu.com jaunty-updates/multiverse Translation-en_US   
Get:7 http://us.archive.ubuntu.com jaunty-backports Release.gpg [189B]         
Ign http://us.archive.ubuntu.com jaunty-backports/main Translation-en_US       
Ign http://us.archive.ubuntu.com jaunty-backports/restricted Translation-en_US 
Ign http://us.archive.ubuntu.com jaunty-backports/universe Translation-en_US   
Ign http://us.archive.ubuntu.com jaunty-backports/multiverse Translation-en_US
Get:8 http://us.archive.ubuntu.com jaunty-proposed Release.gpg [189B]       
Ign http://us.archive.ubuntu.com jaunty-proposed/restricted Translation-en_US
Ign http://us.archive.ubuntu.com jaunty-proposed/main Translation-en_US     
Ign http://us.archive.ubuntu.com jaunty-proposed/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com jaunty-proposed/universe Translation-en_US 
Get:9 http://us.archive.ubuntu.com jaunty Release [74.6kB]                  
Ign http://archive.canonical.com jaunty/partner Packages                       
Ign http://archive.canonical.com jaunty/partner Sources                        
Get:10 http://security.ubuntu.com jaunty-security/main Packages [19.6kB]
Get:11 http://archive.canonical.com jaunty/partner Packages [29B]              
Get:12 http://us.archive.ubuntu.com jaunty-updates Release [49.6kB]            
Get:13 http://security.ubuntu.com jaunty-security/restricted Packages [14B]    
Get:14 http://security.ubuntu.com jaunty-security/main Sources [6377B]         
Get:15 http://security.ubuntu.com jaunty-security/restricted Sources [14B]     
Get:16 http://security.ubuntu.com jaunty-security/universe Packages [7241B]    
Get:17 http://security.ubuntu.com jaunty-security/universe Sources [1187B]     
Get:18 http://security.ubuntu.com jaunty-security/multiverse Packages [14B]    
Get:19 http://security.ubuntu.com jaunty-security/multiverse Sources [14B]     
Get:20 http://us.archive.ubuntu.com jaunty-backports Release [49.6kB]          
Get:21 http://archive.canonical.com jaunty/partner Sources [610B]           
Get:22 http://us.archive.ubuntu.com jaunty-proposed Release [49.6kB]        
Get:23 http://us.archive.ubuntu.com jaunty/main Packages [1251kB]
Get:24 http://us.archive.ubuntu.com jaunty/restricted Packages [8858B]
Get:25 http://us.archive.ubuntu.com jaunty/main Sources [555kB]
Get:26 http://us.archive.ubuntu.com jaunty/restricted Sources [3156B]
Get:27 http://us.archive.ubuntu.com jaunty/universe Packages [4732kB]
Get:28 http://us.archive.ubuntu.com jaunty/universe Sources [2375kB]           
Get:29 http://us.archive.ubuntu.com jaunty/multiverse Packages [189kB]         
Get:30 http://us.archive.ubuntu.com jaunty/multiverse Sources [107kB]          
Get:31 http://us.archive.ubuntu.com jaunty-updates/main Packages [51.7kB]      
Get:32 http://us.archive.ubuntu.com jaunty-updates/restricted Packages [14B]   
Get:33 http://us.archive.ubuntu.com jaunty-updates/main Sources [18.1kB]       
Get:34 http://us.archive.ubuntu.com jaunty-updates/restricted Sources [14B]    
Get:35 http://us.archive.ubuntu.com jaunty-updates/universe Packages [17.1kB]  
Get:36 http://us.archive.ubuntu.com jaunty-updates/universe Sources [4733B]    
Get:37 http://us.archive.ubuntu.com jaunty-updates/multiverse Packages [660B]  
Get:38 http://us.archive.ubuntu.com jaunty-updates/multiverse Sources [639B]   
Get:39 http://us.archive.ubuntu.com jaunty-backports/main Packages [4489B]     
Get:40 http://us.archive.ubuntu.com jaunty-backports/restricted Packages [14B] 
Get:41 http://us.archive.ubuntu.com jaunty-backports/universe Packages [6065B] 
Get:42 http://us.archive.ubuntu.com jaunty-backports/multiverse Packages [14B] 
Get:43 http://us.archive.ubuntu.com jaunty-proposed/restricted Packages [2076B]
Get:44 http://us.archive.ubuntu.com jaunty-proposed/main Packages [39.6kB]     
Get:45 http://us.archive.ubuntu.com jaunty-proposed/multiverse Packages [2241B]
Get:46 http://us.archive.ubuntu.com jaunty-proposed/universe Packages [10.8kB] 
Fetched 9696kB in 11s (878kB/s)                                                
Reading package lists... Done
/usr/bin/apt-get: 101: cannot open /var/lib/apt/foreign/lists/archive.canonical.com_ubuntu_dists_jaunty_main_binary-i386_Packages: No such file
/usr/bin/apt-get: 101: cannot open /var/lib/apt/foreign/lists/archive.canonical.com_ubuntu_dists_jaunty_main_binary-i386_Packages: No such file
Ignoring archive.canonical.com_ubuntu_dists_jaunty_partner_source_Sources
Ignoring security.ubuntu.com_ubuntu_dists_jaunty-security_main_source_Sources
mangle: ia32-libs-tools/mangle.cc:402: void mangle(Archlist&, Renamelist&): Assertion `buf_used > 1' failed.
Aborted

```

---

