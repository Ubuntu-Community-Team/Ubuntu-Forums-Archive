---
title: "New to linux, need help with rpm."
date: 2006-05-17
forum: Desktop Environments
---

### Post by caybo on 2006-05-17
well im new to linux.  I need help using rpm.  I installed xp, and ubuntu  and the boot choose menu works fine. Im trying to install a program(avast antivirus for linux) and i got it in an rpm format.  I type rpm -ivh ("programs name".rpm).I get this error. 

bash: rpm: command not found. 

Did I forget a step?  What should I do?  I typed locate rpm and I got this->

/var/cache/apt/archives/librpm4_4.0.4-31ubuntu1_i386.deb
/var/cache/apt/archives/rpm_4.0.4-31ubuntu1_i386.deb
/usr/share/doc/python-htmlgen/image/rpm1.jpg
/usr/share/doc/python-htmlgen/image/rpm2.jpg
/usr/share/mime/application/x-rpm.xml
/usr/share/icons/gnome/16x16/mimetypes/gnome-mime-application-x-rpm.png
/usr/share/icons/gnome/48x48/mimetypes/gnome-mime-application-x-rpm.png
/usr/lib/python2.4/distutils/command/bdist_rpm.py
/usr/lib/python2.4/distutils/command/bdist_rpm.pyc
/usr/lib/python2.4/distutils/command/bdist_rpm.pyo

Somewhere on the internet it said type
locate -u
locate rpm | grep bin
I did that and with the -u it responded with 
"fatal error: locate: You are not authorized to create a default slocate database!"

the rpm | grep bin responded with nothing, at all.  So I would greatly appreciate it if someone would help me, a newbie to linux, an expert at windows. :KS

---

### Post by Ramses de Norre on 2006-05-17
Install alien```
sudo aptitude install alien
``` Use alien to convert the .rpm to a .deb ```
sudo alien /path/to/file.rpm newfile.deb
``` 
Try to use .deb's if possible, but alien helps when you can't find a .deb.

---

### Post by glotz on 2006-05-17
And finally, to install the .deb package ```
sudo dpkg -i newfile.deb
```
(you'll still have to satisfy possible dependencies)

When did you get help like this the last time at a MS help desk? ;)

---

### Post by Ramses de Norre on 2006-05-17
Oh of course, forgot that :D

---

### Post by caybo on 2006-05-17
ok, did that, got this info

```

caybo@Cayboticus:/tmp$ sudo dpkg -i avast4workstation_1.0.5-2_i386.deb (Reading database ... 64053 files and directories currently installed.)
Preparing to replace avast4workstation 1.0.5-2 (using avast4workstation_1.0.5-2_i386.deb) ...
Unpacking replacement avast4workstation ...
Setting up avast4workstation (1.0.5-2) ...

caybo@Cayboticus:/tmp$

```

Am i done? how do i run the program? Thanks for the really quick reply.  Whats sudo?

---

### Post by glotz on 2006-05-17
Yes you've now installed it. Probably runs with ```
avast4workstation
```

See [https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

---

