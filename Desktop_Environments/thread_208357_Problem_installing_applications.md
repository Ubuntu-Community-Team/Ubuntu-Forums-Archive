---
title: "Problem installing applications"
date: 2006-07-03
forum: Desktop Environments
---

### Post by wey97 on 2006-07-03
I have installed Ubuntu and I'm trying to install applications through Add/Remove.  If I try to check an app for installation, I get the message "'app name' is not available in any software channel...The application might not support your system architecture."

This happens on every app listed in Add/Remove not installed by default.  Why am I getting this message?

Thanks

---

### Post by aysiu on 2006-07-03
What's your architecture? AMD64? PowerPC?

---

### Post by wey97 on 2006-07-03
[QUOTE=aysiu]What's your architecture? AMD64? PowerPC?[/QUOTE]
Sorry I am on an Intel x86 PC.

---

### Post by aysiu on 2006-07-03
That's weird then. Can you post the output of this command? ```
cat /etc/apt/sources.list
```

---

### Post by wey97 on 2006-07-03
[QUOTE=aysiu]That's weird then. Can you post the output of this command? ```
cat /etc/apt/sources.list
```[/QUOTE]

It may be helpful to know that I cannot connect to the internet through Add/Remove or Synaptic Package Manager even after I enter proxy authentication information.  I can't pass through my ISA server for some reason.

I can connect to the internet through Firefox.

I thought the additional applications were available from the CD but I may be wrong.

Anyway, here is the command output:
```

deb cdrom:[Ubuntu 6.06 _Dapper Drake_ - Release i386 (20060531)]/ dapper main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ dapper-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu/ dapper universe main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted
deb http://security.ubuntu.com/ubuntu dapper-security universe
deb-src http://security.ubuntu.com/ubuntu dapper-security universe

```

---

### Post by aysiu on 2006-07-03
[QUOTE=wey97]It may be helpful to know that I cannot connect to the internet through Add/Remove or Synaptic Package Manager even after I enter proxy authentication information.  I can't pass through my ISA server for some reason.[/quote] Hm. That would be the problem, then. Very few additional packages are available through the CD. Most you get online in Ubuntu.

Can you post the output of this command, then? ```
sudo aptitude update
``` We'll see then if you're getting timed out, 403 forbidden, or 404 not found errors.

---

### Post by wey97 on 2006-07-03
[QUOTE=aysiu]Hm. That would be the problem, then. Very few additional packages are available through the CD. Most you get online in Ubuntu.

Can you post the output of this command, then? ```
sudo aptitude update
``` We'll see then if you're getting timed out, 403 forbidden, or 404 not found errors.[/QUOTE]
```

