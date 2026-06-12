---
title: "OpenOffice 2.0 - Again"
date: 2005-10-27
forum: Desktop Environments
---

### Post by Mikulcak on 2005-10-27
Hi there,
I don't know, whether this subject is treated somewhere else here, I didn't find it.
I have problems installing OpenOffice 2. I downloaded the native rpm - packages and 'did' converted them to deb - packages with alien. After that, I did the same with the /desktop-integration/ - folder and installed the packages with dpkg -i; so far, so good. Now I installed the rest of the packages (the core, and so on) the same way. The installation itself works fine, but I just can't start it.
When I try to start it with the terminal (openoffice.org-2.0) it isn't found:

> /usr/bin/openoffice.org-2.0: line 2: /etc/openoffice.org-2.0/program/soffice: cannot execute: Datei oder Verzeichnis nicht gefunden

This is german for: I really can't find the damn file...

OK, the file really doesn't exist, but where is it? Where are all those executables I installed?

Questions, questions...

Thank you very much,
Mikulcak

---

### Post by abou on 2005-10-27
There is a desktop integration package for Debian that does not need to be converted in the zip file you downloaded.  You have essentially converted a package that is designed to only work on RPM distros.

Just move the desktop integration .deb to the same folder as all the other converted packages and install it with the rest.

---

