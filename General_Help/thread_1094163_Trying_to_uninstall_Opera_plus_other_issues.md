---
title: "Trying to uninstall Opera plus other issues"
date: 2009-03-12
forum: General Help
---

### Post by sports fan Matt on 2009-03-12
When I try to uninstall opera and check for updates, I get the following message: debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing opera (--remove):
 subprocess post-removal script returned error exit status 1
Errors were encountered while processing:
 opera
E: Sub-process /usr/bin/dpkg returned an error code (1)

Also when I run update manager its checking for a partial upgrade to Jaunty I assume..How can I stop that message and run update manager as normal?

---

### Post by kryptikos on 2009-03-12
I'd use lsof to locate what process has that file open. You can use 'sudo lsof | grep config.dat' or other variations to see what's utilizing that file. Kill that process and recycle your update to test.

---

### Post by sports fan Matt on 2009-03-12
That returned this: lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/office/.gvfs
      Output information may be incomplete.
dpkg-prec 10589       root    4rW     REG        8,1    36753   26911175 /var/cache/debconf/config.dat

---

### Post by x C0MMAND0 x on 2009-03-12
```
sudo apt-get purge opera
```

That should remove it completely.  Do this immediately after logging on so that no other process should interfere.  Do Ctrl-Alt-Backspace if you are logged on to go back to the login menu and effectively kill all processes.

Let me know if that works for you.

---

### Post by kryptikos on 2009-03-12
Don't worry about the warning part. That is referencing something for the gnome virtual filesystem.

The other part shows that dpkg-preconfigure is holding that file. From appearances your aptitudate or apt-get session incurred an error and dpkg-prec has not let go of the db.  Follow xCOMMANDOx post and let us know what happens.

---

### Post by sports fan Matt on 2009-03-12
It was removed but this error as well: Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libbabl-0.0-0
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  opera
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 23.5MB disk space will be freed.
Do you want to continue [Y/n]? y
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
(Reading database ... 111801 files and directories currently installed.)
Removing opera ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing opera (--remove):
 subprocess post-removal script returned error exit status 1
Errors were encountered while processing:
 opera
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

