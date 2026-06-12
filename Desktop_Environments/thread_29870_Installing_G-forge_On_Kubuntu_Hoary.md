---
title: "Installing G-forge On Kubuntu Hoary"
date: 2005-04-26
forum: Desktop Environments
---

### Post by mad_logic on 2005-04-26
sudo apt-get install gforge

I've been trying to install gforge with the default sources.list but I get the following error:

"The following packages have unmet dependencies:
  gforge: Depends: gforge-lists-mailman but it is not going to be installed or
                              gforge-lists
E: Broken packages"

I dont understand why its doing this.

After a while I added more sources to my sources file:

deb [http://gforge.grazian.org/debian](http://gforge.grazian.org/debian) stable/
deb-src [http://gforge.grazian.org/debian](http://gforge.grazian.org/debian) stable/
deb [http://people.debian.org/~bayle/debian](http://people.debian.org/~bayle/debian) binary-i386/

then updated

sudo apt-get update

and then finally tried installing again but this time I got a different error:

The following packages have unmet dependencies:
  gforge: Depends: gforge-lists-mailman (= 3.3.0-3woody6) but it is not going to be installed or
                   gforge-lists (= 3.3.0-3woody6)
E: Broken packages

 ](*,)

---

### Post by cdhotfire on 2005-04-26
[Right Here]("http://ftp.us.debian.org/debian/pool/main/g/gforge/gforge-lists-mailman_3.1-30_all.deb")
Download this then do
```

$ cd /folder where .deb is at/
$ sudo dpkg -i [size=2]gforge-lists-mailman_3.1-30_all.deb

```

that should do it :)
[/size]

---

### Post by mad_logic on 2005-04-26
I installed the gforge-lists-mailman package that you said I should download, but then it gave me these errors when I tried installing it, I'm completely lost at this stage on what to do next, thanx for pushing me in the right direction.

(Reading database ... 60931 files and directories currently installed.)
Preparing to replace gforge-lists-mailman 3.1-30 (using gforge-lists-mailman_3.1-30_all.deb) ...
Unpacking replacement gforge-lists-mailman ...
dpkg: dependency problems prevent configuration of gforge-lists-mailman:
 gforge-lists-mailman depends on gforge-common; however:
  Package gforge-common is not installed.
 gforge-lists-mailman depends on gforge-db-postgresql | gforge-db; however:
  Package gforge-db-postgresql is not installed.
  Package gforge-db is not installed.
 gforge-lists-mailman depends on gforge-ldap-openldap | gforge-ldap; however:
  Package gforge-ldap-openldap is not installed.
  Package gforge-ldap is not installed.
 gforge-lists-mailman depends on gforge-mta-exim4 | gforge-mta; however:
  Package gforge-mta-exim4 is not installed.
  Package gforge-mta is not installed.
 gforge-lists-mailman depends on apache (>= 1.3.9) | apache-ssl (>= 1.3.9) | apache-perl (>= 1.3.9); however:
  Package apache is not installed.
  Package apache-ssl is not installed.
  Package apache-perl is not installed.
 gforge-lists-mailman depends on libdbi-perl; however:
  Package libdbi-perl is not installed.
 gforge-lists-mailman depends on libdbd-pg-perl; however:
  Package libdbd-pg-perl is not installed.
 gforge-lists-mailman depends on mailman (>= 2.1-3); however:
  Package mailman is not installed.
dpkg: error processing gforge-lists-mailman (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 gforge-lists-mailman

**Have you installed gforge on your system, if yes could you please tell me which steps you followed to get a running gforge system. Thanx in advance**

---

### Post by cdhotfire on 2005-04-26
Okay, do
```

$ sudo gedit /etc/apt/sources.list

```

add this:
```

deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted



## Major bug fix updates produced after the final release of the
## distribution.

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.

deb http://archive.ubuntu.com/ubuntu/ hoary main restricted universe multiverse
deb http://security.ubuntu.com/ubuntu/ hoary-security main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu/ hoary-updates main restricted universe multiverse

deb http://backports.ubuntuforums.org/backports hoary-backports main universe multiverse restricted 
deb http://backports.ubuntuforums.org/backports hoary-extras main universe multiverse restricted

```

then do
```

$ sudo apt-get update
$ sudo apt-get install gforge

```

that should do it. :)

---

### Post by mad_logic on 2005-04-27
[QUOTE=cdhotfire]Okay, do
```

$ sudo gedit /etc/apt/sources.list

```

add this:
```

deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted



## Major bug fix updates produced after the final release of the
## distribution.

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.

deb http://archive.ubuntu.com/ubuntu/ hoary main restricted universe multiverse
deb http://security.ubuntu.com/ubuntu/ hoary-security main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu/ hoary-updates main restricted universe multiverse

deb http://backports.ubuntuforums.org/backports hoary-backports main universe multiverse restricted 
deb http://backports.ubuntuforums.org/backports hoary-extras main universe multiverse restricted

```

then do
```

$ sudo apt-get update
$ sudo apt-get install gforge

```

that should do it. :)[/QUOTE]
 Thanx a lot dude, it's busy downloading the packages, it seems like its gonna go through just fine. Ill keep you posted.

