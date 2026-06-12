---
title: "Have no locales"
date: 2005-10-06
forum: Desktop Environments
---

### Post by burk on 2005-10-06
Hello

I have been installing som packages and programs lately. When i booted into ubuntu today i got the message "cannot find language no_NO.UTF-8 will use System Default instead" (something like that). And the calendar in the upper right corner displays Thu Oct instead of ons okt (norwegian). I tried typing locale -a in console (should list all the languages) but i only get this: ```
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_COLLATE to default locale: No such file or directory
C
POSIX
```
I tried apt-get install locales but then i get this error message:
```
root@BJORN:/home/burk # apt-get install locales
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
  locales: Depends: glibc-2.3.2.ds1-20ubuntu14
E: Broken packages
```
What should i do to get the languagepacks back??

---

### Post by Ampersand on 2005-10-06
glibc should be in the repositories. Have you tried running 'sudo apt-get update' before trying to get locales? Try getting the 'libc6' package (this will provide the necessary version of glibc).

---

### Post by burk on 2005-10-06
Hmm... I tried running apt-get update but lately it has began to fail getting packages from [http://ubuntu-backports.mirrormax.net/dists/hoary-backports](http://ubuntu-backports.mirrormax.net/dists/hoary-backports), and although some files are updated i always get this error```
 E: Some index files failed to download, they have been ignored, or old ones used instead.

```

---

### Post by Ampersand on 2005-10-06
The mirrormax repositories are no longer being used, the sources.list line for the backports is now:

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary-backports main universe multiverse restricted

---

### Post by burk on 2005-10-06
Thanks for that.. I still get the same error when trying to install locales though. Seems like libc6 is broken or something
```
locales: Depends: glibc-2.3.2.ds1-20ubuntu14
E: Broken packages
```
Synaptic shows that i already have libc6 and that there is none broken packages :s

---

### Post by burk on 2005-10-07
Anyone?

---

### Post by snowjunkie on 2005-10-07
I got similar errors when dist-upgrading to breezy... does anyone know how to fix it?  It hasn't really affected me as yet though...

---

### Post by burk on 2005-10-08
I think i have found where the problem is. The locale-package asks for glibc-2.3.2dsl1-20..... but i have glibc-2.3.2dsl1-24. A newer version. Is there a place where i can download the locale folder and extract it to my usr/lib??

---

### Post by Envel on 2005-10-08
[QUOTE=burk]I think i have found where the problem is. The locale-package asks for glibc-2.3.2dsl1-20..... but i have glibc-2.3.2dsl1-24. A newer version. Is there a place where i can download the locale folder and extract it to my usr/lib??[/QUOTE]
Type in terminal:
sudo apt-get update
sudo apt-get upgrade locales

or:
sudo apt-get -f install - if represented above doesn't help.

---

