---
title: "I received some updates today and..."
date: 2009-05-05
forum: General Help
---

### Post by kpkeerthi on 2009-05-05
...is there a changelog or something that would tell me what issues and bugs were addressed with the updates? Thanks.

---

### Post by GrouchoMarx on 2009-05-05
From the Debian [APT HOWTO]("http://www.debian.org/doc/manuals/apt-howto/ch-search.en.html#s-apt-listchanges"):

> 5.5 How to keep informed about the changes in the packages.

Every package installs in its documentation directory (/usr/share/doc/packagename) a file called changelog.Debian.gz which contains the list of changes made to the package since the last version. You can read these files with zless' help, for example, but it is something not so easy, after an complete system upgrade, to start searching changelogs for every upgraded package.

There's a way to automatize this task by means of a tool called apt-listchanges. To begin with one needs to install the apt-listchanges package. During the package installation, Debconf will configure it. Some questions may not be shown to you depending on the priority you set up Debconf to use. Answer to the questions as you want.

The first question asks how you want the changes to be showed by apt-listchanges. You can have them mailed to you, which is good for automatic upgrades, or you can ask them in a pager like less, so you can inspect the changes before leting the upgrade continue. If you don't want apt-listchanges running automaticaly during upgrades you can answer none.

After apt-listchanges is installed, as soon as packages are downloaded (or gotten from a CD or mounted disk) by apt it will show the lists of changes made to those packages before installing them. 

---

### Post by kpkeerthi on 2009-05-07
Its actually very simple. If you receive an update to **packageX** after doing **sudo aptitude update && sudo aptitude dist-upgrade**, just do **aptitude changelog packageX**.

Here is a sample output for brasero:
```

$ aptitude changelog brasero

brasero (2.26.1-0ubuntu1) jaunty-proposed; urgency=low

  * New upstream release (LP: #361224)
    - Fix bgo #576439 &#8211; nautilus crash because of probable double g_free in
      brasero_medium_get_css_feature (Philippe Rouquier) 
    - Fix bgo #575904 - Remove unneeded signal connection and rename callback.
      Fixes crash on Rhythmbox playlist import. (Luis Medinas) (LP: #288392)
    - Fix bgo #576564 &#8211; brasero crashed with SIGSEGV in brasero_image_format_get_cdrdao_size()
      (LP: #346784)
    - Fix bgo #576928 &#8211; Brasero crashes when pasting empty clipboard. (LP: #345177)
    - Fix bgo #573929 &#8211; nautilus crashed with SIGSEGV in start_thread() (Philippe
      Rouquier) (LP: #335942)
    - Fix bgo 573859 &#8211; Several 'Make Cover' buttons in Disc Copy dialog (LP: #347637)
    - Fix bgo #578677 - Registered property name in BraseroDriveSelectionClass is
      translated on runtime. (Luis Medinas) (LP: #578677) (LP: #360884)
  * debian/patches/02_css_double_free.patch:
    - Removed, the change is in the tarball

 -- Pedro Fragoso <ember@ubuntu.com>  Tue, 14 Apr 2009 17:59:04 +0100

```

---

