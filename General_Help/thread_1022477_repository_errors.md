---
title: "repository errors"
date: 2008-12-26
forum: General Help
---

### Post by m_a_b on 2008-12-26
I could have sworn I posted this the other day, but I can't find it anywhere - I guess I hit the wrong button or something...

Anyway, I am getting errors when I add the update sources.  I have tried changing servers (3 different servers including the main) and get the same errors on all 3.  Can anyone tell me what is going on?  I am using 8.04.

Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/restricted/binary-lpia/Packages.gz](http://security.ubuntu.com/ubuntu/dists/hardy-security/restricted/binary-lpia/Packages.gz)  404 Not Found
Failed to fetch [http://ftp.usf.edu/pub/ubuntu/dists/hardy/main/binary-lpia/Packages.gz](http://ftp.usf.edu/pub/ubuntu/dists/hardy/main/binary-lpia/Packages.gz)  404 Not Found
Failed to fetch [http://ftp.usf.edu/pub/ubuntu/dists/hardy/restricted/binary-lpia/Packages.gz](http://ftp.usf.edu/pub/ubuntu/dists/hardy/restricted/binary-lpia/Packages.gz)  404 Not Found
Failed to fetch [http://ftp.usf.edu/pub/ubuntu/dists/hardy/universe/binary-lpia/Packages.gz](http://ftp.usf.edu/pub/ubuntu/dists/hardy/universe/binary-lpia/Packages.gz)  404 Not Found
Failed to fetch [http://ftp.usf.edu/pub/ubuntu/dists/hardy/multiverse/binary-lpia/Packages.gz](http://ftp.usf.edu/pub/ubuntu/dists/hardy/multiverse/binary-lpia/Packages.gz)  404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/main/binary-lpia/Packages.gz](http://security.ubuntu.com/ubuntu/dists/hardy-security/main/binary-lpia/Packages.gz)  404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/multiverse/binary-lpia/Packages.gz](http://security.ubuntu.com/ubuntu/dists/hardy-security/multiverse/binary-lpia/Packages.gz)  404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/universe/binary-lpia/Packages.gz](http://security.ubuntu.com/ubuntu/dists/hardy-security/universe/binary-lpia/Packages.gz)  404 Not Found
Failed to fetch [http://ftp.usf.edu/pub/ubuntu/dists/hardy-updates/restricted/binary-lpia/Packages.gz](http://ftp.usf.edu/pub/ubuntu/dists/hardy-updates/restricted/binary-lpia/Packages.gz)  404 Not Found
Failed to fetch [http://ftp.usf.edu/pub/ubuntu/dists/hardy-updates/main/binary-lpia/Packages.gz](http://ftp.usf.edu/pub/ubuntu/dists/hardy-updates/main/binary-lpia/Packages.gz)  404 Not Found
Failed to fetch [http://ftp.usf.edu/pub/ubuntu/dists/hardy-updates/multiverse/binary-lpia/Packages.gz](http://ftp.usf.edu/pub/ubuntu/dists/hardy-updates/multiverse/binary-lpia/Packages.gz)  404 Not Found
Failed to fetch [http://ftp.usf.edu/pub/ubuntu/dists/hardy-updates/universe/binary-lpia/Packages.gz](http://ftp.usf.edu/pub/ubuntu/dists/hardy-updates/universe/binary-lpia/Packages.gz)  404 Not Found
Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by fragos on 2008-12-26
You get those errors because those URLs don't exist on the Internet. It has nothing to do with servers.

---

### Post by 2hot6ft2 on 2008-12-26
Did you add those to your sources list?
Try ```
sudo apt-get update
``` in a terminal.

And if you added those then remove them they don't work.

what is this part > binary-lpia

---

### Post by m_a_b on 2008-12-26
I just added them from the admin>software sources applet by checking the box next to the entries.  If they don't exist then I guess it is a software bug?  

I did a little poking around on the server and I think it should be binary-i386 instead of binary-lpia.  Do I just remove the incorrect entries and add the updated link or is there a way to correct the problem so the applet actually uses the correct links?

---

### Post by 2hot6ft2 on 2008-12-26
> **m_a_b said:**
> I just added them from the admin>software sources applet by checking the box next to the entries.  If they don't exist then I guess it is a software bug?  

I did a little poking around on the server and I think it should be binary-i386 instead of binary-lpia.  Do I just remove the incorrect entries and add the updated link or is there a way to correct the problem so the applet actually uses the correct links?
I don't think the repos work that way. I don't think there's a i386 part. Open a terminal and run ```
sudo gedit /etc/apt/sources.list
``` and copy and paste the contents in a quote.

---

### Post by 2hot6ft2 on 2008-12-26
Here's mine but I'm running Hardy 8.04 Ultimate Edition 64 bit

I took some out that wouldn't apply to standard ubuntu

> # deb cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release amd64 (20080817.1)]/ hardy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://mirrors.us.kernel.org/ubuntu/](http://mirrors.us.kernel.org/ubuntu/) hardy main restricted
deb-src [http://mirrors.us.kernel.org/ubuntu/](http://mirrors.us.kernel.org/ubuntu/) hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://mirrors.us.kernel.org/ubuntu/](http://mirrors.us.kernel.org/ubuntu/) hardy-updates main restricted
deb-src [http://mirrors.us.kernel.org/ubuntu/](http://mirrors.us.kernel.org/ubuntu/) hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://mirrors.us.kernel.org/ubuntu/](http://mirrors.us.kernel.org/ubuntu/) hardy universe
deb-src [http://mirrors.us.kernel.org/ubuntu/](http://mirrors.us.kernel.org/ubuntu/) hardy universe
deb [http://mirrors.us.kernel.org/ubuntu/](http://mirrors.us.kernel.org/ubuntu/) hardy-updates universe
deb-src [http://mirrors.us.kernel.org/ubuntu/](http://mirrors.us.kernel.org/ubuntu/) hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://mirrors.us.kernel.org/ubuntu/](http://mirrors.us.kernel.org/ubuntu/) hardy multiverse
deb-src [http://mirrors.us.kernel.org/ubuntu/](http://mirrors.us.kernel.org/ubuntu/) hardy multiverse
deb [http://mirrors.us.kernel.org/ubuntu/](http://mirrors.us.kernel.org/ubuntu/) hardy-updates multiverse
deb-src [http://mirrors.us.kernel.org/ubuntu/](http://mirrors.us.kernel.org/ubuntu/) hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

deb [http://mirrors.us.kernel.org/ubuntu/](http://mirrors.us.kernel.org/ubuntu/) hardy-security main restricted
deb-src [http://mirrors.us.kernel.org/ubuntu/](http://mirrors.us.kernel.org/ubuntu/) hardy-security main restricted
deb [http://mirrors.us.kernel.org/ubuntu/](http://mirrors.us.kernel.org/ubuntu/) hardy-security universe
deb-src [http://mirrors.us.kernel.org/ubuntu/](http://mirrors.us.kernel.org/ubuntu/) hardy-security universe
deb [http://mirrors.us.kernel.org/ubuntu/](http://mirrors.us.kernel.org/ubuntu/) hardy-security multiverse
deb-src [http://mirrors.us.kernel.org/ubuntu/](http://mirrors.us.kernel.org/ubuntu/) hardy-security multiverse


---

### Post by 2hot6ft2 on 2008-12-26
You may be right and it looks like changing it to i386 would work like this one.
> [http://security.ubuntu.com/ubuntu/dists/hardy-security/main/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/hardy-security/main/binary-i386/Packages.gz)
Strange how yours would go 5 layers deeper than mine to get the info and yet mine works.

---

### Post by 2hot6ft2 on 2008-12-26
That would make mine go like this
```
http://mirrors.us.kernel.org/ubuntu/dists/hardy-security/main/binary-amd64/Packages.gz
```
when it only goes here now.
```
http://mirrors.us.kernel.org/ubuntu/
```

Weird

---

### Post by fragos on 2008-12-26
Those .gz files are inside the repositories. You're pointing too deep.

---

### Post by 2hot6ft2 on 2008-12-26
> **fragos said:**
> Those .gz files are inside the repositories. You're pointing too deep.
That's what I was thinking. Mine works so I'm not messing with it.

---

### Post by m_a_b on 2008-12-27
my sources.list file looks like this:

> deb [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy main universe multiverse restricted
deb-src [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy main universe multiverse restricted

deb [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-updates main universe multiverse restricted
deb-src [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-updates main universe multiverse restricted

deb [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-security main universe multiverse restricted
deb-src [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-security main universe multiverse restricted

deb [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-netbook-base main universe multiverse restricted
deb-src [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-netbook-base main universe multiverse restricted

deb [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-dell-mini main universe multiverse restricted
deb [http://ftp.usf.edu/pub/ubuntu/](http://ftp.usf.edu/pub/ubuntu/) hardy main restricted universe multiverse
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hardy-security restricted main multiverse universe
deb [http://ftp.usf.edu/pub/ubuntu/](http://ftp.usf.edu/pub/ubuntu/) hardy-updates restricted main multiverse universe
deb-src [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-dell-mini main universe multiverse restricted

Honestly, I didn't do anything to change the sources other than just check the boxes in the software sources applet.

---

### Post by m_a_b on 2008-12-29
bump bump

---

### Post by plucky on 2008-12-29
Do you know how to edit your sources.list?

From what I have read,these three lines should not be in your sources.list
```
deb http://ftp.usf.edu/pub/ubuntu/ hardy main restricted universe multiverse
deb http://security.ubuntu.com/ubuntu/ hardy-security restricted main multiverse universe
deb http://ftp.usf.edu/pub/ubuntu/ hardy-updates restricted main multiverse universe
```

So open your software sources and un-tick the boxes that point to these sources,or edit your sources.list file and put a # in front of each line.

Then reload or "sudo apt-get update" and see if that works.

Good luck

---

### Post by m_a_b on 2008-12-29
well if I remove all of the checked items on the "Ubuntu Software" tab, the errors go away and my sources file looks like: 

> deb [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy main universe multiverse restricted
deb-src [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy main universe multiverse restricted

deb [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-updates main universe multiverse restricted
deb-src [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-updates main universe multiverse restricted

deb [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-security main universe multiverse restricted
deb-src [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-security main universe multiverse restricted

deb [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-netbook-base main universe multiverse restricted
deb-src [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-netbook-base main universe multiverse restricted

deb [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-dell-mini main universe multiverse restricted
deb-src [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-dell-mini main universe multiverse restricted

Is that sufficient?  Are those the only sources I need?

---

### Post by fragos on 2008-12-29
I found medibuntu.org very usefull for the free but not GPL stuff like codecs and Google Earth. The site has directions on how to add their repository.

---

### Post by plucky on 2008-12-30
From what I have been reading in the dell subforum,the Dell mini uses the Intel Atom processor,which doesn't support the X86 instruction set,and therefore you have to use special lpia software that those repos provide.That means that the normal ubuntu repositories will not work for you.

Well anyhow that is my understanding,but as I don't have a Dell mini 9 I cannot verify for myself.


Good Luck

---

### Post by m_a_b on 2008-12-30
yeah it is the atom processor.  I didn't even put 2 and 2 together. makes sense.

---

