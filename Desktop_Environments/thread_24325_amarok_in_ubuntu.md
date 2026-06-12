---
title: "amarok in ubuntu"
date: 2005-04-06
forum: Desktop Environments
---

### Post by deet on 2005-04-06
I am trying to install amarok in ubuntu and I am having trouble downloading and installing all the dependencies.  I tried to get and use apt-build but this too doesnt work.  

My question is: Is there a way to make resolving all these dependencies easier?

---

### Post by Gandalf on 2005-04-06
[QUOTE=deet]I am trying to install amarok in ubuntu and I am having trouble downloading and installing all the dependencies.  I tried to get and use apt-build but this too doesnt work.  

My question is: Is there a way to make resolving all these dependencies easier?[/QUOTE]
 hmmmm i just apt-get it without any dependicie problem
please quote the output of
sudo apt-get install amarok

---

### Post by deet on 2005-04-06
root@ubuntu:/home/fred # apt-get install amarok
Reading package lists... Done
Building dependency tree... Done
Package amarok is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package amarok has no installation candidate

I have also tried to use amarok_1.2.3-1_i386.deb

Thanks
Fred

---

### Post by Gandalf on 2005-04-06
[QUOTE=deet]root@ubuntu:/home/fred # apt-get install amarok
Reading package lists... Done
Building dependency tree... Done
Package amarok is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package amarok has no installation candidate

I have also tried to use amarok_1.2.3-1_i386.deb

Thanks
Fred[/QUOTE]
 ok it seems that you haven't activate some apt sources do the following
```

sudo mv /etc/apt/sources.list /etc/apt/sources.list_backup
sudo gedit /etc/apt/sources.list &

```

this will open gedit with empty file
copy paste the code below into the file, save and exit
```

deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Preview i386 Binary-1 (20050330)]/ hoary main restricted


deb http://fr.archive.ubuntu.com/ubuntu hoary main restricted
deb-src http://fr.archive.ubuntu.com/ubuntu hoary main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://fr.archive.ubuntu.com/ubuntu hoary-updates main restricted
deb-src http://fr.archive.ubuntu.com/ubuntu hoary-updates main restricted

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

deb ftp://ftp.nerim.net/debian-marillat stable main
deb ftp://ftp.nerim.net/debian-marillat unstable main
deb ftp://ftp.nerim.net/debian-marillat testing main
deb http://backports.ubuntuforums.org/backports hoary-extras main universe multiverse restricted

```

after you save run
```

sudo apt-get update
sudo apt-get install amarok

```

it should work

P.S: thanks for this player i didn't know about it it's cool :D

---

### Post by deet on 2005-04-06
This is what I get when i try to use the debian package
It is very difficult to install all these dependencies one by one because they have their own dependencies and some things like gcc and g++ dont want to install at all.


root@ubuntu:/home/fred/Desktop # dpkg -i amarok_1.2.3-1_i386.deb
Selecting previously deselected package amarok.
(Reading database ... 60059 files and directories currently installed.)
Unpacking amarok (from amarok_1.2.3-1_i386.deb) ...
dpkg: dependency problems prevent configuration of amarok:
 amarok depends on amarok-engines | amarok-engine; however:
  Package amarok-engines is not installed.
  Package amarok-engine is not installed.
 amarok depends on kdelibs4 (>= 4:3.3.2-4.0.2); however:
  Package kdelibs4 is not installed.
 amarok depends on libfontconfig1 (>= 2.3.0); however:
  Version of libfontconfig1 on system is 2.2.3-4ubuntu7.
 amarok depends on libqt3c102-mt (>= 3:3.3.3); however:
  Package libqt3c102-mt is not installed.
 amarok depends on libsqlite3-0 (>= 3.1.6); however:
  Package libsqlite3-0 is not installed.
 amarok depends on libtag1 (>= 1.3.1); however:
  Package libtag1 is not installed.
 amarok depends on libtunepimp2 (>= 0.3.0); however:
  Package libtunepimp2 is not installed.
