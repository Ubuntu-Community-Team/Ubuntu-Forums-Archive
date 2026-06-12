---
title: "Help restoring /etc/apt/sources.list on Ubuntu 8.10 back"
date: 2009-01-02
forum: General Help
---

### Post by Tasc0 on 2009-01-02
I was trying to install Firefox 2 by following [this]("http://ubuntuforums.org/showthread.php?t=974955#3"), and I now I can't restore it back. The back up file won't work, is the same as the source.list file (Hardy).

Please help!

---

### Post by adult swim on 2009-01-02
```
gksudo gedit /etc/apt/sources.list
```
highlight everything in there and erase it then paste this in and save it 
```
# deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release Candidate i386 (20081022)]/ intrepid main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://archive.ubuntu.com/ubuntu/ intrepid main restricted
deb-src http://archive.ubuntu.com/ubuntu/ intrepid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu/ intrepid-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu/ intrepid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu/ intrepid universe
deb-src http://archive.ubuntu.com/ubuntu/ intrepid universe
deb http://archive.ubuntu.com/ubuntu/ intrepid-updates universe
deb-src http://archive.ubuntu.com/ubuntu/ intrepid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://archive.ubuntu.com/ubuntu/ intrepid multiverse
deb-src http://archive.ubuntu.com/ubuntu/ intrepid multiverse
deb http://archive.ubuntu.com/ubuntu/ intrepid-updates multiverse
deb-src http://archive.ubuntu.com/ubuntu/ intrepid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
#deb http://archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse
#deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu intrepid partner
deb-src http://archive.canonical.com/ubuntu intrepid partner

deb http://archive.ubuntu.com/ubuntu/ intrepid-security main restricted
deb-src http://archive.ubuntu.com/ubuntu/ intrepid-security main restricted
deb http://archive.ubuntu.com/ubuntu/ intrepid-security universe
deb-src http://archive.ubuntu.com/ubuntu/ intrepid-security universe
deb http://archive.ubuntu.com/ubuntu/ intrepid-security multiverse
#deb http://archive.ubuntu.com/ubuntu/ intrepid-proposed restricted main multiverse universe
deb-src http://archive.ubuntu.com/ubuntu/ intrepid-security multiverse

```

---

### Post by Tasc0 on 2009-01-03
> **adult swim said:**
> ```
gksudo gedit /etc/apt/sources.list
```
highlight everything in there and erase it then paste this in and save it 
```
# deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release Candidate i386 (20081022)]/ intrepid main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://archive.ubuntu.com/ubuntu/ intrepid main restricted
deb-src http://archive.ubuntu.com/ubuntu/ intrepid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu/ intrepid-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu/ intrepid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu/ intrepid universe
deb-src http://archive.ubuntu.com/ubuntu/ intrepid universe
deb http://archive.ubuntu.com/ubuntu/ intrepid-updates universe
deb-src http://archive.ubuntu.com/ubuntu/ intrepid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://archive.ubuntu.com/ubuntu/ intrepid multiverse
deb-src http://archive.ubuntu.com/ubuntu/ intrepid multiverse
deb http://archive.ubuntu.com/ubuntu/ intrepid-updates multiverse
deb-src http://archive.ubuntu.com/ubuntu/ intrepid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
#deb http://archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse
#deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu intrepid partner
deb-src http://archive.canonical.com/ubuntu intrepid partner

deb http://archive.ubuntu.com/ubuntu/ intrepid-security main restricted
deb-src http://archive.ubuntu.com/ubuntu/ intrepid-security main restricted
deb http://archive.ubuntu.com/ubuntu/ intrepid-security universe
deb-src http://archive.ubuntu.com/ubuntu/ intrepid-security universe
deb http://archive.ubuntu.com/ubuntu/ intrepid-security multiverse
#deb http://archive.ubuntu.com/ubuntu/ intrepid-proposed restricted main multiverse universe
deb-src http://archive.ubuntu.com/ubuntu/ intrepid-security multiverse

```
That has more lines than the original one. I also use the **[http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com)** server.

---

### Post by drs305 on 2009-01-03
> **Tasc0 said:**
> That has more lines than the original one. I also use the **[http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com)** server.

You can use the sources.list above to get your update system back running again (if you are using intrepid). Then open synaptic or System > Admin > Software Sources. On the Ubuntu Software tab, go to Settings, Repositories and in the Download from window, select 'Other'. You can then change back to your preferred [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) if it is a standard ubuntu server.

As far as seeing more entries, they are controlled by what you have ticked in various Ubuntu Software/Third Party/Updates tabs. Just untick the sources you don't want to see.

These changes will edit your sources.list

---

### Post by Tasc0 on 2009-01-03
> **drs305 said:**
> You can use the sources.list above to get your update system back running again (if you are using intrepid). Then open synaptic or System > Admin > Software Sources. On the Ubuntu Software tab, go to Settings, Repositories and in the Download from window, select 'Other'. You can then change back to your preferred [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) if it is a standard ubuntu server.

As far as seeing more entries, they are controlled by what you have ticked in various Ubuntu Software/Third Party/Updates tabs. Just untick the sources you don't want to see.