Password:
Reading package lists... Done
Building dependency tree... Done
Initializing package states... Done
Building tag database... Done
Ign http://us.archive.ubuntu.com dapper Release.gpg
Ign http://us.archive.ubuntu.com dapper-updates Release.gpg
Ign http://us.archive.ubuntu.com dapper-backports Release.gpg
Ign http://security.ubuntu.com dapper-security Release.gpg
Ign http://us.archive.ubuntu.com dapper Release
Ign http://us.archive.ubuntu.com dapper-updates Release
Ign http://security.ubuntu.com dapper-security Release
Ign http://us.archive.ubuntu.com dapper-backports Release
Ign http://us.archive.ubuntu.com dapper/main Sources
Ign http://us.archive.ubuntu.com dapper/restricted Sources
Ign http://us.archive.ubuntu.com dapper/universe Sources
Ign http://security.ubuntu.com dapper-security/main Packages
Ign http://us.archive.ubuntu.com dapper-updates/main Packages
Ign http://us.archive.ubuntu.com dapper-updates/restricted Packages
Ign http://security.ubuntu.com dapper-security/restricted Packages
Ign http://security.ubuntu.com dapper-security/main Sources
Ign http://security.ubuntu.com dapper-security/restricted Sources
Ign http://security.ubuntu.com dapper-security/universe Packages
Ign http://security.ubuntu.com dapper-security/universe Sources
Ign http://us.archive.ubuntu.com dapper-updates/main Sources
Ign http://us.archive.ubuntu.com dapper-updates/restricted Sources
Ign http://us.archive.ubuntu.com dapper-backports/main Packages
Ign http://us.archive.ubuntu.com dapper-backports/restricted Packages
Ign http://us.archive.ubuntu.com dapper-backports/universe Packages
Ign http://us.archive.ubuntu.com dapper-backports/multiverse Packages
Ign http://us.archive.ubuntu.com dapper-backports/main Sources
Ign http://us.archive.ubuntu.com dapper-backports/restricted Sources
Ign http://us.archive.ubuntu.com dapper-backports/universe Sources
Ign http://us.archive.ubuntu.com dapper-backports/multiverse Sources
Err http://security.ubuntu.com dapper-security/main Packages
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Err http://security.ubuntu.com dapper-security/restricted Packages
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Err http://security.ubuntu.com dapper-security/main Sources
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Err http://security.ubuntu.com dapper-security/restricted Sources
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Err http://security.ubuntu.com dapper-security/universe Packages
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Err http://us.archive.ubuntu.com dapper/main Sources
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Err http://us.archive.ubuntu.com dapper/restricted Sources
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Err http://us.archive.ubuntu.com dapper/universe Sources
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Err http://us.archive.ubuntu.com dapper-updates/main Packages
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Err http://us.archive.ubuntu.com dapper-updates/restricted Packages
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Err http://us.archive.ubuntu.com dapper-updates/main Sources
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Err http://us.archive.ubuntu.com dapper-updates/restricted Sources
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Err http://us.archive.ubuntu.com dapper-backports/main Packages
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Err http://us.archive.ubuntu.com dapper-backports/restricted Packages
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Err http://us.archive.ubuntu.com dapper-backports/universe Packages
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Err http://us.archive.ubuntu.com dapper-backports/multiverse Packages
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Err http://us.archive.ubuntu.com dapper-backports/main Sources
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Err http://us.archive.ubuntu.com dapper-backports/restricted Sources
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Err http://us.archive.ubuntu.com dapper-backports/universe Sources
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Err http://us.archive.ubuntu.com dapper-backports/multiverse Sources
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Ign http://archive.ubuntu.com dapper Release.gpg
Err http://security.ubuntu.com dapper-security/universe Sources
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Ign http://archive.ubuntu.com dapper Release
Ign http://archive.ubuntu.com dapper/universe Packages
Ign http://archive.ubuntu.com dapper/main Packages
Ign http://archive.ubuntu.com dapper/restricted Packages
Err http://archive.ubuntu.com dapper/universe Packages
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Err http://archive.ubuntu.com dapper/main Packages
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Err http://archive.ubuntu.com dapper/restricted Packages
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Reading package lists... Done

```

---

### Post by aysiu on 2006-07-03
That error doesn't seem to be too common, but maybe [this thread](http://www.ubuntuforums.org/showthread.php?t=96802) might help.

---

### Post by wey97 on 2006-07-03
[QUOTE=aysiu]That error doesn't seem to be too common, but maybe [this thread](http://www.ubuntuforums.org/showthread.php?t=96802) might help.[/QUOTE]
Thanks for the info.

I tried to edit /etc/apt/apt.conf to add 
Acquire::http::Proxy "http://MYDOMAIN\MYNAME:MYPASS@MY.PROXY.COM:MYPORT";

but the file opens as read-only.  I know I have admin privileges because I'm occasionally prompted for the password.

---

### Post by aysiu on 2006-07-03
Have you tried this? ```
sudo cp /etc/apt/apt.conf /etc/apt/apt.conf.backup
sudo nano /etc/apt/apt.conf
```

---

