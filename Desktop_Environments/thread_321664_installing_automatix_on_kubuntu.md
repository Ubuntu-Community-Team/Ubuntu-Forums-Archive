---
title: "installing automatix on kubuntu"
date: 2006-12-19
forum: Desktop Environments
---

### Post by rkakkar on 2006-12-19
i get the following error:

```

$ sudo dpkg -i automatix2_1.1-2.3-6.10edgy_i386.deb
(Reading database ... 64112 files and directories currently installed.)
Preparing to replace automatix2 1.1-2.3-6.10edgy_i386 (using automatix2_1.1-2.3-6.10edgy_i386.deb) ...
Unpacking replacement automatix2 ...
dpkg: dependency problems prevent configuration of automatix2:
 automatix2 depends on tango-icon-theme-common; however:
  Package tango-icon-theme-common is not installed.
 automatix2 depends on tango-icon-theme; however:
  Package tango-icon-theme is not installed.
 automatix2 depends on python2.4-gtk2; however:
  Package python2.4-gtk2 is not installed.
 automatix2 depends on python2.4-glade2; however:
  Package python2.4-glade2 is not installed.
 automatix2 depends on python-vte; however:
  Package python-vte is not installed.
 automatix2 depends on gksu; however:
  Package gksu is not installed.
 automatix2 depends on libgnomeui-0; however:
  Package libgnomeui-0 is not installed.
 automatix2 depends on python-gnome2-extras; however:
  Package python-gnome2-extras is not installed.
dpkg: error processing automatix2 (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 automatix2


```

---

### Post by raul_ on 2006-12-19
You should install that using apt-get or aptitude. Installing the package won't handle dependencies

---

### Post by pebo on 2006-12-19
Have you checked out the[ getautomatix]("http://www.getautomatix.com/wiki/index.php?title=Installation") site? You can add the repository to your sources.list and install via apt / synaptic. Full instructions on the site.
hth

---

### Post by rkakkar on 2006-12-19
i did.. but when i did the last step.. i got the same error:

```

$ sudo apt-get install automatix2
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
  automatix2: Depends: tango-icon-theme-common but it is not installable
              Depends: tango-icon-theme but it is not installable
              Depends: python2.4-gtk2 but it is not installable
              Depends: python2.4-glade2 but it is not installable
              Depends: python-vte but it is not installable
              Depends: gksu but it is not installable
              Depends: libgnomeui-0 but it is not installable
              Depends: python-gnome2-extras but it is not installable
E: Broken packages


```

---

### Post by raul_ on 2006-12-19
I think your sources.list files could use a replacement

---

### Post by B_Stil on 2008-01-03
Were you connected to the internet when you installed Ubuntu?  I had the same problem until I looked at my sources.list file and saw that Ubuntu commented out all my sources when it installed because it couldn't connect to them.  Try that, otherwise google "sources.list" generator and the first link will take you to a site that generates a new file based on your choices.

---

### Post by PeterJS on 2008-01-03
What are you trying to install with automatix? Chances are it's in restricted extras or medibuntu, both of which aren't famous for breaking systems.

---

### Post by doogy2004 on 2008-01-03
> **rkakkar said:**
> i get the following error:

```

$ sudo dpkg -i automatix2_1.1-2.3-6.10edgy_i386.deb
(Reading database ... 64112 files and directories currently installed.)
Preparing to replace automatix2 1.1-2.3-6.10edgy_i386 (using automatix2_1.1-2.3-6.10edgy_i386.deb) ...
Unpacking replacement automatix2 ...
dpkg: dependency problems prevent configuration of automatix2:
 automatix2 depends on tango-icon-theme-common; however:
  Package tango-icon-theme-common is not installed.
 automatix2 depends on tango-icon-theme; however:
  Package tango-icon-theme is not installed.
 automatix2 depends on python2.4-gtk2; however:
  Package python2.4-gtk2 is not installed.
 automatix2 depends on python2.4-glade2; however:
  Package python2.4-glade2 is not installed.
 automatix2 depends on python-vte; however:
  Package python-vte is not installed.
 automatix2 depends on gksu; however:
  Package gksu is not installed.
 automatix2 depends on libgnomeui-0; however:
  Package libgnomeui-0 is not installed.
 automatix2 depends on python-gnome2-extras; however:
  Package python-gnome2-extras is not installed.
dpkg: error processing automatix2 (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 automatix2


```

my first question is why are you installing automatix deb from the command line?, you could just as easily double click on the deb file and the installer will fix the dependancies for you.  If you insist on using the terminal, run the following after attempting to install automatix with the deb.

```
sudo apt-get install -f
```

if you still have questions, here is a link to the installation instructions.  it tells you exactly how to install it once you have the deb downloaded. [http://www.getautomatix.com/wiki/index.php?title=Installation#Easy_Direct_Installation](http://www.getautomatix.com/wiki/index.php?title=Installation#Easy_Direct_Installation)

---

