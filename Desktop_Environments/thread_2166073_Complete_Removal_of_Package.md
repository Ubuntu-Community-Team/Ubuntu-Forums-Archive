---
title: "Complete Removal of Package"
date: 2013-08-07
forum: Desktop Environments
---

### Post by Geoff_Lane on 2013-08-07
Guys,

I run Ubuntu 12.04 LTS on my laptop but would like some advice on a problem with my Raspberry Pi running Debian so am sure I'll get some suggestions.


I have a problem with apache web server and want to remove and start again.

I have tried sudo apt-get --purge remove apache2

Found some files still there so did sudo dpkg --purge apache2

Still found files in /etc/apache2

As some of it works and some doesn't I am going round in circles trying to solve so think it is quicker to start again but cannot completely remove ALL files.

Any suggestions greatly appreciated.

Geffers

---

### Post by bapoumba on 2013-08-07
Did you try sudo apt-get autoremove and then, sudo apt-get clean ?
```
autoremove
           autoremove is used to remove packages that were automatically installed to
           satisfy dependencies for other packages and are now no longer needed.
```

---

### Post by ian-weisser on 2013-08-07
Use dpkg's -L and -S flags to ensure that the files you discover are  really created by Apache instead of some other package. For example,  some of the files may be installed by the apache2.2-common package, or other dependencies.

One appropriate way to uninstall most packages is "sudo apt get autoremove apache2". This will remove apache2 and all it's dependencies (like apache2.2-common).

apt-get's 'purge' flag does not remove files in /home. That's deliberate. Your data in /home is considered yours, not the application's. Package uninstall scripts should not remove your data. For example, you usually don't want your e-mail archive deleted when you when you change mail clients. There is no "autopurge" flag equivalent to "autoremove".

apt-get's 'remove' flag does not remove files in /etc (settings) nor /home. That's deliberate. If you reinstall, your old settings are preserved. This is left over from the bad old days when it took a lot of work and experimentation to find just the right settings, and keeping them was important. Custom settings still occur, and this flag is not obsolete.

Does any flag remove /home files? No.

---

