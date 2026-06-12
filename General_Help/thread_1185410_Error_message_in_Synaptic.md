---
title: "Error message in Synaptic"
date: 2009-06-12
forum: General Help
---

### Post by samebchase on 2009-06-12
Hi, 

I'm still getting used to the newly installed Ubuntu 9.04. Whenever I click on the reload button in Synaptic, the following error message comes up:

W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 43C0AFF0D7FAE680
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 43C0AFF0D7FAE680
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 9F10E6AE9317790E

I request someone to please tell me how this can be fixed.

Thanks,
Samuel

---

### Post by _Purple_ on 2009-06-12
Can you post the content of 
```
gksudo gedit /etc/apt/sources.list
```

---

### Post by michy99 on 2009-06-12
When a repository in this list has a GPG key, you may need to add that to the APT trusted keys. You can do this with the following commands (replace KEY with the key ID)```
gpg --keyserver subkeys.pgp.net --recv KEY
gpg --export --armor KEY | sudo apt-key add -
```In your case the key IDs are :
43C0AFF0D7FAE680
9F10E6AE9317790E

Do the above commands for each key, and then```
sudo apt-get update
```

---

### Post by colau on 2009-06-12
> **michy99 said:**
> When a repository in this list has a GPG key, you may need to add that to the APT trusted keys. You can do this with the following commands (replace KEY with the key ID)```
gpg --keyserver subkeys.pgp.net --recv KEY
      gpg --export --armor KEY | sudo apt-key add -
```In your case the key IDs are :
43C0AFF0D7FAE680
9F10E6AE9317790E

Do the above commands for each key, and then```
sudo apt-get update
```

I have similar problem too with sudo aptitude update
```

W: GPG error: http://packages.medibuntu.org jaunty Release: The following signatures were invalid: BADSIG 2EBC26B60C5A2783 Medibuntu Packaging Team <admin@lists.medibuntu.org>
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: http://archive.ubuntu.com jaunty-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

```

What to do?

---

### Post by _Purple_ on 2009-06-12
> **colau said:**
> I have similar problem too with sudo aptitude update
```

W: GPG error: http://packages.medibuntu.org jaunty Release: The following signatures were invalid: BADSIG 2EBC26B60C5A2783 Medibuntu Packaging Team <admin@lists.medibuntu.org>
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: http://archive.ubuntu.com jaunty-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

```

What to do?

Run in terminal
```
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update 
```

---

### Post by colau on 2009-06-12
> **_Purple_ said:**
> Run in terminal
```
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update 
```
Still problem
```

W: GPG error: http://packages.medibuntu.org jaunty Release: The following signatures were invalid: BADSIG 2EBC26B60C5A2783 Medibuntu Packaging Team <admin@lists.medibuntu.org>
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: http://archive.ubuntu.com jaunty-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/jaunty-updates/Release  

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/jaunty-security/universe/binary-i386/Packages.bz2  Hash Sum mismatch

W: Some index files failed to download, they have been ignored, or old ones used instead.
W: You may want to run apt-get update to correct these problems

```

---

### Post by _Purple_ on 2009-06-12
> **colau said:**
> Still problem
```

W: GPG error: http://packages.medibuntu.org jaunty Release: The following signatures were invalid: BADSIG 2EBC26B60C5A2783 Medibuntu Packaging Team <admin@lists.medibuntu.org>
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: http://archive.ubuntu.com jaunty-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/jaunty-updates/Release  

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/jaunty-security/universe/binary-i386/Packages.bz2  Hash Sum mismatch

W: Some index files failed to download, they have been ignored, or old ones used instead.
W: You may want to run apt-get update to correct these problems

```

Can you post the content of sources.list?

---

### Post by colau on 2009-06-12
> **_Purple_ said:**
> Can you post the content of sources.list?
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
deb http://archive.canonical.com/ubuntu jaunty partner
deb-src http://archive.canonical.com/ubuntu jaunty partner

deb http://archive.ubuntu.com/ubuntu/ jaunty-security main restricted
deb-src http://archive.ubuntu.com/ubuntu/ jaunty-security main restricted
deb http://archive.ubuntu.com/ubuntu/ jaunty-security universe
deb-src http://archive.ubuntu.com/ubuntu/ jaunty-security universe
deb http://archive.ubuntu.com/ubuntu/ jaunty-security multiverse
deb-src http://archive.ubuntu.com/ubuntu/ jaunty-security multiverse

deb http://ppa.launchpad.net/tualatrix/ubuntu jaunty main
deb-src http://ppa.launchpad.net/tualatrix/ubuntu jaunty main

```

---

### Post by samebchase on 2009-06-12
I got this:

```

deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)]/ jaunty main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty main restricted

## Major bug fix updates produced after the final release of the
## distribution.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://am.archive.ubuntu.com/ubuntu/](http://am.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse
# deb-src [http://am.archive.ubuntu.com/ubuntu/](http://am.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner

