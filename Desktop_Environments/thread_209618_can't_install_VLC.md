---
title: "can't install VLC"
date: 2006-07-05
forum: Desktop Environments
---

### Post by neighborlee on 2006-07-05
hi,,

   I am unable to install VLC media player due to :

 sudo apt-get install vlc
Password:
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
  vlc: Depends: libdbus-1-1 (>= 0.36.2) but it is not going to be installed
E: Broken packages

any ideas ?? ;)

thx
nl

---

### Post by Ramses de Norre on 2006-07-05
Hmm are you sure you have all repos? The right version of libdbus should be in the main one..

---

### Post by neighborlee on 2006-07-05
[QUOTE=Ramses de Norre]Hmm are you sure you have all repos? The right version of libdbus should be in the main one..[/QUOTE]

I have main repo and the multi and universe as well

I think problem is because dbus is already installed and  conflicting with at libdbus being needed for VLC..??

thx ;)
nl

---

### Post by neighborlee on 2006-07-05
[QUOTE=neighborlee]I have main repo and the multi and universe as well

I think problem is because dbus is already installed and  conflicting with at libdbus being needed for VLC..??

thx ;)
nl[/QUOTE]

no idea...???? is everyone bonked out from 4th ?lol

cheers
nl

---

### Post by neighborlee on 2006-07-06
[QUOTE=neighborlee]no idea...???? is everyone bonked out from 4th ?lol

cheers
nl[/QUOTE]

bump..sorrry but vlc is a neat app to have...is this because I have enabled multiverse/universe or because im running 64 bit os ??

thx
nl

---

