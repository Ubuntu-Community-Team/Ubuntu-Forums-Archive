---
title: "Help needed"
date: 2009-05-12
forum: General Help
---

### Post by thegrimr3mind on 2009-05-12
i need some help i cant make sense of terminal and my computer says there is an error and to run apt-get i did and got this can someone help me

will@will-desktop:~$ apt-get
apt 0.7.20.2ubuntu6 for i386 compiled on Apr 17 2009 04:25:29
Usage: apt-get [options] command
       apt-get [options] install|remove pkg1 [pkg2 ...]
       apt-get [options] source pkg1 [pkg2 ...]

apt-get is a simple command line interface for downloading and
installing packages. The most frequently used commands are update
and install.

Commands:
   update - Retrieve new lists of packages
   upgrade - Perform an upgrade
   install - Install new packages (pkg is libc6 not libc6.deb)
   remove - Remove packages
   autoremove - Remove automatically all unused packages
   purge - Remove packages and config files
   source - Download source archives
   build-dep - Configure build-dependencies for source packages
   dist-upgrade - Distribution upgrade, see apt-get(8)
   dselect-upgrade - Follow dselect selections
   clean - Erase downloaded archive files
   autoclean - Erase old downloaded archive files
   check - Verify that there are no broken dependencies

Options:
  -h  This help text.
  -q  Loggable output - no progress indicator
  -qq No output except for errors
  -d  Download only - do NOT install or unpack archives
  -s  No-act. Perform ordering simulation
  -y  Assume Yes to all queries and do not prompt
  -f  Attempt to correct a system with broken dependencies in place
  -m  Attempt to continue if archives are unlocatable
  -u  Show a list of upgraded packages as well
  -b  Build the source package after fetching it
  -V  Show verbose version numbers
  -c=? Read this configuration file
  -o=? Set an arbitrary configuration option, eg -o dir::cache=/tmp
See the apt-get(8), sources.list(5) and apt.conf(5) manual
pages for more information and options.
                       This APT has Super Cow Powers.
will@will-desktop:~$

---

### Post by adult swim on 2009-05-12
apt-get is a program and you have to give it commands to run.  you need to be root to run it also so you will need to use sudo.  to update you can run ```
sudo apt-get update
``` once it searches for updates you can install them by running ```
sudo apt-get upgrade
```

---

### Post by thegrimr3mind on 2009-05-12
ill try it thanks

---

### Post by thegrimr3mind on 2009-05-12
do i need to restart my computer after

---

### Post by whoop on 2009-05-12
> **thegrimr3mind said:**
> do i need to restart my computer after
Your computer will inform you if it needs restarting...

---

### Post by adult swim on 2009-05-12
if you are still getting an error post what the error message says.

---

