---
title: "problem with reinstalling vmware server"
date: 2006-05-30
forum: Desktop Environments
---

### Post by djsamsel on 2006-05-30
i uninstalled vmware, because i thought it was creating a problem with my internet connection. turns out it was a problem with bittorrent. so i'd like to reinstall vmware but get the following error message when i try to. any help will be greatly appreciated.




A previous installation of VMware software has been detected.

The previous installation was made by the tar installer (version 3).

Keeping the tar3 installer database format.

Error: Unable to execute "/usr/bin/vmware-uninstall.pl.

Failure

Execution aborted.

---

### Post by garretwp on 2006-05-30
How did you install it in the first place? Did you use the tar method or did you use there install script? Can you manually remove the files from the system and then try and reinstall from there?

Garrett

---

### Post by slavik on 2006-05-30
make sure that the script is executable (chmod +x /usr/bin/vmware-uninstall.pl)

---

### Post by djsamsel on 2006-05-31
i used their script. how do i manually uninstall? i've only use ubuntu for a few weeks and it's my first linux distro, so i guess i'm still learning the basics. thanks, doug

---

### Post by garretwp on 2006-05-31
I believe all of vmware is located in these locations:

/etc/init.d/vmware
/etc/vmware
/var/lock/subsys/vmware
/usr/share/doc/vmware
/usr/bin/vmware
/usr/lib/vmware
/usr/lib/vmware/bin/vmware


try to remove these directories and try the install script to install again. You must sudo in order to remove these directories. For saftey, yuo can try and do a mv into your trash just in case this does not work. Do sudo mv directory ~/.Trash. Or if you want to completely remove it all, do a sudo rm -rf directory name. Be very very careful when you do this command can destroy your other files if done wrong.

i.e. sudo rm -rf /etc/init.d/vmware

Garrett

---

### Post by djsamsel on 2006-06-01
[QUOTE=garretwp]I believe all of vmware is located in these locations:

/etc/init.d/vmware
/etc/vmware
/var/lock/subsys/vmware
/usr/share/doc/vmware
/usr/bin/vmware
/usr/lib/vmware
/usr/lib/vmware/bin/vmware


try to remove these directories and try the install script to install again. You must sudo in order to remove these directories. For saftey, yuo can try and do a mv into your trash just in case this does not work. Do sudo mv directory ~/.Trash. Or if you want to completely remove it all, do a sudo rm -rf directory name. Be very very careful when you do this command can destroy your other files if done wrong.

i.e. sudo rm -rf /etc/init.d/vmware

Garrett[/QUOTE]

thanks a ton, that did it!

---

### Post by tc7 on 2006-07-01
thanks - that helped me too!

---

### Post by nuclearj on 2006-11-16
Muchas Gracias Tambien!

---

### Post by stevh0 on 2008-06-22
thanx guys, saved me alot of trouble ..

appreciate it :)

---

