---
title: "About repositories"
date: 2009-04-18
forum: General Help
---

### Post by satimis on 2009-04-18
Hi folks,


Ubuntu 8.04


I have only one entry on /etc/apt/source.list```

deb http://archive.ubuntu.com/ubuntu hardy main

```


Now I need to make the package sources pointing to main multiverse restricted universe repositories. 


Please advise whether I add follows on that file;```

deb http://archive.ubuntu.com/ubuntu hardy main restricted multiverse universe 
deb-src http://archive.ubuntu.com/ubuntu hardy main restricted multiverse universe 
deb http://archive.ubuntu.com/ubuntu hardy-updates main restricted multiverse universe 
deb-src http://archive.ubuntu.com/ubuntu hardy-updates main restricted multiverse universe 
deb http://archive.ubuntu.com/ubuntu hardy-security main restricted multiverse universe 
deb-src http://archive.ubuntu.com/ubuntu hardy-security main restricted multiverse universe 
deb http://archive.ubuntu.com/ubuntu hardy-backports main restricted multiverse universe 
deb-src http://archive.ubuntu.com/ubuntu hardy-backports main restricted multiverse universe 

```

TIA


B.R.
satimis

---

### Post by mb_webguy on 2009-04-18
Open System->Administration->Software Sources, and on the Ubuntu Software tab, check the boxes next to "Community-maintained Open Source software (universe)", "Proprietary drivers for devices (restricted)", and "Software restricted by copyright or legal issues (multiverse)".

Checking these boxes will add those repositories to your /etc/apt/source.list file.

---

### Post by satimis on 2009-04-18
> **mb_webguy said:**
> Open System->Administration->Software Sources, and on the Ubuntu Software tab, check the boxes next to "Community-maintained Open Source software (universe)", "Proprietary drivers for devices (restricted)", and "Software restricted by copyright or legal issues (multiverse)".

Checking these boxes will add those repositories to your /etc/apt/source.list file.
Hi mb_webguy,


Thanks for your advice.

I don't have desktop running.  This is only a basic OS without X.  I'm building a server on it.


B.R.
satimis

---

### Post by _Purple_ on 2009-04-18
> **satimis said:**
> Hi mb_webguy,


Thanks for your advice.

I don't have desktop running.  This is only a basic OS without X.  I'm building a server on it.


B.R.
satimis

