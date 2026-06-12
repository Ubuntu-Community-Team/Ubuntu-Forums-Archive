---
title: "Kiosk profiles based on groups"
date: 2012-09-24
forum: Desktop Environments
---

### Post by moosicmaan on 2012-09-24
Kubuntu 12.04
KDE 4.8.5
LTSP 64bit Server with 32bit fat and thin clients

I am relatively new to Linux, yet it is my duty to manage the computer labs at a school. I know this is probably Linux 101 stuff so I would be happy to be redirected, especially if this has already been addressed.

I need to lockdown user's desktop based on their primary group. (youngStudents, oldStudents, teachers, libraryKiosks, admins). Last year I successfully used Sabayon and Pessulus with gnome, but the tools don't seem to work because 12.04 is now using dconf. (right?) Besides, I want to use KDE.

I think I understand how to lock down a KDE desktop now, but I am confused on how to direct users of different groups to a different set of (copied from default) configuration files. How would one change $KDEDIRS and/or $KDEHOME to point to the different set of files, or is there an easier/better way to do this? 

I found this [thread]("http://www.linuxquestions.org/questions/linux-server-73/set-environment-variable-by-group-819292/") on setting environmental variables by group. Is it a good practice to alter /etc/profile, or is there a better way? Am I barking up the right tree?

Thanks,
Jason

---

