---
title: "How do I install wine?"
date: 2005-08-02
forum: Desktop Environments
---

### Post by Navyblue on 2005-08-02
How do I install wine? I get this when doing apt-get:

```

navyblue@PC:~$ sudo apt-get install wine
Password:
Reading package lists... Done
Building dependency tree... Done
Package wine is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package wine has no installation candidate

```

Thanks in advance. :)

---

### Post by heimo on 2005-08-02
wine is in universe, which means you probably need to add universe to your sources, see here:

[https://wiki.ubuntu.com/UniversePackages?highlight=%28universe%29](https://wiki.ubuntu.com/UniversePackages?highlight=%28universe%29)
[http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=wine&searchon=names&subword=1&version=hoary&release=all](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=wine&searchon=names&subword=1&version=hoary&release=all)

---

### Post by Navyblue on 2005-08-02
[QUOTE=heimo]wine is in universe, which means you probably need to add universe to your sources, see here:

[https://wiki.ubuntu.com/UniversePackages?highlight=%28universe%29](https://wiki.ubuntu.com/UniversePackages?highlight=%28universe%29)
[http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=wine&searchon=names&subword=1&version=hoary&release=all](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=wine&searchon=names&subword=1&version=hoary&release=all)[/QUOTE]
 I have enabled the universe repository, and even the multiverse.

If I were to add the repository stated in the wine website I am able to see "winetool" from synaptic. However if I try to install it says:

```

winetools:
 Depends: wine (>=0.0.20040914) but it is not installable
 Depends: xdialog  but it is not installable
 Depends: gtk-smooth-themes  but it is not installable

```

And also, while downloading the package list synaptic also says

```

http://wine.sourceforge.net/apt/source/deb/Sources.gz: 404 Not Found

```

---

### Post by heimo on 2005-08-02
You don't need that sourceforge in sources.list. Can you post your /etc/apt/sources.list? Have you checked that your mirror has the package? And you ran *sudo apt-get update* after changing sources.list? It should be quite straightforward.

---

### Post by Navyblue on 2005-08-02
Here is my /etc/apt/sources.lst.

```

deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release amd64 (20050407)]/ hoary main restricted


deb-src http://sg.archive.ubuntu.com/ubuntu hoary main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://sg.archive.ubuntu.com/ubuntu hoary-updates main restricted
deb-src http://sg.archive.ubuntu.com/ubuntu hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.

# deb http://sg.archive.ubuntu.com/ubuntu hoary-updates universe
# deb-src http://sg.archive.ubuntu.com/ubuntu hoary-updates universe

deb http://security.ubuntu.com/ubuntu hoary-security main restricted
deb-src http://security.ubuntu.com/ubuntu hoary-security main restricted

# deb http://security.ubuntu.com/ubuntu hoary-security universe
# deb-src http://security.ubuntu.com/ubuntu hoary-security universe

deb http://wine.sourceforge.net/apt/ binary/
deb-src http://wine.sourceforge.net/apt/ source/deb/
deb http://sg.archive.ubuntu.com/ubuntu/ hoary main restricted universe multiverse
deb-src http://sg.archive.ubuntu.com/ubuntu/ hoary main restricted universe multiverse

```

---

### Post by Lord Illidan on 2005-08-02
Try using synaptic..

---

### Post by Navyblue on 2005-08-02
[QUOTE=Lord Illidan]Try using synaptic..[/QUOTE]
 Yep I did. The error message is described in post #3.

---

### Post by heimo on 2005-08-02
You have some parts overlapping in your sources.list - you could use this as a template:
[http://ubuntuguide.org/#extrarepositories]("http://ubuntuguide.org/#extrarepositories")

And then just apt-get or use synaptic. Oh, and take those sourceforge lines off that sources.list to avoid problems.

---

### Post by Navyblue on 2005-08-02
Did as the webbie says. I even tried the us mirror to copy the site. Now I can't even find anything that contains the word "wine" under the name and description. I was able to fine the wine documentation before (yes only the documentation file). :D

---

### Post by heimo on 2005-08-02
Post any error messages you get. And run
 ```
sudo apt-get update
sudo apt-cache search wine

```

---

### Post by Navyblue on 2005-08-02
[QUOTE=heimo]Post any error messages you get. And run
 ```
sudo apt-get update
sudo apt-cache search wine

```[/QUOTE]
 Here it goes.

```

navyblue@PC:~$ sudo apt-get update
Get:1 http://security.ubuntu.com hoary-security Release.gpg [189B]
Get:2 http://sg.archive.ubuntu.com hoary-updates Release.gpg [189B]
Get:3 http://sg.archive.ubuntu.com hoary Release.gpg [189B]
Hit http://sg.archive.ubuntu.com hoary-updates Release
Hit http://sg.archive.ubuntu.com hoary Release
Get:4 http://security.ubuntu.com hoary-security Release [16.9kB]
Ign http://security.ubuntu.com hoary-security Release
Hit http://security.ubuntu.com hoary-security/main Packages
Hit http://sg.archive.ubuntu.com hoary-updates/main Packages
Hit http://sg.archive.ubuntu.com hoary-updates/restricted Packages
Hit http://sg.archive.ubuntu.com hoary-updates/main Sources
Hit http://sg.archive.ubuntu.com hoary-updates/restricted Sources
Hit http://sg.archive.ubuntu.com hoary-updates/universe Packages
Hit http://sg.archive.ubuntu.com hoary-updates/universe Sources
Hit http://sg.archive.ubuntu.com hoary/multiverse Packages
Hit http://sg.archive.ubuntu.com hoary/multiverse Sources
Hit http://security.ubuntu.com hoary-security/restricted Packages
Hit http://security.ubuntu.com hoary-security/main Sources
Hit http://security.ubuntu.com hoary-security/restricted Sources
Hit http://security.ubuntu.com hoary-security/universe Packages
Hit http://security.ubuntu.com hoary-security/universe Sources
Fetched 16.9kB in 6s (2619B/s)
Reading package lists... Done
W: GPG error: http://security.ubuntu.com hoary-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: You may want to run apt-get update to correct these problems
navyblue@PC:~$ sudo apt-cache search wine
navyblue@PC:~$ 

```

---

### Post by heimo on 2005-08-02
Oh... I think you should post this question on this AMD64 forum...
[http://ubuntuforums.org/forumdisplay.php?f=60](http://ubuntuforums.org/forumdisplay.php?f=60)

I really didn't notice before re-reading your sources.list again. There's probably no amd64 version precompiled. I don't know how you folks do it, but as I've understood, you need to do some tricks and magic to use 32-bit versions of packages. Or compile. Or install from some other source.

But that's basicly your problem. :-/ :-\ Hmm... Really, you should ask this on the other forum (or search forum) for AMD64 and wine. "How do I install Wine on AMD64". Hopefully this helps.

---

### Post by Navyblue on 2005-08-02
[QUOTE=heimo]Oh... I think you should post this question on this AMD64 forum...
[http://ubuntuforums.org/forumdisplay.php?f=60](http://ubuntuforums.org/forumdisplay.php?f=60)

I really didn't notice before re-reading your sources.list again. There's probably no amd64 version precompiled. I don't know how you folks do it, but as I've understood, you need to do some tricks and magic to use 32-bit versions of packages. Or compile. Or install from some other source.

But that's basicly your problem. :-/ :-\ Hmm... Really, you should ask this on the other forum (or search forum) for AMD64 and wine. "How do I install Wine on AMD64". Hopefully this helps.[/QUOTE]

Thanks a lot for your help. I do notice a couple of other softwares "missing" as well, so i guess you are right. Will ask this on the AMD 64 forum.

---

### Post by Lord Illidan on 2005-08-02
All you have to do is get the source from the Wine Homepage and compile it on your system. Nothing way too advanced, but it might take some time....

---

### Post by Navyblue on 2005-08-02
Just read from the other thread on AMD 64 Ubuntu forum that it seems impossible right now to compile Wine on 64 bit system. Don't ask me why, I won't understand anyway. :p

I have tried it by following instruction on the wine website and the process got halted as it can't download a component.

---

