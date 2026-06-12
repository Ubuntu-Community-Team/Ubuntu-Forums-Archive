---
title: "kdelibs build problems"
date: 2010-11-09
forum: Desktop Environments
---

### Post by t_echtenkamp on 2010-11-09
Hi - new to posting here, so go easy :)

I'm trying to build kdelibs and running into some problems. I'm following the guide [here]("http://techbase.kde.org/Getting_Started/Build/KDE4#kdelibs") and getting stuck on the "cmakekde .." step. The problem that I am having is that my version of Soprano is being detected as too old:

Soprano version 2.5.2 is too old. Please install 2.5.60 or newer

So I got Soprano from the git repository 'git clone git://git.kde.org/soprano' and built it. My question is, how do I get the cmake to recognise that I have version 2.5.63 and not 2.5.2? Where do I put which files, or which environment variables do I set, or what options do I need to pass to cmake? I've tried a bunch of things already, but to no avail.

Thanks for any help.

---

### Post by t_echtenkamp on 2010-11-10
I got this figured out finally. 

I had to make a debian package out of the updated source from the repository, and then install that package with dpkg.

I used the guide [here]("http://www.debian.org/doc/manuals/maint-guide/ch-update.en.html") in section 9.3 and then section 6.1 to figure out how to package it into a debian package.

Cheers.

---

