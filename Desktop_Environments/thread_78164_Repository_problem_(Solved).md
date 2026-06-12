---
title: "Repository problem? (Solved)"
date: 2005-10-17
forum: Desktop Environments
---

### Post by rozojc on 2005-10-17
Hi everyone...
I'm having a problem lately and haven't been able to find a solution (which is normal cause I'm not precisely a linux guru or anything :D ).

I don't know why but I added a repositorie to Synaptic and it started complaining about a signature that was wrong. "No prob", I thought, and I just deleted the line, but I keep getting the error. Each time I open Synaptic and I reload everything it says:

W: GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

Now, that I know of, I have a pretty standard (maybe sub-standard)
So, I checked the forum and I removed all the "us" prefixes to the repositories, relodad and...nope, didn't work, I'm now getting:

W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

Any ideas? The following is my sources.list file:
#deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Preview i386 (20050908)]/ breezy main restricted

deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main restricted

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted

# deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) breezy multiverse universe main restricted


#deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) sarge main
#deb [ftp://cipherfunk.org/pub/packages/ubuntu](ftp://cipherfunk.org/pub/packages/ubuntu) breezy main

---

### Post by dbott67 on 2005-10-17
The US archives are down.  The answer is in [this thread]("http://www.ubuntuforums.org/showthread.php?p=411974").

This is the "official" sources.list file.  Your /etc/apt/sources.list file needs to be edited so that it looks like this (basically, you have to remove any of the 'US' parts of the URLs):

```
## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu breezy-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu breezy main universe multiverse restricted
deb-src http://archive.ubuntu.com/ubuntu breezy main universe multiverse restricted

deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

deb http://security.ubuntu.com/ubuntu breezy-security universe
deb-src http://security.ubuntu.com/ubuntu breezy-security universe
```

Close Synaptic & when you open it, click RELOAD.

-Dave

---

### Post by rozojc on 2005-10-17
Ooops, I did look at that thread but didn't see that part where you pasted the official list. I just copied and pasted it on top of mine (leaving the two things I had added and commented where I got the win32 video codecs from) and it worked.

Thanx and sorry for asking something that had actually been answered already :rolleyes:

---

### Post by gbusse on 2005-10-18
NOT SOLVED... I tried this and I am still getting GPG errors....

---

### Post by nix4me on 2005-10-18
I agree.  That worked for me last night but not tonight.  Im using the de repositories now with success.

I wonder why there are so many problems.

nix

---

### Post by thinkpadg41 on 2005-10-19
[QUOTE=dbott67]The US archives are down.  The answer is in [this thread]("http://www.ubuntuforums.org/showthread.php?p=411974").

This is the "official" sources.list file.  Your /etc/apt/sources.list file needs to be edited so that it looks like this (basically, you have to remove any of the 'US' parts of the URLs):

```
## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu breezy-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu breezy main universe multiverse restricted
deb-src http://archive.ubuntu.com/ubuntu breezy main universe multiverse restricted

deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

deb http://security.ubuntu.com/ubuntu breezy-security universe
deb-src http://security.ubuntu.com/ubuntu breezy-security universe
```

Close Synaptic & when you open it, click RELOAD.

-Dave[/QUOTE]


.......when I'm done upgrading codecs and etc, should I  insert a '#' - back, at the beginning of the line of all restricted in the "resources.list" ?????

---