deb [http://ppa.launchpad.net/team-xbmc-intrepid/ubuntu](http://ppa.launchpad.net/team-xbmc-intrepid/ubuntu) intrepid main
deb-src [http://ppa.launchpad.net/team-xbmc-intrepid/ubuntu](http://ppa.launchpad.net/team-xbmc-intrepid/ubuntu) intrepid main
deb [http://ppa.launchpad.net/team-xbmc-intrepid/ppa/ubuntu](http://ppa.launchpad.net/team-xbmc-intrepid/ppa/ubuntu) intrepid main
deb [http://ppa.launchpad.net/team-xbmc/jaunty-ppa/ubuntu](http://ppa.launchpad.net/team-xbmc/jaunty-ppa/ubuntu) jaunty main
deb-src [http://ppa.launchpad.net/team-xbmc/jaunty-ppa/ubuntu](http://ppa.launchpad.net/team-xbmc/jaunty-ppa/ubuntu) jaunty main
deb [http://ppa.launchpad.net/team-xbmc/ppa/ubuntu/](http://ppa.launchpad.net/team-xbmc/ppa/ubuntu/) jaunty main
deb [http://ppa.launchpad.net/team-xbmc/ppa/ubuntu/](http://ppa.launchpad.net/team-xbmc/ppa/ubuntu/) jaunty main
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-updates restricted main multiverse universe
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) jaunty-security restricted main multiverse universe


```

---

### Post by colau on 2009-06-12
> **samebchase said:**
> I got this:

```

gpg --keyserver subkeys.pgp.net --recv 43C0AFF0D7FAE680
gpg --export --armor 43C0AFF0D7FAE680 | sudo apt-key add -
sudo apt-get update

```
Run these commands.
```

gpg --keyserver subkeys.pgp.net --recv 9F10E6AE9317790E
gpg --export --armor 9F10E6AE9317790E | sudo apt-key add -
sudo apt-get update

```

---

### Post by _Purple_ on 2009-06-12
colau, 
Add this line to your sources.list
```
deb-src http://packages.medibuntu.org/ jaunty free non-free 
```

Then run
```
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```

Does it still show error?

---

### Post by samebchase on 2009-06-12
@michy99 @_Purple_

What you suggested fixed the issue.

Thanks guys,
Samuel

---

### Post by _Purple_ on 2009-06-12
samebchase,
In sources.list file, replace the following lines
```
deb http://ppa.launchpad.net/team-xbmc-intrepid/ubuntu intrepid main
deb-src http://ppa.launchpad.net/team-xbmc-intrepid/ubuntu intrepid main
deb http://ppa.launchpad.net/team-xbmc-intrepid/ppa/ubuntu intrepid main
```

with
```
deb http://ppa.launchpad.net/team-xbmc-jaunty/ubuntu jaunty main
deb-src http://ppa.launchpad.net/team-xbmc-jaunty/ubuntu jaunty main
deb http://ppa.launchpad.net/team-xbmc-jaunty/ppa/ubuntu jaunty main 
```

Then save and run
```
sudo apt-get update
```

---

### Post by 3rdalbum on 2009-06-12
The message about the signatures not being verified, is just a warning, not an error message. You can still install packages from the repositories that you haven't added keys for.

---

### Post by colau on 2009-06-12
> **_Purple_ said:**
> colau, 
Add this line to your sources.list
```
deb-src http://packages.medibuntu.org/ jaunty free non-free 
```

Then run
```
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```

Does it still show error?
Still problem
```

W: GPG error: http://packages.medibuntu.org jaunty Release: The following signatures were invalid: BADSIG 2EBC26B60C5A2783 Medibuntu Packaging Team <admin@lists.medibuntu.org>
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: http://archive.ubuntu.com jaunty-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/jaunty-updates/Release  

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/jaunty-security/universe/binary-i386/Packages.bz2  Hash Sum mismatch

W: Some index files failed to download, they have been ignored, or old ones used instead.
W: You may want to run apt-get update to correct these problems

```

---

### Post by _Purple_ on 2009-06-12
colau,
Try to change the mirror to best server or any other server near you.

---

### Post by razorbone on 2009-09-19
Hi. Need help as well. :( I get this error whenever i try the "sudo apt-get update" command in the terminal. Also i get this same message when i try Update Manager with Kubuntu system:

[]("http://ubuntuforums.org/register.php?a=act&u=915053&i=30406fe41833f5de41839c81cfef0efcef7e05a8")W: GPG error: [http://ubuntu.cn99.com](http://ubuntu.cn99.com) jaunty-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: You may want to run apt-get update to correct these problems

Are the solutions provided in this thread applicable to this error message? Please help. :(

---

### Post by razorbone on 2009-09-19
I changed my server to "Main Server" and i still get this message:

GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>Failed to fetch [http://ppa.launchpad.net/kubuntu-ppa/backports/ubuntu/dists/jaunty/main/binary-i386/Packages.bz2](http://ppa.launchpad.net/kubuntu-ppa/backports/ubuntu/dists/jaunty/main/binary-i386/Packages.bz2)  Hash Sum mismatch
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/jaunty/universe/binary-i386/Packages.bz2](http://archive.ubuntu.com/ubuntu/dists/jaunty/universe/binary-i386/Packages.bz2)  Sub-process bzip2 returned an error code (2)
Some index files failed to download, they have been ignored, or old ones used instead.

Help Please.. :(

---

