---
title: "kmenuedit in lucid?"
date: 2010-06-08
forum: Desktop Environments
---

### Post by chitowner2 on 2010-06-08
Hi folks,

I am interested in a simple way to track and retain a list of installed applications from version to version. I know dpkg can give a list, but it will include every bootable app in the file system, several hundred of them, which makes it pretty useless for my purpose.

I have found that in karmic (pre-kde4) there is a file at /.config/menus/applications-kmenuedit.menu that is a reasonably nice list of installed apps. There does not seem to be a similar file in lucid with kde4.

Does anyone know how to generate such a file?

Thanks,
CT

---

### Post by ankspo71 on 2010-06-09
Hi,
Run this command to generate a simple list of installed applications.
```
ls -R /usr/share/applications > installed-applications.txt
```
All the command does is lists the contents of the given folder recursively, then copies the results to a text file. The results will be in your home folder in a file called "installed-applications.txt" 

You might have a few more application shortcuts in /home/<user>/.local/share/applications. Those would usually be the custom shortcuts or the shortcuts from applications installed from outside sources.
Hope that helps.

---

