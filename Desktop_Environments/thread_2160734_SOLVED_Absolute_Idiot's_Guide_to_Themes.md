---
title: "SOLVED: Absolute Idiot's Guide to Themes?"
date: 2013-07-08
forum: Desktop Environments
---

### Post by alphaamanitin on 2013-07-08
Hello Forum,

I don't know why, but I just am having a hard time wrapping my head around editing themes.  I have read about it, but I need guide that is for a 3 year old or something.  My real problem is that I like the default Greybird and the like, but in LibreOffice Math the buttons in the "elements" toolbar are not very visible, but if I put on something like a dark one, I don't like the looks that much.  

Thanks,

AlphaA

---

### Post by Peripheral Visionary on 2013-07-08
[Here]("http://wiki.xfce.org/howto/xfwm4_theme") is one that might help, and [here]("http://forum.xfce.org/viewtopic.php?id=6770") is one with some screen shots and stuff to help you visualize things.

---

### Post by vasa1 on 2013-07-08
> **alphaamanitin said:**
> ... but in LibreOffice Math the buttons in the "elements" toolbar are not very visible, but if I put on something like a dark one, I don't like the looks that much.  
...
Could you put up an image? I have LibreOffice 4, but I don't see an "elements" toolbar. There's a sort of panel which looks like this (using default Greybird)

---

### Post by alphaamanitin on 2013-07-08
Well, usig the default settings, and most of the settings that are not dark themes my menu is crap.  I cannot figure out why it is this way, any thoughts?

AlphaA

---

### Post by Toz on 2013-07-09
This is definitely not normal. Which version of Xubuntu and libreoffice are you using?

Have you made any changes to the default greybird theme?

Have you added any gtk hacks to either /etc/gtk-2.0/gtkrc or $HOME/.gtkrc-2.0? Perhaps you can post the contents of those two file.

Have you made any changes to libreoffice appearance settings (Tools->Options->Libreoffice->Appearance)?

---

### Post by alphaamanitin on 2013-07-09
I am running Xubuntu 12.04 LTS on a Pan9 System76 laptop.  To my knowledge I have changed nothing.  I have installed some themes, but I have not customized anything in regards to the xubuntu theme or the LibreOffice appearance.  When I get back home I will check the files you suggest and post them.  

I can say this though; recently I was away from the net for 10 days and built up 41 updates.  It wanted to to a partial update, which I did, then did a full update.  After that, LibreOffice was gone, and attempting to reinstall via apt-get would not work.  It said I was missing certain libreoffice dependancies.  I, therefore, downloaded LibreOffice 4 AMD64 from the LibreOffice homepage and followed the instructions for installing from the *.deb files.  I then installed the local help .deb, and the result, is as you see, crappy icons.  I will also post a screen of the icons in writer.  They are awful, clearly visible, but awful.  I hate the way they look, and I don't remember having this problem when I first installed LibreOffice 4 (the installation I had before I did the partial update I just mentioned, and was installed in the same way as the newest installation).

Maybe I can get this resolved, I have not been happy with the overall look of my installation.  

Thanks,

AlphaA

---

### Post by Toz on 2013-07-09
> **alphaamanitin said:**
> I can say this though; recently I was away from the net for 10 days and built up 41 updates.  It wanted to to a partial update, which I did, then did a full update.  After that, LibreOffice was gone, and attempting to reinstall via apt-get would not work.  It said I was missing certain libreoffice dependancies.  

Can you aso post back the results of:
```
sudo apt-get update
```
...and
```
sudo apt-get install libreoffice
```

---

### Post by alphaamanitin on 2013-07-09
Okay, so, no files for the gtkrc you asked for.  This is what I do have ```
user@Q:~$ ls /etc/gtk-2.0/
im-multipress.conf
user@Q:~$ ls /etc/gtk-3.0/
im-multipress.conf  settings.ini 
```

For my $HOME: I only have $HOME/.gtk-bookmarks

Now for the updates:

