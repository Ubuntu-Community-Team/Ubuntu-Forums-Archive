---
title: "how to make checkinstall only build the package without installing it?"
date: 2005-09-26
forum: Desktop Environments
---

### Post by foxy123 on 2005-09-26
I remember I could do it with RPMs in SuSE but with Ubuntu it automatically installs the package.

---

### Post by mlomker on 2005-09-26
**--install=no** doesn't work?  You can see the command-line switches with **checkinstall --help**.

---

### Post by foxy123 on 2005-09-26
[QUOTE=mlomker]**--install=no** doesn't work?  You can see the command-line switches with **checkinstall --help**.[/QUOTE]
```
$ checkinstall --help

checkinstall 1.5.3, Copyright 2001 Felipe Eduardo Sanchez Diaz Duran
           This software is released under the GNU GPL.


checkinstall 1.5.3, Copyright 2001 Felipe Eduardo Sanchez Diaz Duran
           This software is released under the GNU GPL.

Usage: checkinstall [options] [command [command arguments]]
Options:

*Package type selection*

-t,--type=<slackware|rpm|debian> Choose packaging system
-S                               Build a Slackware package
-R                               Build a RPM package
-D                               Build a Debian package

*Scripting options*

-y, --default                  Accept default answers to all questions
--pkgname=<name>               Set name
--pkgversion=<version>         Set version
-A, --arch, --pkgarch=<arch>   Set architecture
--pkgrelease=<release>         Set release
--pkglicense=<license>         Set license
--pkggroup=<group>             Set software group
--pkgsource=<source>           Set source location
--pkgaltsource=<altsource>     Set alternate source location
--pakdir=<directory>           The new package will be saved here
--maintainer=<email addr>      The package maintainer (.deb)
--provides=<list>              Features provided by this package (.rpm)
--rpmflags=<flags>             Pass this flags to the rpm installer
--dpkgflags=<flags>            Pass this flags to the dpkg installer
--spec=<path>                  .spec file location
--nodoc                        Do not include documentacion files

*Info display options*

-d<0|1|2>                      Set debug level
-si                            Run an interactive install command
--showinstall=<yes|no>         Toggle interactive install command
-ss                            Run an interactive Slackware installation script
--showslack=<yes|no>           Toggle interactive Slackware installation script
--exclude=<file|dir[,...]>     Exclude files/directtories from the package

*Package tuning options*

--autodoinst=<yes|no>          Toggle the creation of a doinst.sh script
--strip=<yes|no>               Strip any ELF binaries found inside the package
--stripso=<yes|no>             Strip any ELF binary libraries (.so files)
--gzman=<yes|no>               Compress any man pages found inside the package
--docdir=<path>                Where to put documentation files
--umask=<mask>                 Set the umask value
--newslack                     Use the new (8.1+) Slackware description format
                               ("--newslack" implies "-S")

*Cleanup options*

--deldoc=<yes|no>              Delete doc-pak upon termination
--deldesc=<yes|no>             Delete description-pak upon termination
--delspec=<yes|no>             Delete spec file upon termination
--bk                           Backup any overwritten files
--backup=<yes|no>              Toggle backup

*About CheckInstall*

--help, -h                     Show this message
--copyright                    Show Copyright information
--version                      Show version information

```

no such switch :(

---

### Post by foxy123 on 2005-09-26
I have installed the latest version 1.6.0.1 and it has that option.

---

### Post by mlomker on 2005-09-26
> no such switch :(

You should grab the [latest version]("http://asic-linux.com.mx/~izto/checkinstall/download.php").  It compiles easily and has more features.

---