These changes will edit your sources.list
Thanks, but I'm not convised by that.

Can't I just have the *original* un-modified **sources.list** of Ubuntu 8.10?

---

### Post by drs305 on 2009-01-03
> **Tasc0 said:**
> Thanks, but I'm not convised by that.

Can't I just have the *original* un-modified **sources.list** of Ubuntu 8.10?


```

# deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - amd64 (20081001)]/ intrepid main restricted
deb http://archive.ubuntu.com/ubuntu intrepid main restricted
deb-src http://archive.ubuntu.com/ubuntu intrepid main restricted
    
deb http://security.ubuntu.com/ubuntu intrepid-security main restricted
deb-src http://security.ubuntu.com/ubuntu intrepid-security main restricted
       
## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu intrepid-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu intrepid-updates main restricted
       

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb http://archive.ubuntu.com/ubuntu intrepid universe
# deb-src http://archive.ubuntu.com/ubuntu intrepid universe
# deb http://archive.ubuntu.com/ubuntu intrepid-updates universe
# deb-src http://archive.ubuntu.com/ubuntu intrepid-updates universe
# deb http://archive.ubuntu.com/ubuntu intrepid-security universe
# deb-src http://archive.ubuntu.com/ubuntu intrepid-security universe

```

---

### Post by taurus on 2009-01-03
> **Tasc0 said:**
> Thanks, but I'm not convised by that.

Can't I just have the *original* un-modified **sources.list** of Ubuntu 8.10?

What's the output of this command from a terminal?

```
ls -la /etc/apt
```

---

### Post by Tasc0 on 2009-01-03
> **taurus said:**
> What's the output of this command from a terminal?

```
ls -la /etc/apt
```
```

total 60
drwxr-xr-x   4 root root  4096 2009-01-03 12:59 .
drwxr-xr-x 123 root root 12288 2009-01-03 14:52 ..
drwxr-xr-x   2 root root  4096 2009-01-02 20:59 apt.conf.d
-rw-------   1 root root     0 2008-10-29 19:54 secring.gpg
-rw-r--r--   1 root root  3131 2009-01-03 12:50 sources.list
-rw-r--r--   1 root root  2994 2009-01-03 12:43 sources.list~
-rw-r--r--   1 root root  2970 2009-01-03 01:00 sources.list.backup
drwxr-xr-x   2 root root  4096 2008-08-14 13:55 sources.list.d
-rw-r--r--   1 root root  3077 2009-01-03 12:50 sources.list.save
-rw-------   1 root root  1200 2008-10-29 19:54 trustdb.gpg
-rw-r--r--   1 root root  6713 2008-10-29 19:54 trusted.gpg
-rw-r--r--   1 root root  6713 2008-10-29 19:54 trusted.gpg~

```

---

### Post by drs305 on 2009-01-03
From what you posted it looks like all your sources.list backups are from today. ;-(

The list I posted is from the LiveCD. I commented out the CDROM since your's is probably not the same version.

---

### Post by Tasc0 on 2009-01-03
> **drs305 said:**
> From what you posted it looks like all your sources.list backups are from today. ;-(

The list I posted is from the LiveCD. I commented out the CDROM since your's is probably not the same version.
Huh?

---

### Post by heatpumpcontrol on 2009-01-03
Seems to me that drs305 has provided you with what you need. You may be asking for something different and you're not verbalizing that.
That list is from the live cd and it doesn't get any better than that.

---

### Post by drs305 on 2009-01-03
> **Tasc0 said:**
> Huh?

I'm not sure I understand the post but I'll try to answer. All your sources.list files/backups are from today but your first post appears to be from yesterday, so I inferred that you didn't have an old enough backup to be an original. 

I commented out the CD because the file designation in the post is actually from the beta version. The 1 Oct date may be earlier than the release version cd. When you use an ubuntu cd as a source, you must use the one that is listed in sources.list (or alter your file). For instance, you couldn't use an 8.1 LiveCD if you installed via the 8.04 LiveCD unless you update it in sources.list. 

Hope that explains things. And if you have resolved the issue please mark the thread solved or ask more questions.

---

### Post by Tasc0 on 2009-01-04
> **drs305 said:**
> I'm not sure I understand the post but I'll try to answer. All your sources.list files/backups are from today but your first post appears to be from yesterday, so I inferred that you didn't have an old enough backup to be an original. 

I commented out the CD because the file designation in the post is actually from the beta version. The 1 Oct date may be earlier than the release version cd. When you use an ubuntu cd as a source, you must use the one that is listed in sources.list (or alter your file). For instance, you couldn't use an 8.1 LiveCD if you installed via the 8.04 LiveCD unless you update it in sources.list. 

Hope that explains things. And if you have resolved the issue please mark the thread solved or ask more questions.
Well, as far as restoring the *original* source.list, no, it's not solved.

But I used the one in post [#2]("http://ubuntuforums.org/showthread.php?t=1028990#2") and it works okay.

So, I'm not sure if I should tag it as "solved". I was looking for a command to restore it back.

---