```
Hit http://us.archive.ubuntu.com precise Release.gpg
Hit http://us.archive.ubuntu.com precise-updates Release.gpg
Hit http://us.archive.ubuntu.com precise-backports Release.gpg
Hit http://security.ubuntu.com precise-security Release.gpg
Hit http://security.ubuntu.com precise-security Release
Hit http://us.archive.ubuntu.com precise Release
Hit http://us.archive.ubuntu.com precise-updates Release
Hit http://us.archive.ubuntu.com precise-backports Release
Hit http://security.ubuntu.com precise-security/main Sources
Hit http://security.ubuntu.com precise-security/restricted Sources
Hit http://security.ubuntu.com precise-security/universe Sources
Hit http://security.ubuntu.com precise-security/multiverse Sources
Hit http://security.ubuntu.com precise-security/main amd64 Packages
Hit http://security.ubuntu.com precise-security/restricted amd64 Packages
Hit http://security.ubuntu.com precise-security/universe amd64 Packages
Hit http://security.ubuntu.com precise-security/multiverse amd64 Packages
Hit http://us.archive.ubuntu.com precise/main Sources
Hit http://us.archive.ubuntu.com precise/restricted Sources
Hit http://security.ubuntu.com precise-security/main i386 Packages
Hit http://security.ubuntu.com precise-security/restricted i386 Packages
Hit http://security.ubuntu.com precise-security/universe i386 Packages
Hit http://us.archive.ubuntu.com precise/universe Sources
Hit http://us.archive.ubuntu.com precise/multiverse Sources
Hit http://us.archive.ubuntu.com precise/main amd64 Packages
Hit http://us.archive.ubuntu.com precise/restricted amd64 Packages
Hit http://us.archive.ubuntu.com precise/universe amd64 Packages
Hit http://us.archive.ubuntu.com precise/multiverse amd64 Packages
Hit http://us.archive.ubuntu.com precise/main i386 Packages
Hit http://us.archive.ubuntu.com precise/restricted i386 Packages
Hit http://extras.ubuntu.com precise Release.gpg
Hit http://ppa.launchpad.net precise Release.gpg
Hit http://ppa.launchpad.net precise Release.gpg
Hit http://ppa.launchpad.net precise Release.gpg
Hit http://archive.canonical.com precise Release.gpg
Hit http://security.ubuntu.com precise-security/multiverse i386 Packages
Hit http://us.archive.ubuntu.com precise/universe i386 Packages
Hit http://us.archive.ubuntu.com precise/multiverse i386 Packages
Hit http://us.archive.ubuntu.com precise/main TranslationIndex
Hit http://us.archive.ubuntu.com precise/multiverse TranslationIndex
Hit http://us.archive.ubuntu.com precise/restricted TranslationIndex
Get:1 http://linux.dropbox.com precise Release.gpg [489 B]
Hit http://apt.duke4.net precise Release.gpg
Hit http://security.ubuntu.com precise-security/main TranslationIndex
Hit http://security.ubuntu.com precise-security/multiverse TranslationIndex
Hit http://security.ubuntu.com precise-security/restricted TranslationIndex
Hit http://security.ubuntu.com precise-security/universe TranslationIndex
Hit http://ftp.osuosl.org precise Release.gpg
Hit http://ftp.osuosl.org precise Release.gpg
Hit http://us.archive.ubuntu.com precise/universe TranslationIndex
Hit http://us.archive.ubuntu.com precise-updates/main Sources
Hit http://us.archive.ubuntu.com precise-updates/restricted Sources
Hit http://us.archive.ubuntu.com precise-updates/universe Sources
Hit http://us.archive.ubuntu.com precise-updates/multiverse Sources
Hit http://security.ubuntu.com precise-security/main Translation-en
Hit http://security.ubuntu.com precise-security/multiverse Translation-en
Hit http://security.ubuntu.com precise-security/restricted Translation-en
Hit http://us.archive.ubuntu.com precise-updates/main amd64 Packages
Hit http://us.archive.ubuntu.com precise-updates/restricted amd64 Packages
Hit http://security.ubuntu.com precise-security/universe Translation-en
Hit http://us.archive.ubuntu.com precise-updates/universe amd64 Packages
Hit http://us.archive.ubuntu.com precise-updates/multiverse amd64 Packages
Hit http://us.archive.ubuntu.com precise-updates/main i386 Packages
Hit http://extras.ubuntu.com precise Release
Hit http://ppa.launchpad.net precise Release.gpg
Hit http://ppa.launchpad.net precise Release.gpg
Hit http://ppa.launchpad.net precise Release.gpg
Hit http://ppa.launchpad.net precise Release
Hit http://ppa.launchpad.net precise Release
Hit http://archive.canonical.com precise Release
Hit http://us.archive.ubuntu.com precise-updates/restricted i386 Packages
Hit http://us.archive.ubuntu.com precise-updates/universe i386 Packages
Hit http://us.archive.ubuntu.com precise-updates/multiverse i386 Packages
Hit http://us.archive.ubuntu.com precise-updates/main TranslationIndex
Hit http://us.archive.ubuntu.com precise-updates/multiverse TranslationIndex
Get:2 http://linux.dropbox.com precise Release [2,603 B]
Hit http://apt.duke4.net precise Release
Hit http://us.archive.ubuntu.com precise-updates/restricted TranslationIndex
Hit http://us.archive.ubuntu.com precise-updates/universe TranslationIndex
Hit http://us.archive.ubuntu.com precise-backports/main Sources
Hit http://us.archive.ubuntu.com precise-backports/restricted Sources
Hit http://us.archive.ubuntu.com precise-backports/universe Sources
Hit http://ftp.osuosl.org precise Release
Hit http://us.archive.ubuntu.com precise-backports/multiverse Sources
Hit http://us.archive.ubuntu.com precise-backports/main amd64 Packages
Hit http://us.archive.ubuntu.com precise-backports/restricted amd64 Packages
Hit http://us.archive.ubuntu.com precise-backports/universe amd64 Packages
Hit http://us.archive.ubuntu.com precise-backports/multiverse amd64 Packages
Hit http://extras.ubuntu.com precise/main Sources
Hit http://ppa.launchpad.net precise Release
Hit http://ppa.launchpad.net precise Release
Hit http://ppa.launchpad.net precise Release
Hit http://archive.canonical.com precise/partner Sources
Hit http://us.archive.ubuntu.com precise-backports/main i386 Packages
Hit http://us.archive.ubuntu.com precise-backports/restricted i386 Packages
Hit http://us.archive.ubuntu.com precise-backports/universe i386 Packages
Hit http://us.archive.ubuntu.com precise-backports/multiverse i386 Packages
Hit http://us.archive.ubuntu.com precise-backports/main TranslationIndex
Hit http://us.archive.ubuntu.com precise-backports/multiverse TranslationIndex
Hit http://us.archive.ubuntu.com precise-backports/restricted TranslationIndex
Hit http://us.archive.ubuntu.com precise-backports/universe TranslationIndex
Hit http://us.archive.ubuntu.com precise/main Translation-en
Hit http://us.archive.ubuntu.com precise/multiverse Translation-en
Get:3 http://linux.dropbox.com precise/main amd64 Packages [1,148 B]
Hit http://apt.duke4.net precise/main Sources
Hit http://us.archive.ubuntu.com precise/restricted Translation-en
Hit http://us.archive.ubuntu.com precise/universe Translation-en
Hit http://us.archive.ubuntu.com precise-updates/main Translation-en
Hit http://us.archive.ubuntu.com precise-updates/multiverse Translation-en
Hit http://us.archive.ubuntu.com precise-updates/restricted Translation-en
Hit http://ftp.osuosl.org precise Release
Hit http://extras.ubuntu.com precise/main amd64 Packages
Hit http://extras.ubuntu.com precise/main i386 Packages
Hit http://ppa.launchpad.net precise Release
Hit http://ppa.launchpad.net precise/main Sources
Hit http://ppa.launchpad.net precise/main amd64 Packages
Hit http://ppa.launchpad.net precise/main i386 Packages
Ign http://ppa.launchpad.net precise/main TranslationIndex
Hit http://ppa.launchpad.net precise/main Sources
Hit http://us.archive.ubuntu.com precise-updates/universe Translation-en
Hit http://us.archive.ubuntu.com precise-backports/main Translation-en
Hit http://archive.canonical.com precise/partner amd64 Packages
Hit http://archive.canonical.com precise/partner i386 Packages
Ign http://archive.canonical.com precise/partner TranslationIndex
Hit http://us.archive.ubuntu.com precise-backports/multiverse Translation-en
Hit http://us.archive.ubuntu.com precise-backports/restricted Translation-en
Hit http://us.archive.ubuntu.com precise-backports/universe Translation-en
Get:4 http://linux.dropbox.com precise/main i386 Packages [1,148 B]
Ign http://linux.dropbox.com precise/main TranslationIndex
Ign http://extras.ubuntu.com precise/main TranslationIndex
Hit http://ppa.launchpad.net precise/main amd64 Packages
Hit http://ppa.launchpad.net precise/main i386 Packages
Hit http://apt.duke4.net precise/main amd64 Packages
Ign http://ppa.launchpad.net precise/main TranslationIndex
Hit http://apt.duke4.net precise/main i386 Packages
Ign http://apt.duke4.net precise/main TranslationIndex
Hit http://ppa.launchpad.net precise/main Sources
Hit http://ppa.launchpad.net precise/main amd64 Packages
Hit http://ppa.launchpad.net precise/main i386 Packages
Ign http://ppa.launchpad.net precise/main TranslationIndex
Hit http://ppa.launchpad.net precise/main Sources
Hit http://ftp.osuosl.org precise/main Sources
Hit http://ftp.osuosl.org precise/main amd64 Packages
Hit http://ftp.osuosl.org precise/main i386 Packages
Ign http://ftp.osuosl.org precise/main TranslationIndex
Hit http://ppa.launchpad.net precise/main amd64 Packages
Hit http://ppa.launchpad.net precise/main i386 Packages
Ign http://ppa.launchpad.net precise/main TranslationIndex
Hit http://ppa.launchpad.net precise/main Sources
Hit http://ppa.launchpad.net precise/main amd64 Packages
Hit http://ftp.osuosl.org precise/main Sources
Hit http://ftp.osuosl.org precise/main amd64 Packages
Hit http://ftp.osuosl.org precise/main i386 Packages
Ign http://ftp.osuosl.org precise/main TranslationIndex
Hit http://ppa.launchpad.net precise/main i386 Packages
Ign http://ppa.launchpad.net precise/main TranslationIndex
Hit http://ppa.launchpad.net precise/main Sources
Hit http://ppa.launchpad.net precise/main amd64 Packages
Hit http://ppa.launchpad.net precise/main i386 Packages
Ign http://ppa.launchpad.net precise/main TranslationIndex
Ign http://archive.canonical.com precise/partner Translation-en_US
Ign http://extras.ubuntu.com precise/main Translation-en_US
Ign http://archive.canonical.com precise/partner Translation-en
Ign http://extras.ubuntu.com precise/main Translation-en
Ign http://linux.dropbox.com precise/main Translation-en_US
Ign http://apt.duke4.net precise/main Translation-en_US
Ign http://linux.dropbox.com precise/main Translation-en
Ign http://apt.duke4.net precise/main Translation-en
Ign http://ppa.launchpad.net precise/main Translation-en_US
Ign http://ppa.launchpad.net precise/main Translation-en
Ign http://ppa.launchpad.net precise/main Translation-en_US
Ign http://ppa.launchpad.net precise/main Translation-en
Ign http://ppa.launchpad.net precise/main Translation-en_US
Ign http://ppa.launchpad.net precise/main Translation-en
Ign http://ppa.launchpad.net precise/main Translation-en_US
Ign http://ppa.launchpad.net precise/main Translation-en
Ign http://ppa.launchpad.net precise/main Translation-en_US
Ign http://ppa.launchpad.net precise/main Translation-en
Ign http://ppa.launchpad.net precise/main Translation-en_US
Ign http://ppa.launchpad.net precise/main Translation-en
Ign http://ftp.osuosl.org precise/main Translation-en_US
Ign http://ftp.osuosl.org precise/main Translation-en
Ign http://ftp.osuosl.org precise/main Translation-en_US
Ign http://ftp.osuosl.org precise/main Translation-en
Fetched 5,388 B in 2s (2,345 B/s)
Reading package lists...


```