dpkg: error processing amarok (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 amarok
root@ubuntu:/home/fred/Desktop #

---

### Post by deet on 2005-04-06
sorry it seems we were posting simultaneously

i will try what you suggested now

thank you so much

Fred

---

### Post by deet on 2005-04-06
Still having dependency problems

Here is the output.  I copied the source file above into the blank window and saved as you indicated I should above.

I like this player very much and would love to get it to work.



root@ubuntu:/home/fred # apt-get update
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary Release.gpg [189B]
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary Release.gpg [189B]
Ign [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-extras Release.gpg
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security Release.gpg [189B]
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary Release [19.9kB]
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary Release [19.9kB]
Get:6 [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security Release [16.9kB]
Ign [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-extras Release
Ign [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-extras/main Packages
Get:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/universe Packages [2182kB]
Ign [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-extras/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/main Packages
Hit [ftp://ftp.nerim.net](ftp://ftp.nerim.net) stable Release.gpg
Ign [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-extras/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/universe Sources
Get:8 [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) hoary Release.gpg [189B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/multiverse Packages
Hit [ftp://ftp.nerim.net](ftp://ftp.nerim.net) unstable Release.gpg
Ign [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-extras/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/multiverse Sources
Get:9 [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) hoary-updates Release.gpg [189B]
Get:10 [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-extras/main Packages [20B]
Hit [ftp://ftp.nerim.net](ftp://ftp.nerim.net) testing Release.gpg
Get:11 [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) hoary Release [19.9kB]
Get:12 [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-extras/universe Packages [613B]
Hit [ftp://ftp.nerim.net](ftp://ftp.nerim.net) stable Release
Get:13 [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-extras/multiverse Packages [20B]
Get:14 [ftp://ftp.nerim.net](ftp://ftp.nerim.net) unstable Release [2022B]
Get:15 [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) hoary-updates Release [16.8kB]
Get:16 [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-extras/restricted Packages [1438B]
Get:17 [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) hoary/main Packages [489kB]
Hit [ftp://ftp.nerim.net](ftp://ftp.nerim.net) testing Release
Hit [ftp://ftp.nerim.net](ftp://ftp.nerim.net) stable/main Packages
Get:18 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/universe Sources [866kB]
Hit [ftp://ftp.nerim.net](ftp://ftp.nerim.net) unstable/main Packages
Hit [ftp://ftp.nerim.net](ftp://ftp.nerim.net) testing/main Packages
Get:19 [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) hoary/restricted Packages [4374B]
Get:20 [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) hoary/main Sources [175kB]
Get:21 [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) hoary/restricted Sources [1320B]
Get:22 [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) hoary-updates/main Packages [14B]
Get:23 [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) hoary-updates/restricted Packages [14B]
Get:24 [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) hoary-updates/main Sources [14B]
Get:25 [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) hoary-updates/restricted Sources [14B]
Fetched 3815kB in 24s (154kB/s)
Reading package lists... Done
root@ubuntu:/home/fred # apt-get install amarok
Reading package lists... Done
Building dependency tree... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  amarok: Depends: amarok-arts but it is not going to be installed or
                   amarok-engines but it is not going to be installed or
                   amarok-engine
          Depends: kdelibs4 (>= 4:3.4.0) but it is not going to be installed
          Depends: libqt3c102-mt (>= 3:3.3.3) but it is not going to be installed
          Depends: libsqlite3-0 (>= 3.0.8) but it is not going to be installed
          Depends: libtag1 (>= 1.3.1) but it is not going to be installed
          Depends: libtunepimp2 (>= 0.3.0) but it is not going to be installed
  apt-build: Depends: gcc but it is not going to be installed
             Depends: g++ but it is not going to be installed
             Depends: libappconfig-perl (>= 1.5) but it is not going to be installed
             Depends: libapt-pkg-perl (>= 0.1.11) but it is not going to be installed
             Depends: devscripts but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
root@ubuntu:/home/fred #

---

### Post by deet on 2005-04-06
Sorry

the answer was right there i guess

i simply ran 

apt-get -f install

and it worked

can anyone tell me what this -f switch does and why this wouldn't run properly right off the bat

Thanks for your help Gandalf

Fred

---

### Post by Gandalf on 2005-04-06
[QUOTE=deet]Sorry

the answer was right there i guess

i simply ran 

apt-get -f install

and it worked

can anyone tell me what this -f switch does and why this wouldn't run properly right off the bat

Thanks for your help Gandalf

Fred[/QUOTE]
 apt-get -f install it just force the install of the dependicie of the last apt-get install task runned... (i hope i'm not saying crap here :D )

BTW i think you will have to [color=blue]sudo apt-get install amarok*[/color] to install all it's related things (not so much but you need the package amarok-gstreamer) to be able to play and hear music (must go to Settings -> Configure amaroK -> engine and select "esdsink" in the output drop box)

---

### Post by Gandalf on 2005-04-06
BTW the sources.list i gave you have the sources in france since i'm living there so do the following
```
sudo mv /etc/apt/sources.list /etc/sources.list_french
sudo mv /etc/apt/sources.list_backup /etc/apt/sources.list
sudo gedit /etc/apt/sources.list &
sudo gedit /etc/apt/sources.list_french &
```

and try making the soures.list look like sourced.list_french without changing the sources!!

---

### Post by deet on 2005-04-06
Does someone have a source file in English I can copy?  If one was posted Im sure it would help the multitude of users like me.

Thanks 
Fred

---

### Post by Gandalf on 2005-04-06
[QUOTE=deet]Does someone have a source file in English I can copy?  If one was posted Im sure it would help the multitude of users like me.

Thanks 
Fred[/QUOTE]
 well actually you have it (/etc/apt/sources.list_backup) just uncomment the line BTW the sources.list i gave you doesn't load the packages in french language if that's what you afraid of, but it's only better to choose a mirror in the same country (near) you to download packages faster nothing more... you can keep the one i gave you but i think it will be a little bit slower if you're far away from france

---

### Post by deet on 2005-04-06
that was what I was afraid of.  I have done what you suggested and have closer sources now.

Thanks for your help Gandalf and BTW I like your site.  Don't worry its not too dark.

Fred

---

### Post by Gandalf on 2005-04-06
[QUOTE=deet]that was what I was afraid of.  I have done what you suggested and have closer sources now.

Thanks for your help Gandalf and BTW I like your site.  Don't worry its not too dark.

Fred[/QUOTE]
 no problem man... and thx :oops: lol :lol:

---

