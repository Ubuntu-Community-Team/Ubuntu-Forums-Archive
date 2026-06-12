---
title: "apt-get update error"
date: 2009-06-06
forum: General Help
---

### Post by colau on 2009-06-06
Last part
```

Fetched 578B in 6s (89B/s)                                                                                                  
Reading package lists... Done
W: GPG error: http://packages.medibuntu.org jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: http://archive.ubuntu.com jaunty-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: GPG error: http://archive.ubuntu.com jaunty-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/jaunty-updates/Release  

W: Some index files failed to download, they have been ignored, or old ones used instead.
W: You may want to run apt-get update to correct these problems

```

cat /etc/apt/sources.list
```

# deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)]/ jaunty main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://backintime.le-web.org/repository stable main

deb http://archive.ubuntu.com/ubuntu/ jaunty main restricted
deb-src http://archive.ubuntu.com/ubuntu/ jaunty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu/ jaunty-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu/ jaunty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu/ jaunty universe
deb-src http://archive.ubuntu.com/ubuntu/ jaunty universe
deb http://archive.ubuntu.com/ubuntu/ jaunty-updates universe
deb-src http://archive.ubuntu.com/ubuntu/ jaunty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://archive.ubuntu.com/ubuntu/ jaunty multiverse
deb-src http://archive.ubuntu.com/ubuntu/ jaunty multiverse
deb http://archive.ubuntu.com/ubuntu/ jaunty-updates multiverse
deb-src http://archive.ubuntu.com/ubuntu/ jaunty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://bd.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse
# deb-src http://bd.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu jaunty partner
# deb-src http://archive.canonical.com/ubuntu jaunty partner

deb http://archive.ubuntu.com/ubuntu/ jaunty-security main restricted
deb-src http://archive.ubuntu.com/ubuntu/ jaunty-security main restricted
deb http://archive.ubuntu.com/ubuntu/ jaunty-security universe
deb-src http://archive.ubuntu.com/ubuntu/ jaunty-security universe
deb http://archive.ubuntu.com/ubuntu/ jaunty-security multiverse
deb-src http://archive.ubuntu.com/ubuntu/ jaunty-security multiverse

```

---

### Post by DeMus on 2009-06-06
> **colau said:**
> Last part
```

Fetched 578B in 6s (89B/s)                                                                                                  
Reading package lists... Done
W: GPG error: http://packages.medibuntu.org jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: http://archive.ubuntu.com jaunty-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: GPG error: http://archive.ubuntu.com jaunty-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/jaunty-updates/Release  

W: Some index files failed to download, they have been ignored, or old ones used instead.
W: You may want to run apt-get update to correct these problems

```

This looks like you have added repositories without the proper gpg key, so these new repositories are treated as unsafe and are not included in the update.
What you need to do when you want to use these repositories is to get the right gpg key.

---

### Post by colau on 2009-06-06
> **DeMus said:**
> This looks like you have added repositories without the proper gpg key, so these new repositories are treated as unsafe and are not included in the update.
What you need to do when you want to use these repositories is to get the right gpg key.
How can I get rid of this messages?

---

### Post by DeMus on 2009-06-06
> **colau said:**
> How can I get rid of this messages?

Either add the right gpg key, or when not possible remove the extra repositories which cause these errors.

---

### Post by DeMus on 2009-06-06
I see you write a new problem (top panel causing an error). Does that mean this problem is solved now? If so, please write it here so others can benefit from it.

---

### Post by colau on 2009-06-06
> **DeMus said:**
> I see you write a new problem (top panel causing an error). Does that mean this problem is solved now? If so, please write it here so others can benefit from it.
I am trying to add right gpg-key but how to do that?

---

### Post by DeMus on 2009-06-06
> **colau said:**
> I am trying to add right gpg-key but how to do that?

These keys normally are found on the website you also found the repository. When you have downloaded the gpg file, you have to do this:
open Synaptic
choose menu Settings and choose repositories
in the new window you choose the tab called Authentication and import the gpg file.
When closing the window you get a message things have changed and you need to reload. This button is in Synaptic all the way to the left.
Then the repository is also included in the list of repositories and you will have the possibility to install packages from there.

---

### Post by plucky on 2009-06-06
[Medibuntu](https://help.ubuntu.com/community/Medibuntu)

What is ```
deb http://backintime.le-web.org/repository stable main
``` this repository? Try putting a # in front of that line and then post output of ```
sudo apt-get update
```


Good Luck

---

### Post by DeMus on 2009-06-06
Try this in a terminal:

wget -q [http://medibuntu.sos-sts.com/repo/medibuntu-key.gpg](http://medibuntu.sos-sts.com/repo/medibuntu-key.gpg) -O- | sudo apt-key add -

I found it in:
[http://ubuntuforums.org/showthread.php?t=318519]("http://ubuntuforums.org/showthread.php?t=318519")

---

### Post by colau on 2009-06-07
> **DeMus said:**
> Try this in a terminal:

wget -q [http://medibuntu.sos-sts.com/repo/medibuntu-key.gpg](http://medibuntu.sos-sts.com/repo/medibuntu-key.gpg) -O- | sudo apt-key add -

I found it in:
[http://ubuntuforums.org/showthread.php?t=318519]("http://ubuntuforums.org/showthread.php?t=318519")

Medibuntu problem is solved.
But this is the latest problem after apt-get update.
```

Fetched 570B in 4s (129B/s)                          
Reading package lists... Done
W: GPG error: http://archive.ubuntu.com jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5
W: GPG error: http://archive.ubuntu.com jaunty-updates Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5
W: GPG error: http://archive.ubuntu.com jaunty-security Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5
W: You may want to run apt-get update to correct these problems

```

---

### Post by chemtamer on 2009-07-03
i found this error
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty Release.gpg
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/multiverse Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/universe Translation-en_US
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates Release.gpg [189B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/multiverse Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/universe Translation-en_US
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-security Release.gpg [189B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-security/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-security/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-security/multiverse Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-security/universe Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates Release                       
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates Release                       
  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-security Release                      
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-security Release                      
  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/main Packages                         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/universe Packages
Fetched 378B in 5s (70B/s)
Reading package lists... Done
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/jaunty-updates/Release](http://archive.ubuntu.com/ubuntu/dists/jaunty-updates/Release)  

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/jaunty-security/Release](http://archive.ubuntu.com/ubuntu/dists/jaunty-security/Release)  

W: Some index files failed to download, they have been ignored, or old ones used instead.
W: You may want to run apt-get update to correct these problems

---

