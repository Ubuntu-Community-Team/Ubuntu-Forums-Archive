---
title: "problem while trying to apt-get update"
date: 2005-05-20
forum: Desktop Environments
---

### Post by kingofhell on 2005-05-20
i get this error when i typed sudo apt-get update in console
W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: [http://sg.archive.ubuntu.com](http://sg.archive.ubuntu.com) hoary-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.


i did exactly what is said in [www.ubuntuguide.org](www.ubuntuguide.org)  including 
gpg --keyserver wwwkeys.eu.pgp.net --recv-keys 1F41B907
gpg --armor --export 1F41B907 | sudo apt-key add -

---

### Post by stevenyu on 2005-05-21
can you post the content of your source file from** /etc/apt/**

---

### Post by kingofhell on 2005-05-21
[QUOTE=stevenyu]can you post the content of your source file from** /etc/apt/**[/QUOTE]
sure
deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted


deb [http://sg.archive.ubuntu.com/ubuntu](http://sg.archive.ubuntu.com/ubuntu) hoary main restricted
deb-src [http://sg.archive.ubuntu.com/ubuntu](http://sg.archive.ubuntu.com/ubuntu) hoary main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://sg.archive.ubuntu.com/ubuntu](http://sg.archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb-src [http://sg.archive.ubuntu.com/ubuntu](http://sg.archive.ubuntu.com/ubuntu) hoary-updates main restricted

## Uncomment the following two lines to fetch updated software from the network
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse

deb [ftp://ftp.nerim.net/debian-marillat](ftp://ftp.nerim.net/debian-marillat) stable main
deb [ftp://ftp.nerim.net/debian-marillat](ftp://ftp.nerim.net/debian-marillat) unstable main
deb [ftp://ftp.nerim.net/debian-marillat](ftp://ftp.nerim.net/debian-marillat) testing main

deb [http://backports.ubuntuforums.org/ubp](http://backports.ubuntuforums.org/ubp) hoary-backports main universe multiverse restricted
deb [http://backports.ubuntuforums.org/ubp](http://backports.ubuntuforums.org/ubp) hoary-extras main universe multiverse restricted

---

### Post by eyequeue on 2005-05-21
[QUOTE=kingofhell]
i did exactly what is said in [www.ubuntuguide.org]("http://www.ubuntuguide.org")  including 
gpg --keyserver wwwkeys.eu.pgp.net --recv-keys 1F41B907
gpg --armor --export 1F41B907 | sudo apt-key add -[/QUOTE]

That particular key, 1F41B907, is for the marillat repository.

Try those same two lines again, using KeyID 437D05B5 and see if that resolves things for you.

---

### Post by kingofhell on 2005-05-21
[QUOTE=eyequeue]That particular key, 1F41B907, is for the marillat repository.

Try those same two lines again, using KeyID 437D05B5 and see if that resolves things for you.[/QUOTE]
 and what does this problem suggest

W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates/main Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_hoary-updates_main_binary-i386_Packages) - stat (2 No such file or directory)

---

### Post by kingofhell on 2005-05-21
[QUOTE=eyequeue]That particular key, 1F41B907, is for the marillat repository.

Try those same two lines again, using KeyID 437D05B5 and see if that resolves things for you.[/QUOTE]
i dun think so

W: GPG error: [http://sg.archive.ubuntu.com](http://sg.archive.ubuntu.com) hoary-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: You may want to run apt-get update to correct these problems

---

### Post by eyequeue on 2005-05-21
[QUOTE=kingofhell]and what does this problem suggest

W: Couldn't stat source package list [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com") hoary-updates/main Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_hoary-updates_main_binary-i386_Packages) - stat (2 No such file or directory)[/QUOTE]

Rerun 'sudo apt-get update' and that should clear up.

---

### Post by kingofhell on 2005-05-22
[QUOTE=eyequeue]Rerun 'sudo apt-get update' and that should clear up.[/QUOTE]
 unfortunately, it didnt

---

### Post by Xian on 2005-05-22
I took the source list you provided, then commented out some duplicated repos and the marillat repos as their network was down when I attempted to pull from those, and was able to finish an 'sudo apt-get update' with no errors. Listed below is the source.list I used, and next it the apt-get session:

```
#deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted


#deb http://sg.archive.ubuntu.com/ubuntu hoary main restricted
#deb-src http://sg.archive.ubuntu.com/ubuntu hoary main restricted

## Major bug fix updates produced after the final release of the
## distribution.
#deb http://sg.archive.ubuntu.com/ubuntu hoary-updates main restricted
#deb-src http://sg.archive.ubuntu.com/ubuntu hoary-updates main restricted

## Uncomment the following two lines to fetch updated software from the network
deb http://us.archive.ubuntu.com/ubuntu hoary main restricted
deb-src http://us.archive.ubuntu.com/ubuntu hoary main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb http://us.archive.ubuntu.com/ubuntu hoary-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu hoary universe
deb-src http://us.archive.ubuntu.com/ubuntu hoary universe

deb http://security.ubuntu.com/ubuntu hoary-security main restricted
deb-src http://security.ubuntu.com/ubuntu hoary-security main restricted

deb http://security.ubuntu.com/ubuntu hoary-security universe
deb-src http://security.ubuntu.com/ubuntu hoary-security universe

deb http://archive.ubuntu.com/ubuntu hoary multiverse
deb-src http://archive.ubuntu.com/ubuntu hoary multiverse

#deb ftp://ftp.nerim.net/debian-marillat stable main
#deb ftp://ftp.nerim.net/debian-marillat unstable main
#deb ftp://ftp.nerim.net/debian-marillat testing main

deb http://backports.ubuntuforums.org/ubp hoary-backports main universe multiverse restricted
deb http://backports.ubuntuforums.org/ubp hoary-extras main universe multiverse restricted
```

```
$ sudo apt-get update
Ign http://backports.ubuntuforums.org hoary-backports Release.gpg
Ign http://backports.ubuntuforums.org hoary-extras Release.gpg
Ign http://backports.ubuntuforums.org hoary-backports Release
Ign http://backports.ubuntuforums.org hoary-extras Release
Ign http://backports.ubuntuforums.org hoary-backports/main Packages
Ign http://backports.ubuntuforums.org hoary-backports/universe Packages
Ign http://backports.ubuntuforums.org hoary-backports/multiverse Packages
Ign http://backports.ubuntuforums.org hoary-backports/restricted Packages
Ign http://backports.ubuntuforums.org hoary-extras/main Packages
Ign http://backports.ubuntuforums.org hoary-extras/universe Packages
Ign http://backports.ubuntuforums.org hoary-extras/multiverse Packages
Ign http://backports.ubuntuforums.org hoary-extras/restricted Packages
Hit http://backports.ubuntuforums.org hoary-backports/main Packages
Hit http://backports.ubuntuforums.org hoary-backports/universe Packages
Hit http://backports.ubuntuforums.org hoary-backports/multiverse Packages
Hit http://backports.ubuntuforums.org hoary-backports/restricted Packages
Hit http://backports.ubuntuforums.org hoary-extras/main Packages
Hit http://backports.ubuntuforums.org hoary-extras/universe Packages
Hit http://backports.ubuntuforums.org hoary-extras/multiverse Packages
Hit http://backports.ubuntuforums.org hoary-extras/restricted Packages
Get:1 http://us.archive.ubuntu.com hoary Release.gpg [189B]
Get:2 http://us.archive.ubuntu.com hoary-updates Release.gpg [189B]
Hit http://us.archive.ubuntu.com hoary Release
Get:3 http://archive.ubuntu.com hoary Release.gpg [189B]
Hit http://us.archive.ubuntu.com hoary-updates Release
Get:4 http://security.ubuntu.com hoary-security Release.gpg [189B]
Hit http://us.archive.ubuntu.com hoary/main Packages
Hit http://archive.ubuntu.com hoary Release
Hit http://security.ubuntu.com hoary-security Release
Hit http://us.archive.ubuntu.com hoary/restricted Packages
Hit http://us.archive.ubuntu.com hoary/main Sources
Hit http://archive.ubuntu.com hoary/multiverse Packages
Hit http://security.ubuntu.com hoary-security/main Packages
Hit http://us.archive.ubuntu.com hoary/restricted Sources
Hit http://us.archive.ubuntu.com hoary/universe Packages
Hit http://archive.ubuntu.com hoary/multiverse Sources
Hit http://security.ubuntu.com hoary-security/restricted Packages
Hit http://security.ubuntu.com hoary-security/main Sources
Hit http://us.archive.ubuntu.com hoary/universe Sources
Hit http://us.archive.ubuntu.com hoary-updates/main Packages
Hit http://security.ubuntu.com hoary-security/restricted Sources
Hit http://security.ubuntu.com hoary-security/universe Packages
Hit http://security.ubuntu.com hoary-security/universe Sources
Hit http://us.archive.ubuntu.com hoary-updates/restricted Packages
Hit http://us.archive.ubuntu.com hoary-updates/main Sources
Hit http://us.archive.ubuntu.com hoary-updates/restricted Sources
Fetched 192B in 21s (9B/s)
Reading package lists... Done
```

---

