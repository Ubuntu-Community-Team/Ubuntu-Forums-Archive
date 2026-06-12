---
title: "php5.3.0.0.dotdeb"
date: 2009-04-08
forum: General Help
---

### Post by quikone8 on 2009-04-08
I installed the package above and it is very buggy, I would like to remove it, but first I need to find it and then know how to remove it.  Does anyone have suggestions for this?  I would like to remove it from terminal.

---

### Post by kryptikos on 2009-04-08
Hi...need to know how you installed it? Did you install it from source? apt-get? the synaptic package manager? or dpkg?

---

### Post by quikone8 on 2009-04-08
I used apt-get install after putting putting deb [http://packages.dotdeb.org](http://packages.dotdeb.org) stable
deb-src [http://packages.dotdeb..org](http://packages.dotdeb..org) into the sources list

---

### Post by kryptikos on 2009-04-08
Since you used apt-get you can use modifiers to remove/purge the software. 

command structure is: **apt-get remove <name of package>**
**apt-get --purge remove <name of package>**
or **apt-get purge <name of package>**

The difference between remove and purge is -> remove will delete the software but leave configuration files. Purge will delete everything. 

Remember you can check your man pages as well. They are a wealth of information. Running **man apt-get** will show you:

> remove
           remove is identical to install except that packages are removed instead of installed. If a
           plus sign is appended to the package name (with no intervening space), the identified
           package will be installed instead of removed.

       purge
           purge is identical to remove except that packages are removed and purged.



Happy computing..... :)

---

### Post by quikone8 on 2009-04-08
When I try either remove or purge the system complains that the package is not installed.  How would I prove whether that is true or not?

---

### Post by kryptikos on 2009-04-08
what does **apt-cache show <name of software>** show?

---

### Post by quikone8 on 2009-04-08
> **kryptikos said:**
> what does **apt-cache show <name of software>** show?

Package: php5-gd
Status: deinstall ok config-files
Priority: optional
Section: web
Installed-Size: 380
Maintainer: Guillaume Plessis <gui@php.net>
Architecture: i386
Source: php5
Version: 5.3.0-0.dotdeb.1
Config-Version: 5.3.0-0.dotdeb.1
Depends: libc6 (>= 2.7-1), libfreetype6 (>= 2.3.5), libjpeg62, libpng12-0 (>= 1.2.13-4), libt1-5 (>= 5.1.0), libx11-6, libxpm4, zlib1g (>= 1:1.1.4), phpapi-20090115+lfs, php5-common (= 5.3.0-0.dotdeb.1)
Conffiles:
 /etc/php5/conf.d/gd.ini c2a6d431751cf7502aa7a1152bd4cf39
Description: GD module for php5
 This package provides a module for handling graphics directly from PHP
 scripts. It supports the PNG, JPEG, XPM formats as well as Freetype/ttf fonts.
 .
 PHP5 is an HTML-embedded scripting language. Much of its syntax is borrowed
 from C, Java and Perl with a couple of unique PHP-specific features thrown
 in. The goal of the language is to allow web developers to write dynamically
 generated pages quickly. This version of PHP5 was built with the Suhosin patch.
Homepage: [http://www.php.net/](http://www.php.net/)

Package: php5-gd
Priority: optional
Section: web
Installed-Size: 164
Maintainer: Ubuntu Core Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Debian PHP Maintainers <pkg-php-maint@lists.alioth.debian.org>
Architecture: i386
Source: php5
Version: 5.2.4-2ubuntu5.5
Depends: libc6 (>= 2.4), libfreetype6 (>= 2.3.5), libgd2-xpm (>= 2.0.35.dfsg), libjpeg62, libpng12-0 (>= 1.2.13-4), libt1-5, libx11-6, libxpm4, php5-common (= 5.2.4-2ubuntu5.5), phpapi-20060613+lfs, zlib1g (>= 1:1.2.3.3.dfsg-1)
Filename: pool/main/p/php5/php5-gd_5.2.4-2ubuntu5.5_i386.deb
Size: 32904
MD5sum: 1f804c22fc2cce43b227cb7e2cc6e041
SHA1: b8cdb970dedb4581141d4584426dcd025676ae65
SHA256: 14ee8e52899555be248c039ca063f1b7d2de687c73416fd9f11e895a617ac471
Description: GD module for php5
 This package provides a module for handling graphics directly from PHP
 scripts. It supports the PNG, JPEG, XPM formats as well as Freetype/ttf fonts.
 .
 PHP5 is an HTML-embedded scripting language. Much of its syntax is borrowed
 from C, Java and Perl with a couple of unique PHP-specific features thrown
 in. The goal of the language is to allow web developers to write
 dynamically generated pages quickly.
Bugs: [https://bugs.launchpad.net/ubuntu/+filebug](https://bugs.launchpad.net/ubuntu/+filebug)
Origin: Ubuntu
Task: edubuntu-server, edubuntu-ship-addon

Package: php5-gd
Priority: optional
Section: web
Installed-Size: 160
Maintainer: Ubuntu Core Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Debian PHP Maintainers <pkg-php-maint@lists.alioth.debian.org>
Architecture: i386
Source: php5
Version: 5.2.4-2ubuntu5
Depends: libc6 (>= 2.7-1), libfreetype6 (>= 2.3.5), libgd2-xpm (>= 2.0.35.dfsg), libjpeg62, libpng12-0 (>= 1.2.13-4), libt1-5, libx11-6, libxpm4, php5-common (= 5.2.4-2ubuntu5), phpapi-20060613+lfs, zlib1g (>= 1:1.2.3.3.dfsg-1)
Filename: pool/main/p/php5/php5-gd_5.2.4-2ubuntu5_i386.deb
Size: 32796
MD5sum: c8e92d5287a4f6c0655a6eb85775476b
SHA1: 6a9637a92b3ce990377e18e8927415aad33ec77a
SHA256: 3e7a0e8f022c8d2f519145d076b2a36c7707ce9f292cffe4b1b745a57c3f3aea
Description: GD module for php5
 This package provides a module for handling graphics directly from PHP
 scripts. It supports the PNG, JPEG, XPM formats as well as Freetype/ttf fonts.
 .
 PHP5 is an HTML-embedded scripting language. Much of its syntax is borrowed
 from C, Java and Perl with a couple of unique PHP-specific features thrown
 in. The goal of the language is to allow web developers to write
 dynamically generated pages quickly.
Bugs: mailto:ubuntu-users@lists.ubuntu.com
Origin: Ubuntu
Task: edubuntu-server, edubuntu-ship-addon

---

### Post by kryptikos on 2009-04-08
When you tell it to remove are you using "php5-gd" as the package name or "php5.3.0.0.dotdeb". If you are using php5.3.0.0 etc that is why it lists as uninstalled. You need to use "php5-gd". 

If that still fails you can also try: 

**dpkg -r <package name> ** or **dpkg --purge <package name>** (will require the sudo in front of that).

---

### Post by quikone8 on 2009-04-08
> **kryptikos said:**
> When you tell it to remove are you using "php5-gd" as the package name or "php5.3.0.0.dotdeb". If you are using php5.3.0.0 etc that is why it lists as uninstalled. You need to use "php5-gd". 

If that still fails you can also try: 

**dpkg -r <package name> ** or **dpkg --purge <package name>** (will require the sudo in front of that).


__purge seems like it worked, now I get the following when trying to re-install;

ron@tolmarket:~$ sudo apt-get install php5 php5-cli php5-common php5-curl php5-dev php5-gd php5-imap php5-ldap unzip
Reading package lists... Done
Building dependency tree       
Reading state information... Done
php5-cli is already the newest version.
php5-common is already the newest version.
php5-curl is already the newest version.
unzip is already the newest version.
unzip set to manually installed.
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  php5-gd: Depends: php5-common (= 5.2.4-2ubuntu5.5) but 5.3.0-0.dotdeb.1 is to be installed
           Depends: phpapi-20060613+lfs
  php5-imap: Depends: phpapi-20060613+lfs
  php5-ldap: Depends: php5-common (= 5.2.4-2ubuntu5.5) but 5.3.0-0.dotdeb.1 is to be installed
             Depends: phpapi-20060613+lfs
E: Broken packages

---

### Post by kryptikos on 2009-04-08
Why are you trying to reinstall the php5-gd when it was the cause of your initial problem and you complained that it was buggy and you no longer wanted it installed?

> ron@tolmarket:~$ sudo apt-get install php5 php5-cli php5-common php5-curl php5-dev **php5-gd** php5-imap php5-ldap unzip

---

### Post by quikone8 on 2009-04-08
Not the same version, this is from the ubuntu repos.

---

### Post by kryptikos on 2009-04-08
> Depends: phpapi-20060613+lfs

It's telling you what you need to install as a dependency. Running a quick aptitude serach and there is a package out there. 

>  aptitude search phpapi-20060613
v   phpapi-20060613+lfs 

---

### Post by quikone8 on 2009-04-08
Is there an effective way to uninstall, remove, purge this dotdeb file.  PHP worked okay before I tried it?

---

### Post by Dr. Pappa on 2011-09-09
Hi,

I seem to be having the same issue as quikone8 and I'm pretty stumped.

I'm trying to install the package php5-xsl in hardy, but I get this error:

> The following packages have unmet dependencies:
  php5-xsl: Depends: php5-common (= 5.2.4-2ubuntu5.17) but 5.2.8-0.dotdeb.1 is to be installed
E: Broken packagesUsing "apt-cache show php5-common" I can see that I have the 5.2.4-2ubuntu5.17 version of this package installed, but it seems php5-xsl is dependent on the 5.2.8-0.dotdeb.1 version of php5-common.

I'm not sure how to proceed from here.

---

