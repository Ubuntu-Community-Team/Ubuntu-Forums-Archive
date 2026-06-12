---
title: "Problems Installing Koffice 1.4"
date: 2005-06-28
forum: Desktop Environments
---

### Post by Darren Crotchett on 2005-06-28
I've been having problems installing Koffice.  I have added:
deb [http://kubuntu.org/hoary-koffice14](http://kubuntu.org/hoary-koffice14) hoary-updates main

to my sources.list and ran apt-get update.  But, whenever I do:  apt-get install koffice, I get:

root@laptop:/home/backdoc # apt-get install koffice
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  koffice: Depends: karbon (>= 1:1.4.0-0ubuntu0hoary2) but it is not going to be installed
           Depends: kchart (>= 1:1.4.0-0ubuntu0hoary2) but it is not going to be installed
           Depends: kformula (>= 1:1.4.0-0ubuntu0hoary2) but it is not going to be installed
           Depends: kivio (>= 1:1.4.0-0ubuntu0hoary2) but it is not going to be installed
           Depends: koshell (>= 1:1.4.0-0ubuntu0hoary2) but it is not going to be installed
           Depends: kpresenter (>= 1:1.4.0-0ubuntu0hoary2) but it is not going to be installed
           Depends: kspread (>= 1:1.4.0-0ubuntu0hoary2) but it is not going to be installed
           Depends: kugar (>= 1:1.4.0-0ubuntu0hoary2) but it is not going to be installed
           Depends: kword (>= 1:1.4.0-0ubuntu0hoary2) but it is not going to be installed
           Depends: krita (>= 1:1.4.0-0ubuntu0hoary2) but it is not going to be installed
E: Broken packages


If I try to install any of the individual packages, I get errors, too.  I even tried downloading the *.deb for kubuntu and running dpkg on it.  Still no joy.  Any suggestions?

TIA,
Darren

---

### Post by Xian on 2005-06-28
koffice is located in the Universe repos. 
Do you have those enabled?

See how to add [extra repositories](http://ubuntuguide.org/#extrarepositories)

Here's my output from that same command:
```
$ sudo apt-get install koffice
Password:
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  karbon kchart kformula kivio kivio-data koffice-data koffice-libs koshell
  kpresenter kspread kugar kword latex-xft-fonts libwv2-1 python2.3
Suggested packages:
  koffice-doc-html koffice-i18n koffice-dev wordnet tetex-extra python2.3-doc
  python2.3-profiler
Recommended packages:
  openoffice.org-mimelnk python2.3-iconvcodec python2.3-cjkcodecs
  python2.3-japanese-codecs
The following NEW packages will be installed:
  karbon kchart kformula kivio kivio-data koffice koffice-data koffice-libs
  koshell kpresenter kspread kugar kword latex-xft-fonts libwv2-1 python2.3
0 upgraded, 16 newly installed, 0 to remove and 1 not upgraded.
Need to get 17.4MB of archives.
After unpacking 59.8MB of additional disk space will be used.
Do you want to continue [Y/n]?
```

---

### Post by SGC on 2005-06-28
> koffice is located in the Universe repos.
The universe repository have the old version (1.3)

Try to do the following:
```

sudo apt-get install koffice kchart kformula kivio koshell kpresenter kspread kugar kword krita 

```

If it does not works then post the contents of your /etc/apt/sources.list

---

### Post by Darren Crotchett on 2005-06-28
[QUOTE=SGC]The universe repository have the old version (1.3)

Try to do the following:
```

sudo apt-get install koffice kchart kformula kivio koshell kpresenter kspread kugar kword krita 

```

If it does not works then post the contents of your /etc/apt/sources.list[/QUOTE]

Thanks to all for the suggestions.  This didn't work. And, I might should mention that the source listing mentioned at the [http://www.kubuntu.org/hoary-koffice-14.php](http://www.kubuntu.org/hoary-koffice-14.php) page gives errors, as well.  That is, deb [http://download.kde.org/pub/kde/stable/koffice-1.4/kubuntu](http://download.kde.org/pub/kde/stable/koffice-1.4/kubuntu) hoary-updates main, doesn't work.

So, here's my sources file:

root@laptop:/home/backdoc # cat /etc/apt/sources.list
deb cdrom:[Kubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted


deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted

## Major bug fix updates produced after the final release of the
## distribution.
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

# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

deb [http://kubuntu.org/hoary-koffice14](http://kubuntu.org/hoary-koffice14) hoary-updates main

---

### Post by Xian on 2005-06-28
Since my source list is working why don't you try it and see if you can get a better result? 

First rename your's just to preserve a backup.
```
 $ sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup
```
Here is my sources.list. 
Copy/Paste it into a text editor and use as your own.

EDIT: Afterwards be sure to run a '$ sudo apt-get update' session.

```
#deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb http://archive.ubuntu.com/ubuntu hoary-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
deb-src http://archive.ubuntu.com/ubuntu/ hoary main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu/ hoary main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu hoary-security main restricted universe
deb-src http://security.ubuntu.com/ubuntu hoary-security main restricted universe

##Backports
deb ftp://ftp2.caliu.info/backports/ hoary-extras main universe multiverse restricted
deb ftp://ftp2.caliu.info/backports/ hoary-backports main universe multiverse restricted

```

---

### Post by SGC on 2005-06-28
koffice-libs depends on a version of kdelibs4 that >= 3.4.1 , So I think you need to update your version of kde to 3.4.1 in order to install koffice, add this to sources.list:
```

deb http://kubuntu.org/hoary-kde341 hoary-updates main

```

Then:
sudo apt-get update
sudo apt-get koffice

---

### Post by Darren Crotchett on 2005-06-28
[QUOTE=Xian]Since my source list is working why don't you try it and see if you can get a better result? 

First rename your's just to preserve a backup.
```
 $ sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup
```
Here is my sources.list. 
Copy/Paste it into a text editor and use as your own.
```
#deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb http://archive.ubuntu.com/ubuntu hoary-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
deb-src http://archive.ubuntu.com/ubuntu/ hoary main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu/ hoary main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu hoary-security main restricted universe
deb-src http://security.ubuntu.com/ubuntu hoary-security main restricted universe

##Backports
deb ftp://ftp2.caliu.info/backports/ hoary-extras main universe multiverse restricted
deb ftp://ftp2.caliu.info/backports/ hoary-backports main universe multiverse restricted

```

EDIT: Afterwards be sure to run a '$ sudo apt-get update' session.[/QUOTE]

Oh yeah.  I did the update.  And, I appreciate it.  But, it gives me 1.3.  I'm wanting to get 1.4.

My sources.list is the default (I think) except for what they recommended on the kubuntu page.  And, as I mentioned, one of them didn't work.  I'm surprised that I don't see any other posts with the same problem.

I'll check back tomorrow.  I've got to quit for this evening.  

Thanks,
Darren

PS.  It is very difficult to copy the text from those text boxes.

---

### Post by Xian on 2005-06-28
[QUOTE=Darren Crotchett]PS.  It is very difficult to copy the text from those text boxes.[/QUOTE]
Change the font that your browser uses to render web pages. 
I use the Times New Roman (sz 13).

---

### Post by McAviti on 2005-06-29
[QUOTE=Darren Crotchett]Oh yeah.  I did the update.  And, I appreciate it.  But, it gives me 1.3.  I'm wanting to get 1.4.

My sources.list is the default (I think) except for what they recommended on the kubuntu page.  And, as I mentioned, one of them didn't work.  I'm surprised that I don't see any other posts with the same problem.
[/QUOTE]

Don't be surprised, look at my post. [http://ubuntuforums.org/showthread.php?t=44440](http://ubuntuforums.org/showthread.php?t=44440) ;)

I have pretty the same error like you, only that I'm running on a system with German language. But good to know that it's not a language dependent problem, because that's what I suspected first. If I happen to fall over a solution I'll let you know here in this thread as well.

---

### Post by ltmon on 2005-06-29
[QUOTE=SGC]koffice-libs depends on a version of kdelibs4 that >= 3.4.1 , So I think you need to update your version of kde to 3.4.1 in order to install koffice, add this to sources.list:
```

deb http://kubuntu.org/hoary-kde341 hoary-updates main

```

Then:
sudo apt-get update
sudo apt-get koffice[/QUOTE]

SGC has it right.

I would update KDE seperately to 3.4.1 before doing koffice just in case there are problems.  Then do koffice.

L.

---

### Post by Darren Crotchett on 2005-06-29
[QUOTE=ltmon]SGC has it right.

I would update KDE seperately to 3.4.1 before doing koffice just in case there are problems.  Then do koffice.

L.[/QUOTE]

I went back to my old sources.list and made sure that (deb [http://kubuntu.org/hoary-kde341](http://kubuntu.org/hoary-kde341) hoary-updates main) was in my sources.list.  This time it worked.  I did have to remove the reference to the cdrom from sources.list first, though.

Thanks for all of the help.  It is apparently installing right now.   We'll see.

Darren

For anyone else having problems, here's my sources.list file.


backdoc@laptop:~$ cat /etc/apt/sources.list
# deb cdrom:[Kubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted


deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted

## Major bug fix updates produced after the final release of the
## distribution.
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

deb [http://kubuntu.org/hoary-kde341](http://kubuntu.org/hoary-kde341) hoary-updates main

# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

deb [http://kubuntu.org/hoary-koffice14](http://kubuntu.org/hoary-koffice14) hoary-updates main

---

### Post by Darren Crotchett on 2005-06-29
[QUOTE=McAviti]Don't be surprised, look at my post. [http://ubuntuforums.org/showthread.php?t=44440](http://ubuntuforums.org/showthread.php?t=44440) ;)

I have pretty the same error like you, only that I'm running on a system with German language. But good to know that it's not a language dependent problem, because that's what I suspected first. If I happen to fall over a solution I'll let you know here in this thread as well.[/QUOTE]

I saw your post.  I thought it was the same problem.  But, I don't speak/read German.

I think I have a working sources.list file.  See my reply below.

Let me know if it helps you, too.

Darren

---

### Post by Darren Crotchett on 2005-06-29
[QUOTE=Xian]Change the font that your browser uses to render web pages. 
I use the Times New Roman (sz 13).[/QUOTE]

My fonts are about like yours, and the text boxes are still difficult to select text with the mouse because they have scrollbars and there is no auto scrolling to accomodate text that is outside the bounds of the box.  Also, Ctrl+A selects the entire page.  So, it is very difficult to select it.

[Here's a screenshot](http://orca.st.usm.edu/~dcrotche/desktop.jpg)

---

### Post by McAviti on 2005-06-30
Darren!

[QUOTE=Darren Crotchett]I saw your post.  I thought it was the same problem.  But, I don't speak/read German.

I think I have a working sources.list file.  See my reply below.

Let me know if it helps you, too.

Darren[/QUOTE]

Ok, that source for kde 3.4.1 did the trick. Would be maybe worth on that page ([http://kubuntu.org/hoary-koffice-14.php](http://kubuntu.org/hoary-koffice-14.php)) mentioning it. :)

thanx a lot!
~klemens

---