```

user@Q:~$ sudo apt-get install libreoffice
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libcdr-0.0-0 libclucene-contribs1 libclucene-core1 libcmis-0.3-3
  libexttextcat-2.0-0 libexttextcat-data libhyphen0 liblangtag-common
  liblangtag1 libmspub-0.0-0 libneon27-gnutls libreoffice-base
  libreoffice-base-core libreoffice-calc libreoffice-common libreoffice-core
  libreoffice-draw libreoffice-gnome libreoffice-gtk libreoffice-impress
  libreoffice-java-common libreoffice-math libreoffice-pdfimport
  libreoffice-report-builder-bin libreoffice-style-galaxy
  libreoffice-style-human libreoffice-writer libvisio-0.0-0 python-uno
  uno-libs3 ure xfonts-mathml
Suggested packages:
  hyphen-hyphenation-patterns libreoffice-grammarcheck libreoffice-help-4.1
  libreoffice-l10n-4.1 myspell-dictionary mythes-thesaurus
  openclipart-libreoffice pstoedit libreoffice-officebean libmyodbc
  odbc-postgresql libsqliteodbc tdsodbc mdbtools libmysql-java libpg-java
  libjtds-java libreoffice-gcj libreoffice-report-builder
  libreoffice-style-crystal libreoffice-style-hicontrast
  libreoffice-style-oxygen libreoffice-style-tango libreoffice-evolution
  crystalcursors kde-icons-crystal otf-stix
The following packages will be REMOVED:
  libreoffice-debian-menus
The following NEW packages will be installed:
  libcdr-0.0-0 libclucene-contribs1 libclucene-core1 libcmis-0.3-3
  libexttextcat-2.0-0 libexttextcat-data libhyphen0 liblangtag-common
  liblangtag1 libmspub-0.0-0 libneon27-gnutls libreoffice libreoffice-base
  libreoffice-base-core libreoffice-calc libreoffice-common libreoffice-core
  libreoffice-draw libreoffice-gnome libreoffice-gtk libreoffice-impress
  libreoffice-java-common libreoffice-math libreoffice-pdfimport
  libreoffice-report-builder-bin libreoffice-style-galaxy
  libreoffice-style-human libreoffice-writer libvisio-0.0-0 python-uno
  uno-libs3 ure xfonts-mathml
0 upgraded, 33 newly installed, 1 to remove and 3 not upgraded.
Need to get 87.5 MB/92.1 MB of archives.
After this operation, 292 MB of additional disk space will be used.

```

Any thoughts?  

Thanks,

AlphaA

**UPDATE**

So, I went in and changed the view in LibreOffice's menu, and it is now fixed.  I don't know how it got that way in the first place, because I never touched it.  Even in the previous install.

---

