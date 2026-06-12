---
title: "preseed setting to use /cdrom as mirror in automated install"
date: 2019-05-30
forum: Debian
---

### Post by alpsoss on 2019-05-30
Hi,

I am working on a system where I want to install from /cdrom. The initial install cannot use network mirror for some reasons.

I need to have automated install and thus I am using preseed file.

What is the right preseed config for mirror to specify to use the /cdrom. 

Based on an old thread, I have tried: 

d-i mirror/protocol string file
d-i mirror/file/directory string /cdrom

But this does not work.

The main-menu log (screen 1) is:



!! ERROR: Bad archive mirror


An error has been detected while trying to use the specified Debian archive
mirror.


Possible reasons for the error are: incorrect mirror specified; mirror is not
available (possibly due to an unreliable network connection); mirror is broken
(for example because an invalid Release file was found); mirror does not
support the correct Debian version.


Additional details may be available in /var/log/syslog or on virtual console 4.


Please check the specified mirror or try a different one.
[Press enter to continue]



Here is the tail end of the installer debug capture:

May 30 20:46:55 debconf: <-- 0 ftp.us.debian.org
May 30 20:46:55 debconf: --> GET mirror/http/directory
May 30 20:46:55 debconf: <-- 0 /debian/
May 30 20:46:55 choose-mirror[30932]: DEBUG: command: wget --no-verbose [http://ftp.us.debian.org/debian/dists/stretch/Release](http://ftp.us.debian.org/debian/dists/stretch/Release) -O - | grep -E '^(Suite|Codename|Architectures):'
May 30 20:47:51 choose-mirror[30932]: WARNING **: mirror does not support the specified release (stretch)
May 30 20:47:51 debconf: --> FSET mirror/http/hostname seen false
May 30 20:47:51 debconf: <-- 0 false
May 30 20:47:51 debconf: --> FSET mirror/http/directory seen false
May 30 20:47:51 debconf: <-- 0 false
May 30 20:47:51 debconf: --> FSET mirror/country seen false
May 30 20:47:51 debconf: <-- 0 false
May 30 20:47:51 debconf: --> FSET mirror/suite seen false
May 30 20:47:51 debconf: <-- 0 false
May 30 20:47:51 debconf: --> INPUT critical mirror/bad
May 30 20:47:51 debconf: <-- 0 question will be asked
May 30 20:47:51 debconf: --> GO

Any pointers on how I can proceed?

thx
-a

---

### Post by Frogs Hair on 2019-05-30
Welcome !

Is this installation Debian ?

---

### Post by alpsoss on 2019-05-30
> **Frogs Hair said:**
> Welcome !

Is this installation Debian ?


Yes, this is debian

---

### Post by Frogs Hair on 2019-05-31
Moved to *Debian*.

---