---

### Post by mad_logic on 2005-04-27
Thanx for the sources dude, I think that was the problem, cause the ones I got from the gforge wesite were giving me errors.

Anyways it downloaded all the packages...i think, then it took me through the LDAP config and a few other configs, but it seems to get stuck. I tried sudo apt-get install gforge for the second time it took me through more configs but then it got stuck again with the following errors:

dpkg: dependency problems prevent configuration of gforge:
 gforge depends on gforge-web-apache | gforge-web; however:
  Package gforge-web-apache is not configured yet.
  Package gforge-web is not installed.
  Package gforge-web-apache which provides gforge-web is not configured yet.
dpkg: error processing gforge (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 gforge-web-apache
 gforge

I have no clue on what to do next, thanx again for your help mate...

---

### Post by cdhotfire on 2005-04-30
[QUOTE=mad_logic]Thanx for the sources dude, I think that was the problem, cause the ones I got from the gforge wesite were giving me errors.

Anyways it downloaded all the packages...i think, then it took me through the LDAP config and a few other configs, but it seems to get stuck. I tried sudo apt-get install gforge for the second time it took me through more configs but then it got stuck again with the following errors:

dpkg: dependency problems prevent configuration of gforge:
 gforge depends on gforge-web-apache | gforge-web; however:
  Package gforge-web-apache is not configured yet.
  Package gforge-web is not installed.
  Package gforge-web-apache which provides gforge-web is not configured yet.
dpkg: error processing gforge (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 gforge-web-apache
 gforge

I have no clue on what to do next, thanx again for your help mate...[/QUOTE]

hmm, try
```

$ sudo dpkg-reconfigure gforge-web-apache

```

seems that this is the package that is causing problems.

---

### Post by mad_logic on 2005-05-03
I executed the sudo dpkg-reconfigure gforge-web-apache

I got this error
/usr/sbin/dpkg-reconfigure: gforge-web-apache is broken or not fully installed


 ](*,)

---

### Post by cdhotfire on 2005-05-04
```

$ sudo apt-get install gforce-web
$ sudo apt-get install gforce-web-apache

```

?

---

### Post by mad_logic on 2005-05-17
I uninstalled Hoary and install Warty and everything ran perfectly.
 [-X

---

### Post by cdhotfire on 2005-05-17
lol, nice, i couldnt be of more help.:???:

---

### Post by mc_cgp on 2005-05-18
[QUOTE=mad_logic]I uninstalled Hoary and install Warty and everything ran perfectly.
 [-X[/QUOTE]


Hi,

Did you installed version 3.1? do you have an how-to?

TIA

---

