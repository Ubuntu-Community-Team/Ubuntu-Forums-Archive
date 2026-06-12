---
title: "when i run the synaptic packages i only see the programs that i installed ? help"
date: 2007-08-30
forum: Desktop Environments
---

### Post by tropcky on 2007-08-30
[IMG][[img]http://www.upload2world.com/pic38/upload2world_600b4.png[/img]](http://www.upload2world.com)[/IMG]

so as u see its only the programs that already installed plez help i cant  dawnload any thing now

---

### Post by rsambuca on 2007-08-30
Did you recently search your installed packages?  Go to your "Settings" Filters and play around in there.  Uncheck the installed files.

---

### Post by tropcky on 2007-08-30
i trayed but its the same nothing changes

---

### Post by rsambuca on 2007-08-30
post your /etc/apt/sources.list

---

### Post by tropcky on 2007-08-30
sorry but how can do that 
i am new on linnx

---

### Post by rsambuca on 2007-08-30
No problem.  Open a terminal (Applications -> Accessories -> Terminal) at the prompt, cut and paste this into the terminal```
cat /etc/apt/sources.list
```then cut and paste the output here.

---

### Post by tropcky on 2007-08-30
here it is 
tropcky@tropcky-linux:~$ cat /etc/apt/sources.list
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://ubuntu.supp.name/ubuntu/](http://ubuntu.supp.name/ubuntu/) feisty main restricted
deb-src [http://ubuntu.supp.name/ubuntu/](http://ubuntu.supp.name/ubuntu/) feisty restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ubuntu.supp.name/ubuntu/](http://ubuntu.supp.name/ubuntu/) feisty-updates main restricted
deb-src [http://ubuntu.supp.name/ubuntu/](http://ubuntu.supp.name/ubuntu/) feisty-updates main restricted #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://ubuntu.supp.name/ubuntu/](http://ubuntu.supp.name/ubuntu/) feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://ubuntu.supp.name/ubuntu/](http://ubuntu.supp.name/ubuntu/) feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://eg.archive.ubuntu.com/ubuntu/](http://eg.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://eg.archive.ubuntu.com/ubuntu/](http://eg.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://ubuntu.supp.name/ubuntu/](http://ubuntu.supp.name/ubuntu/) feisty-security main restricted
deb-src [http://ubuntu.supp.name/ubuntu/](http://ubuntu.supp.name/ubuntu/) feisty-security restricted main multiverse universe #Added by software-properties
deb [http://ubuntu.supp.name/ubuntu/](http://ubuntu.supp.name/ubuntu/) feisty-security universe
deb [http://ubuntu.supp.name/ubuntu/](http://ubuntu.supp.name/ubuntu/) feisty-security multiverse
tropcky@tropcky-linux:~$

---

### Post by rsambuca on 2007-08-30
What happens when you type

sudo apt-get update

into a terminal.  Do you see it updating from your repositories?

---

### Post by tropcky on 2007-08-30
u gonna love that 
Ign [http://ubuntu.supp.name](http://ubuntu.supp.name) feisty Release.gpg
Ign [http://ubuntu.supp.name](http://ubuntu.supp.name) feisty/main Translation-en_US
Ign [http://ubuntu.supp.name](http://ubuntu.supp.name) feisty/restricted Translation-en_US
Ign [http://ubuntu.supp.name](http://ubuntu.supp.name) feisty/universe Translation-en_US
Ign [http://ubuntu.supp.name](http://ubuntu.supp.name) feisty/multiverse Translation-en_US
Ign [http://ubuntu.supp.name](http://ubuntu.supp.name) feisty-updates Release.gpg
Ign [http://ubuntu.supp.name](http://ubuntu.supp.name) feisty-updates/main Translation-en_US
Ign [http://ubuntu.supp.name](http://ubuntu.supp.name) feisty-updates/restricted Translation-en_US
Ign [http://ubuntu.supp.name](http://ubuntu.supp.name) feisty-security Release.gpg
Ign [http://ubuntu.supp.name](http://ubuntu.supp.name) feisty-security/main Translation-en_US
Ign [http://ubuntu.supp.name](http://ubuntu.supp.name) feisty-security/restricted Translation-en_US
Ign [http://ubuntu.supp.name](http://ubuntu.supp.name) feisty-security/universe Translation-en_US
Ign [http://ubuntu.supp.name](http://ubuntu.supp.name) feisty-security/multiverse Translation-en_US
Ign [http://ubuntu.supp.name](http://ubuntu.supp.name) feisty Release
Ign [http://ubuntu.supp.name](http://ubuntu.supp.name) feisty-updates Release
Ign [http://ubuntu.supp.name](http://ubuntu.supp.name) feisty-security Release
Ign [http://ubuntu.supp.name](http://ubuntu.supp.name) feisty/main Packages
Ign [http://ubuntu.supp.name](http://ubuntu.supp.name) feisty/restricted Packages
Ign [http://ubuntu.supp.name](http://ubuntu.supp.name) feisty/restricted Sources
Ign [http://ubuntu.supp.name](http://ubuntu.supp.name) feisty/main Sources
Ign [http://ubuntu.supp.name](http://ubuntu.supp.name) feisty/multiverse Sources
Ign [http://ubuntu.supp.name](http://ubuntu.supp.name) feisty/universe Sources
Ign [http://ubuntu.supp.name](http://ubuntu.supp.name) feisty/universe Packages
Ign [http://ubuntu.supp.name](http://ubuntu.supp.name) feisty/multiverse Packages
Ign [http://ubuntu.supp.name](http://ubuntu.supp.name) feisty-updates/main Packages
Ign [http://ubuntu.supp.name](http://ubuntu.supp.name) feisty-updates/restricted Packages
Ign [http://ubuntu.supp.name](http://ubuntu.supp.name) feisty-updates/main Sources
Ign [http://ubuntu.supp.name](http://ubuntu.supp.name) feisty-updates/restricted Sources
Ign [http://ubuntu.supp.name](http://ubuntu.supp.name) feisty-security/main Packages
Ign [http://ubuntu.supp.name](http://ubuntu.supp.name) feisty-security/restricted Packages
Ign [http://ubuntu.supp.name](http://ubuntu.supp.name) feisty-security/restricted Sources
Ign [http://ubuntu.supp.name](http://ubuntu.supp.name) feisty-security/main Sources
Ign [http://ubuntu.supp.name](http://ubuntu.supp.name) feisty-security/multiverse Sources
Ign [http://ubuntu.supp.name](http://ubuntu.supp.name) feisty-security/universe Sources
Ign [http://ubuntu.supp.name](http://ubuntu.supp.name) feisty-security/universe Packages
Ign [http://ubuntu.supp.name](http://ubuntu.supp.name) feisty-security/multiverse Packages
Err [http://ubuntu.supp.name](http://ubuntu.supp.name) feisty/main Packages
  404 Not Found
Err [http://ubuntu.supp.name](http://ubuntu.supp.name) feisty/restricted Packages
  404 Not Found
Err [http://ubuntu.supp.name](http://ubuntu.supp.name) feisty/restricted Sources
  404 Not Found
Err [http://ubuntu.supp.name](http://ubuntu.supp.name) feisty/main Sources
  404 Not Found
Err [http://ubuntu.supp.name](http://ubuntu.supp.name) feisty/multiverse Sources
  404 Not Found
Err [http://ubuntu.supp.name](http://ubuntu.supp.name) feisty/universe Sources
  404 Not Found
Err [http://ubuntu.supp.name](http://ubuntu.supp.name) feisty/universe Packages
  404 Not Found
Err [http://ubuntu.supp.name](http://ubuntu.supp.name) feisty/multiverse Packages
  404 Not Found
Err [http://ubuntu.supp.name](http://ubuntu.supp.name) feisty-updates/main Packages
  404 Not Found
Err [http://ubuntu.supp.name](http://ubuntu.supp.name) feisty-updates/restricted Packages
  404 Not Found
Err [http://ubuntu.supp.name](http://ubuntu.supp.name) feisty-updates/main Sources
  404 Not Found
Err [http://ubuntu.supp.name](http://ubuntu.supp.name) feisty-updates/restricted Sources
  404 Not Found
Err [http://ubuntu.supp.name](http://ubuntu.supp.name) feisty-security/main Packages
  404 Not Found
Err [http://ubuntu.supp.name](http://ubuntu.supp.name) feisty-security/restricted Packages
  404 Not Found
Err [http://ubuntu.supp.name](http://ubuntu.supp.name) feisty-security/restricted Sources
  404 Not Found
Err [http://ubuntu.supp.name](http://ubuntu.supp.name) feisty-security/main Sources
  404 Not Found
Err [http://ubuntu.supp.name](http://ubuntu.supp.name) feisty-security/multiverse Sources
  404 Not Found
Err [http://ubuntu.supp.name](http://ubuntu.supp.name) feisty-security/universe Sources
  404 Not Found
Err [http://ubuntu.supp.name](http://ubuntu.supp.name) feisty-security/universe Packages
  404 Not Found
Err [http://ubuntu.supp.name](http://ubuntu.supp.name) feisty-security/multiverse Packages
  404 Not Found
Failed to fetch [http://ubuntu.supp.name/ubuntu/dists/feisty/main/binary-i386/Packages.gz](http://ubuntu.supp.name/ubuntu/dists/feisty/main/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://ubuntu.supp.name/ubuntu/dists/feisty/restricted/binary-i386/Packages.gz](http://ubuntu.supp.name/ubuntu/dists/feisty/restricted/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://ubuntu.supp.name/ubuntu/dists/feisty/restricted/source/Sources.gz](http://ubuntu.supp.name/ubuntu/dists/feisty/restricted/source/Sources.gz)  404 Not Found
Failed to fetch [http://ubuntu.supp.name/ubuntu/dists/feisty/main/source/Sources.gz](http://ubuntu.supp.name/ubuntu/dists/feisty/main/source/Sources.gz)  404 Not Found
Failed to fetch [http://ubuntu.supp.name/ubuntu/dists/feisty/multiverse/source/Sources.gz](http://ubuntu.supp.name/ubuntu/dists/feisty/multiverse/source/Sources.gz)  404 Not Found
Failed to fetch [http://ubuntu.supp.name/ubuntu/dists/feisty/universe/source/Sources.gz](http://ubuntu.supp.name/ubuntu/dists/feisty/universe/source/Sources.gz)  404 Not Found
Failed to fetch [http://ubuntu.supp.name/ubuntu/dists/feisty/universe/binary-i386/Packages.gz](http://ubuntu.supp.name/ubuntu/dists/feisty/universe/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://ubuntu.supp.name/ubuntu/dists/feisty/multiverse/binary-i386/Packages.gz](http://ubuntu.supp.name/ubuntu/dists/feisty/multiverse/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://ubuntu.supp.name/ubuntu/dists/feisty-updates/main/binary-i386/Packages.gz](http://ubuntu.supp.name/ubuntu/dists/feisty-updates/main/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://ubuntu.supp.name/ubuntu/dists/feisty-updates/restricted/binary-i386/Packages.gz](http://ubuntu.supp.name/ubuntu/dists/feisty-updates/restricted/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://ubuntu.supp.name/ubuntu/dists/feisty-updates/main/source/Sources.gz](http://ubuntu.supp.name/ubuntu/dists/feisty-updates/main/source/Sources.gz)  404 Not Found
Failed to fetch [http://ubuntu.supp.name/ubuntu/dists/feisty-updates/restricted/source/Sources.gz](http://ubuntu.supp.name/ubuntu/dists/feisty-updates/restricted/source/Sources.gz)  404 Not Found
Failed to fetch [http://ubuntu.supp.name/ubuntu/dists/feisty-security/main/binary-i386/Packages.gz](http://ubuntu.supp.name/ubuntu/dists/feisty-security/main/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://ubuntu.supp.name/ubuntu/dists/feisty-security/restricted/binary-i386/Packages.gz](http://ubuntu.supp.name/ubuntu/dists/feisty-security/restricted/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://ubuntu.supp.name/ubuntu/dists/feisty-security/restricted/source/Sources.gz](http://ubuntu.supp.name/ubuntu/dists/feisty-security/restricted/source/Sources.gz)  404 Not Found
Failed to fetch [http://ubuntu.supp.name/ubuntu/dists/feisty-security/main/source/Sources.gz](http://ubuntu.supp.name/ubuntu/dists/feisty-security/main/source/Sources.gz)  404 Not Found
Failed to fetch [http://ubuntu.supp.name/ubuntu/dists/feisty-security/multiverse/source/Sources.gz](http://ubuntu.supp.name/ubuntu/dists/feisty-security/multiverse/source/Sources.gz)  404 Not Found
Failed to fetch [http://ubuntu.supp.name/ubuntu/dists/feisty-security/universe/source/Sources.gz](http://ubuntu.supp.name/ubuntu/dists/feisty-security/universe/source/Sources.gz)  404 Not Found
Failed to fetch [http://ubuntu.supp.name/ubuntu/dists/feisty-security/universe/binary-i386/Packages.gz](http://ubuntu.supp.name/ubuntu/dists/feisty-security/universe/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://ubuntu.supp.name/ubuntu/dists/feisty-security/multiverse/binary-i386/Packages.gz](http://ubuntu.supp.name/ubuntu/dists/feisty-security/multiverse/binary-i386/Packages.gz)  404 Not Found
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.
tropcky@tropcky-linux:~$

---

### Post by rsambuca on 2007-08-30
The servers holding your repositories are down.  If you want, you can cut and paste this into your sources.list - I know they work.

```
gksudo gedit /etc/apt/sources.list
```

Paste this into it, save it, then reload your synaptic.```
# 
# ## UBUNTU REPOSITORIES
## -------------------
##
## Feisty (Ubuntu 7.04)
deb http://archive.ubuntu.com/ubuntu feisty main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu feisty main restricted universe multiverse
##
## Proposed Updates
deb http://archive.ubuntu.com/ubuntu feisty-proposed main restricted universe multiverse
##
## Bug Fixes
deb http://archive.ubuntu.com/ubuntu feisty-updates main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu feisty-updates main restricted universe multiverse
##
## Security Updates
deb http://security.ubuntu.com/ubuntu feisty-security main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu feisty-security main restricted universe multiverse
##
## Backports
deb http://archive.ubuntu.com/ubuntu feisty-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu feisty-backports main restricted universe multiverse

## OTHER REPOSITORIES
## ------------------
##
## Canonical (RealPlayer10, Opera, DesktopSecure etc...) 
deb http://archive.canonical.com/ubuntu feisty-commercial main
##
## Medibuntu (Codecs and extra applications)
deb http://medibuntu.sos-sts.com/repo/ feisty free non-free
```

---

### Post by tropcky on 2007-08-30
will it works thank but  it gives some erors  right after i relod it 
the ferst one :
Could not download all repository indexes

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.
[http://ubuntu.supp.name/ubuntu/dists/feisty/main/binary-i386/Packages.gz:](http://ubuntu.supp.name/ubuntu/dists/feisty/main/binary-i386/Packages.gz:) 404 Not Found
[http://ubuntu.supp.name/ubuntu/dists/feisty/restricted/binary-i386/Packages.gz:](http://ubuntu.supp.name/ubuntu/dists/feisty/restricted/binary-i386/Packages.gz:) 404 Not Found
[http://ubuntu.supp.name/ubuntu/dists/feisty/restricted/source/Sources.gz:](http://ubuntu.supp.name/ubuntu/dists/feisty/restricted/source/Sources.gz:) 404 Not Found
[http://ubuntu.supp.name/ubuntu/dists/feisty/main/source/Sources.gz:](http://ubuntu.supp.name/ubuntu/dists/feisty/main/source/Sources.gz:) 404 Not Found
[http://ubuntu.supp.name/ubuntu/dists/feisty/multiverse/source/Sources.gz:](http://ubuntu.supp.name/ubuntu/dists/feisty/multiverse/source/Sources.gz:) 404 Not Found
[http://ubuntu.supp.name/ubuntu/dists/feisty/universe/source/Sources.gz:](http://ubuntu.supp.name/ubuntu/dists/feisty/universe/source/Sources.gz:) 404 Not Found
[http://ubuntu.supp.name/ubuntu/dists/feisty/universe/binary-i386/Packages.gz:](http://ubuntu.supp.name/ubuntu/dists/feisty/universe/binary-i386/Packages.gz:) 404 Not Found
[http://ubuntu.supp.name/ubuntu/dists/feisty/multiverse/binary-i386/Packages.gz:](http://ubuntu.supp.name/ubuntu/dists/feisty/multiverse/binary-i386/Packages.gz:) 404 Not Found
[http://ubuntu.supp.name/ubuntu/dists/feisty-updates/main/binary-i386/Packages.gz:](http://ubuntu.supp.name/ubuntu/dists/feisty-updates/main/binary-i386/Packages.gz:) 404 Not Found
[http://ubuntu.supp.name/ubuntu/dists/feisty-updates/restricted/binary-i386/Packages.gz:](http://ubuntu.supp.name/ubuntu/dists/feisty-updates/restricted/binary-i386/Packages.gz:) 404 Not Found
[http://ubuntu.supp.name/ubuntu/dists/feisty-updates/main/source/Sources.gz:](http://ubuntu.supp.name/ubuntu/dists/feisty-updates/main/source/Sources.gz:) 404 Not Found
[http://ubuntu.supp.name/ubuntu/dists/feisty-updates/restricted/source/Sources.gz:](http://ubuntu.supp.name/ubuntu/dists/feisty-updates/restricted/source/Sources.gz:) 404 Not Found
[http://ubuntu.supp.name/ubuntu/dists/feisty-security/main/binary-i386/Packages.gz:](http://ubuntu.supp.name/ubuntu/dists/feisty-security/main/binary-i386/Packages.gz:) 404 Not Found
[http://ubuntu.supp.name/ubuntu/dists/feisty-security/restricted/binary-i386/Packages.gz:](http://ubuntu.supp.name/ubuntu/dists/feisty-security/restricted/binary-i386/Packages.gz:) 404 Not Found
[http://ubuntu.supp.name/ubuntu/dists/feisty-security/restricted/source/Sources.gz:](http://ubuntu.supp.name/ubuntu/dists/feisty-security/restricted/source/Sources.gz:) 404 Not Found
[http://ubuntu.supp.name/ubuntu/dists/feisty-security/main/source/Sources.gz:](http://ubuntu.supp.name/ubuntu/dists/feisty-security/main/source/Sources.gz:) 404 Not Found
[http://medibuntu.sos-sts.com/repo/dists/feisty/non-fre/binary-i386/Packages.gz:](http://medibuntu.sos-sts.com/repo/dists/feisty/non-fre/binary-i386/Packages.gz:) 404 Not Found
[http://ubuntu.supp.name/ubuntu/dists/feisty-security/multiverse/source/Sources.gz:](http://ubuntu.supp.name/ubuntu/dists/feisty-security/multiverse/source/Sources.gz:) 404 Not Found
[http://ubuntu.supp.name/ubuntu/dists/feisty-security/universe/source/Sources.gz:](http://ubuntu.supp.name/ubuntu/dists/feisty-security/universe/source/Sources.gz:) 404 Not Found
[http://ubuntu.supp.name/ubuntu/dists/feisty-security/universe/binary-i386/Packages.gz:](http://ubuntu.supp.name/ubuntu/dists/feisty-security/universe/binary-i386/Packages.gz:) 404 Not Found
[http://ubuntu.supp.name/ubuntu/dists/feisty-security/multiverse/binary-i386/Packages.gz:](http://ubuntu.supp.name/ubuntu/dists/feisty-security/multiverse/binary-i386/Packages.gz:) 404 Not Found


and the sacand one :
An error occured

The following details are provided:
W: GPG error: [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783

---

### Post by Steveway on 2007-08-30
Do you even have a connection to the internet? Or are you behind a proxy?

---

### Post by tropcky on 2007-08-30
no man i have a dsl connection

---

### Post by rsambuca on 2007-08-31
Have you tried synaptic yet since adding the repositories?

---

### Post by the yawner on 2007-08-31
It seems the only valid site on your list is [http://eg.archive.ubuntu.com/ubuntu/](http://eg.archive.ubuntu.com/ubuntu/).

Please try the following:
- System>Administration>Software Sources
- On the Ubuntu Software tab, on parameter *Download from*, select Main server.

---

### Post by tropcky on 2007-08-31
i did man i tray to chos the main server but it just make more bad 
and ya rsambuca  i trayed the synaptic after i did what u told  but it gevs me3 some err  and i posted 2 u    maby u didnt see it

---

### Post by tropcky on 2007-08-31
and here when i tray 2 update 
look at thes 
tropcky@tropcky-linux:~$ sudo apt-get update
Get:1 [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty Release.gpg [189B]
Get:2 [http://archive.canonical.com](http://archive.canonical.com) feisty-commercial Release.gpg [191B]
Ign [http://archive.canonical.com](http://archive.canonical.com) feisty-commercial/main Translation-en_US
Ign [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty/free Translation-en_US       
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty Release.gpg [191B]            
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/main Translation-en_US                 
Ign [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty/non-fre Translation-en_US
Hit [http://archive.canonical.com](http://archive.canonical.com) feisty-commercial Release           
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/restricted Translation-en_US    
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/universe Translation-en_US    
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/multiverse Translation-en_US  
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/restricted Translation-en_US  
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/multiverse Translation-en_US  
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates Release.gpg [191B]  
Hit [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty Release                    
Err [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty Release                    
  
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/universe Translation-en_US
Hit [http://archive.canonical.com](http://archive.canonical.com) feisty-commercial/main Packages     
Get:5 [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty Release [2195B]            
Ign [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty Release      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/multiverse Translation-en_US
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security Release.gpg [191B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/multiverse Translation-en_US
Ign [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty/free Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/multiverse Translation-en_US
Get:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-proposed Release.gpg [191B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-proposed/main Translation-en_US
Ign [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty/non-fre Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-proposed/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-proposed/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-proposed/multiverse Translation-en_US
Get:8 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports Release.gpg [191B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/restricted Translation-en_US
Hit [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty/free Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/multiverse Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty Release   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates Release
Err [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty/non-fre Packages            
  404 Not Found
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-proposed Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/multiverse Sources
Get:9 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-proposed/main Packages [65.9kB]
Get:10 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-proposed/restricted Packages [14B]
Get:11 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-proposed/universe Packages [14.9kB]
Get:12 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-proposed/multiverse Packages [8593B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/multiverse Sources
Fetched 2394B in 4s (535B/s)
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/non-fre/binary-i386/Packages.gz](http://medibuntu.sos-sts.com/repo/dists/feisty/non-fre/binary-i386/Packages.gz)  404 Not Found
Reading package lists... Done
W: GPG error: [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
W: Duplicate sources.list entry [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_feisty_restricted_binary-i386_Packages)
W: Duplicate sources.list entry [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_feisty_multiverse_binary-i386_Packages)
W: Duplicate sources.list entry [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_feisty-updates_restricted_binary-i386_Packages)
W: Duplicate sources.list entry [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_feisty-security_restricted_binary-i386_Packages)
W: Duplicate sources.list entry [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_feisty-security_multiverse_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.
tropcky@tropcky-linux:~$

---

### Post by the yawner on 2007-08-31
Well, you're hitting the the main server just fine. So let's break it down a bit:

> **Ign** [http://archive.canonical.com](http://archive.canonical.com) feisty-commercial/main Translation-en_US
These are ignored repositories. I'm guessing you're using a different localization so it's not that integral. Notice most of the lines are just US en (english) translations.

> Err [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty/**non-fre** Packages
404 Not Found

According to Medibuntu, it should be:
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) feisty free non-**free**.

> W: GPG error: [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
It's basically an authentication for the Medibuntu repo to be sure you're downloading from the correct site. On terminal, type:
*wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add - && sudo apt-get update*
to get the GPG key.

> W: Duplicate sources.list entry [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dist s_feisty_restricted_binary-i386_Packages)
Could you repost your current sources list? It seems there are a couple of duplicated entries.
*sudo gedit /etc/apt/sources.list*

---

### Post by tropcky on 2007-08-31
here it is man 
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-updates main restricted #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://eg.archive.ubuntu.com/ubuntu/](http://eg.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://eg.archive.ubuntu.com/ubuntu/](http://eg.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-security main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-security restricted main multiverse universe #Added by software-properties
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-security universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-security multiverse
# 
# ## UBUNTU REPOSITORIES
## -------------------
##
## Feisty (Ubuntu 7.04)
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty restricted multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty restricted multiverse
##
## Proposed Updates
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-proposed main restricted universe multiverse
##
## Bug Fixes
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-updates restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-updates restricted universe multiverse
##
## Security Updates
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-security restricted multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-security restricted multiverse
##
## Backports
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

## OTHER REPOSITORIES
## ------------------
##
## Canonical (RealPlayer10, Opera, DesktopSecure etc...) 
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) feisty-commercial main
##
## Medibuntu (Codecs and extra applications)
deb [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) feisty free non-fre

---