Please check [this page](https://help.ubuntu.com/community/Repositories/CommandLine) to manage repositories using CLI.

---

### Post by satimis on 2009-04-18
> **_Purple_ said:**
> Please check [this page](https://help.ubuntu.com/community/Repositories/CommandLine) to manage repositories using CLI.

Hi _Purple_


Thanks for your advice and URL.


# cat /etc/apt/source.list```

deb http://archive.ubuntu.com/ubuntu hardy main

```
It is an empty file with only one line.


I'll add following repositories to the file;

For the Universe:```

deb http://archive.ubuntu.com/ubuntu/ hardy universe
deb-src http://archive.ubuntu.com/ubuntu/ hardy universe
deb http://archive.ubuntu.com/ubuntu/ hardy-updates universe
deb-src http://archive.ubuntu.com/ubuntu/ hardy-updates universe

```


For the Multiverse:```

deb http://archive.ubuntu.com/ubuntu/ hardy multiverse
deb-src http://archive.ubuntu.com/ubuntu/ hardy multiverse
deb http://archive.ubuntu.com/ubuntu/ hardy-updates multiverse
deb-src http://archive.ubuntu.com/ubuntu/ hardy-updates multiverse

```


For the restricted Universe:```

deb http://archive.ubuntu.com/ubuntu/ hardy main restricted
deb-src http://archive.ubuntu.com/ubuntu/ hardy main restricted
deb http://archive.ubuntu.com/ubuntu/ hardy-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu/ hardy-updates main restricted

```

Then run "apt-get update" afterwards.

If I miss any repositories please correct me.  TIA


Do I need importing any key?


B.R.
satimis

---

### Post by juancarlospaco on 2009-04-18
make backup of sources.list

---

### Post by satimis on 2009-04-18
> **juancarlospaco said:**
> make backup of sources.list
Hi juancarlospaco,


Yes, I'll.  Thanks.


A further question:
For example, if I want to use the mirror;
[ftp://ftp.planetmirror.com/pub/ubuntu/](ftp://ftp.planetmirror.com/pub/ubuntu/)

whether replace all```

deb http://archive.ubuntu.com/ubuntu/  ....
deb-src http://archive.ubuntu.com/ubuntu/  ....

```

with```

deb ftp://ftp.planetmirror.com/pub/ubuntu/  ....
deb-src ftp://ftp.planetmirror.com/pub/ubuntu/  ....
.....

```
?

Thanks


B.R.
satimis

---

### Post by _Purple_ on 2009-04-18
Hi satimis

As juancarlospaco has mentioned, its always a good idea to backup your configuration files before making any changes.
```
sudo cp /etc/apt/sources.list /etc/apt/sources.list.backup
```

May be you can take a look at this list and add them if you want. Its includes the main, restricted, universe, multiverse and security, updates, proposed and backports. 

```

###### Ubuntu Main Repos
deb http://us.archive.ubuntu.com/ubuntu/ hardy main restricted universe multiverse 
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy main restricted universe multiverse 

###### Ubuntu Update Repos
deb http://us.archive.ubuntu.com/ubuntu/ hardy-security main restricted universe multiverse 
deb http://us.archive.ubuntu.com/ubuntu/ hardy-updates main restricted universe multiverse 
deb http://us.archive.ubuntu.com/ubuntu/ hardy-proposed main restricted universe multiverse 
deb http://us.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse 
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-security main restricted universe multiverse 
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-updates main restricted universe multiverse 
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-proposed main restricted universe multiverse 
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse 

###### Ubuntu Partner Repo
deb http://archive.canonical.com/ubuntu hardy partner
deb-src http://archive.canonical.com/ubuntu hardy partner



```

After adding these to the list, save and run
```
sudo apt-get update
```

Please note that the lines starting with # are commented.

---

### Post by _Purple_ on 2009-04-18
> **satimis said:**
> Hi juancarlospaco,


Yes, I'll.  Thanks.


A further question:
For example, if I want to use the mirror;
[ftp://ftp.planetmirror.com/pub/ubuntu/](ftp://ftp.planetmirror.com/pub/ubuntu/)

whether replace all```

deb http://archive.ubuntu.com/ubuntu/  ....
deb-src http://archive.ubuntu.com/ubuntu/  ....

```

with```

deb ftp://ftp.planetmirror.com/pub/ubuntu/  ....
deb-src ftp://ftp.planetmirror.com/pub/ubuntu/  ....
.....

```
?

Thanks


B.R.
satimis

Correct. You can add the ftp sources using that format and you do not have to import any key for that. :)

---

### Post by satimis on 2009-04-18
> **_Purple_ said:**
> Correct. You can add the ftp sources using that format and you do not have to import any key for that. :)

Hi _Purple_,


Performed following steps;

# cp /etc/apt/sources.list /etc/apt/sources.list.origin

# nano /etc/apt/sources.list
adding;```


###### For the Universe:
deb ftp://ftp.planetmirror.com/pub/ubuntu/ hardy universe
deb-src ftp://ftp.planetmirror.com/pub/ubuntu/ hardy universe
deb ftp://ftp.planetmirror.com/pub/ubuntu/ hardy-updates universe
deb-src ftp://ftp.planetmirror.com/pub/ubuntu/ hardy-updates universe

###### For the Multiverse:
deb ftp://ftp.planetmirror.com/pub/ubuntu/ hardy multiverse
deb-src ftp://ftp.planetmirror.com/pub/ubuntu/ hardy multiverse
deb ftp://ftp.planetmirror.com/pub/ubuntu/ hardy-updates multiverse
deb-src ftp://ftp.planetmirror.com/pub/ubuntu/ hardy-updates multiverse

###### For the restricted Universe:
deb ftp://ftp.planetmirror.com/pub/ubuntu/ hardy main restricted
deb-src ftp://ftp.planetmirror.com/pub/ubuntu/ hardy main restricted
deb ftp://ftp.planetmirror.com/pub/ubuntu/ hardy-updates main restricted
deb-src ftp://ftp.planetmirror.com/pub/ubuntu/ hardy-updates main restricted


###### Ubuntu Update Repos
deb ftp://ftp.planetmirror.com/pub/ubuntu/ hardy-security main restricted universe multiverse 
deb ftp://ftp.planetmirror.com/pub/ubuntu/ hardy-updates main restricted universe multiverse 
deb ftp://ftp.planetmirror.com/pub/ubuntu/ hardy-proposed main restricted universe multiverse 
deb ftp://ftp.planetmirror.com/pub/ubuntu/ hardy-backports main restricted universe multiverse 
deb-src ftp://ftp.planetmirror.com/pub/ubuntu/ hardy-security main restricted universe multiverse 
deb-src ftp://ftp.planetmirror.com/pub/ubuntu/ hardy-updates main restricted universe multiverse 
deb-src ftp://ftp.planetmirror.com/pub/ubuntu/ hardy-proposed main restricted universe multiverse 
deb-src ftp://ftp.planetmirror.com/pub/ubuntu/ hardy-backports main restricted universe multiverse 

###### Ubuntu Partner Repo
deb http://archive.canonical.com/ubuntu hardy partner
deb-src http://archive.canonical.com/ubuntu hardy partner

```


# aptitude update```

Err ftp://ftp.planetmirror.com hardy Release.gpg                                                      
  Could not resolve 'ftp.planetmirror.com'
Err ftp://ftp.planetmirror.com hardy-updates Release.gpg                                              
  Could not resolve 'ftp.planetmirror.com'
Err ftp://ftp.planetmirror.com hardy-security Release.gpg                                             
  Could not resolve 'ftp.planetmirror.com'
Err ftp://ftp.planetmirror.com hardy-proposed Release.gpg                                             
  Could not resolve 'ftp.planetmirror.com'
Err ftp://ftp.planetmirror.com hardy-backports Release.gpg                                            
  Could not resolve 'ftp.planetmirror.com'
Get:1 http://archive.canonical.com hardy Release.gpg [189B]                                           
Get:2 http://archive.canonical.com hardy Release [6998B]                                              
Ign http://archive.canonical.com hardy/partner Packages                         
Ign http://archive.canonical.com hardy/partner Sources
Get:3 http://archive.canonical.com hardy/partner Packages [3642B]
Get:4 http://archive.canonical.com hardy/partner Sources [1550B]                               
Hit http://archive.ubuntu.com hardy Release.gpg                                 
Hit http://archive.ubuntu.com hardy Release          
Hit http://archive.ubuntu.com hardy/main Packages
Fetched 12.4kB in 4s (2706B/s)
Reading package lists... Done

```

There are warnings here.  It seems the mistakes haveing been rectified automatically.  Do I need taking any action here?

OR

Replace "partner repo"```

http://archive.canonical.com/ubuntu

```

with```

ftp://ftp.planetmirror.com/pub/ubuntu/

```

Thanks


# aptitude upgrade```

W: The "upgrade" command is deprecated; use "safe-upgrade" instead.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done  

```
    

# aptitude safe-upgrade```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      

```


B.R.
satimis

---

### Post by _Purple_ on 2009-04-18
Hey satimis,
There are few repositories in your /etc/apt/sources.list that are repeated. You can follow the one I have posted earlier. As for the ftp mirror, I am not sure why this error is generated. Looks like it is a mirror of Australia. Why don't you try some other mirror and see if it works for you?

---

### Post by oldos2er on 2009-04-18
"# aptitude upgrade"

 Run "aptitude update" first to enable the repositories.

---

### Post by satimis on 2009-04-19
> **_Purple_ said:**
> Hey satimis,
There are few repositories in your /etc/apt/sources.list that are repeated. You can follow the one I have posted earlier. As for the ftp mirror, I am not sure why this error is generated. Looks like it is a mirror of Australia. Why don't you try some other mirror and see if it works for you?
Hi _Purple_,

After saving my sources.list I used your sources.list running "aptitude update" and then "aptitude upgrade"

Following errors found;


# cat /var/log/apt/term.log | grep error```

 * Setting kernel variables...                                                  
error: permission denied on key 'kernel.printk'
error: permission denied on key 'kernel.maps_protect'
error: permission denied on key 'fs.inotify.max_user_watches'
error: "vm.mmap_min_addr" is an unknown key

```


# cat /var/log/apt/term.log | grep fail ```

invoke-rc.d: initscript apparmor, action "start" failed.
invoke-rc.d: initscript apparmor, action "reload" failed.
invoke-rc.d: initscript apparmor, action "force-reload" failed.
                                                                         [fail]
invoke-rc.d: initscript apparmor, action "start" failed.
invoke-rc.d: initscript apparmor, action "reload" failed.
invoke-rc.d: initscript apparmor, action "force-reload" failed.

```


This is a guest (VZ) running on OpenVZ, a virtualization box;

Host - Ubuntu 8.04, workstation
Guest (VZ) - base Ubuntu 8.04

I'm prepared building a Mail Server on the guest.


In such a circumstance I'll remove this VZ and create a new one.  I'll use the sources.list of the host on the new VZ which has following content;```

#deb cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1)]/ hardy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://hk.archive.ubuntu.com/ubuntu/ hardy main restricted
deb-src http://hk.archive.ubuntu.com/ubuntu/ hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://hk.archive.ubuntu.com/ubuntu/ hardy-updates main restricted
deb-src http://hk.archive.ubuntu.com/ubuntu/ hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://hk.archive.ubuntu.com/ubuntu/ hardy universe
deb-src http://hk.archive.ubuntu.com/ubuntu/ hardy universe
deb http://hk.archive.ubuntu.com/ubuntu/ hardy-updates universe
deb-src http://hk.archive.ubuntu.com/ubuntu/ hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://hk.archive.ubuntu.com/ubuntu/ hardy multiverse
deb-src http://hk.archive.ubuntu.com/ubuntu/ hardy multiverse
deb http://hk.archive.ubuntu.com/ubuntu/ hardy-updates multiverse
deb-src http://hk.archive.ubuntu.com/ubuntu/ hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://hk.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse
# deb-src http://hk.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu hardy partner
# deb-src http://archive.canonical.com/ubuntu hardy partner

deb http://security.ubuntu.com/ubuntu hardy-security main restricted
deb-src http://security.ubuntu.com/ubuntu hardy-security main restricted
deb http://security.ubuntu.com/ubuntu hardy-security universe
deb-src http://security.ubuntu.com/ubuntu hardy-security universe
deb http://security.ubuntu.com/ubuntu hardy-security multiverse
deb-src http://security.ubuntu.com/ubuntu hardy-security multiverse

```


to see whether there is any problem.  Any advice on the said sources.list ?


B.R.
satimis

---

### Post by satimis on 2009-04-19
> **oldos2er said:**
> "# aptitude upgrade"

 Run "aptitude update" first to enable the repositories.

Yes, I did.  Thanks


B.R.
satimis

---

### Post by satimis on 2009-04-19
Hi _Purple_ and folks,


host - Ubuntu 8.04 workstation
guests (VZ) - ubuntu-8.04-i386-minimal


Restarted from the beginning, created a new VZ with clean ubuntu-8.04-i386-minimal installed.  It is running without problem.  Network established.  Ping its ip address w/o packet loss.

# cp /etc/apt/sources.list /etc/apt/sources.list.origin

It was an one line file as previously stated.

Added the content of /etc/apt/sources.list of the host on the said file.

# aptitude update
Went through w/o complaint


# aptitude safe-upgrade```

.....
The following packages will be upgraded:
  apt apt-utils base-files bash bsdutils dash dpkg gcc-4.2-base 
  initscripts iproute klibc-utils libc6 libc6-i686 libcurl3-gnutls 
  libdbus-1-3 libgcc1 libgnutls13 libklibc libkrb53 libldap-2.4-2 
  libpam-modules libpam-runtime libpam0g libssl0.9.8 libstdc++6 
  login mount passwd perl-base procps python2.5 python2.5-minimal 
  ssh sudo sysv-rc sysvutils tzdata util-linux util-linux-locales 
  vim-common vim-tiny 
41 packages upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
Need to get 24.1MB of archives. After unpacking 32.8kB will be used.
Do you want to continue? [Y/n/?] Y
....
....
find: /var/cache/fontconfig: No such file or directory
find: /var/cache/fonts: No such file or directory
find: /var/cache/anthy: No such file or directory
find: /var/lib/belocs: No such file or directory
find: /var/lib/gconf: No such file or directory
find: /var/lib/defoma: No such file or directory
find: /var/log/installer: No such file or directory
find: /initrd.img: No such file or directory
find: /vmlinuz: No such file or directory
find: /cdrom: No such file or directory
find: /media/cdrom: No such file or directory
find: /usr/share/fonts: No such file or directory
find: /var/lib/anthy: No such file or directory
find: /var/lib/defoma: No such file or directory
find: /lib/modules: No such file or directory
....
....
Setting up procps (1:3.2.7-5ubuntu3) ...
 * Setting kernel variables...                                      
error: permission denied on key 'kernel.printk'
error: permission denied on key 'kernel.maps_protect'
error: permission denied on key 'fs.inotify.max_user_watches'
error: "vm.mmap_min_addr" is an unknown key
                                                             [fail]
....

```
Above mistakes have been found.  Can I ignore them?


TIA


B.R.
satimis

---

