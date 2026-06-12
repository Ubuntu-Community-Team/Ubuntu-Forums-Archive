---
title: "Firefox and Thunderbird trashed"
date: 2005-01-29
forum: Desktop Environments
---

### Post by andbert on 2005-01-29
I did a apt-get update && upgrade, and after rebooting either ff or tb start...

i've tried running them as root as well but nothing happens.

when trying to run firefox from terminal the following output occurs:
```
andreas@ubuntu:~ $ firefox
*** loading the extensions datasource
*** ExtensionManager:_updateManifests: no access privileges to application directory, skipping.
*** loading the extensions datasource
*** ExtensionManager:_updateManifests: no access privileges to application directory, skipping.
Segmentation fault
```

Running firefox with 'sudo' command gives me:
```
andreas@ubuntu:~ $ sudo firefox
Password:
*** loading the extensions datasource
*** loading the extensions datasource
Segmentation fault
```


and when running thunderbird in terminal:
```
andreas@ubuntu:~ $ mozilla-thunderbird
selected locale: en-US
observe:
nothing here: null
observe called
FILE: [xpconnect wrapped nsIFile]DOUBLE-CLICK: 400 --> -1 THRESHOLD: 4 --> -1 /usr/lib/mozilla-thunderbird/run-mozilla.sh: line 159:  8752 Segmentation fault    "$prog" ${1+"$@"}
```

my epiphany browser works though....

any input?

---

### Post by johnwind on 2005-01-30
this is what i get instead, after i try to install java plugins..... :sad: 
reinstall, remove....everything seems to be getting worse...need help !!!

root@ubuntu:/usr/local # apt-get remove mozilla-firefox
Reading Package Lists... Done
Building Dependency Tree... Done
The following packages will be REMOVED:
  mozilla-firefox
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B of archives.
After unpacking 27.9MB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 74651 files and directories currently installed.)
Removing mozilla-firefox ...
root@ubuntu:/usr/local # apt-get install mozilla-firefox
Reading Package Lists... Done
Building Dependency Tree... Done
Suggested packages:
  latex-xft-fonts
The following NEW packages will be installed:
  mozilla-firefox
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/9568kB of archives.
After unpacking 27.9MB of additional disk space will be used.

Preconfiguring packages ...
Selecting previously deselected package mozilla-firefox.
(Reading database ... 74181 files and directories currently installed.)
Unpacking mozilla-firefox (from .../mozilla-firefox_0.99+1.0PR.1+revertedto0.9.3-0ubuntu3_i386.deb) ...
Setting up mozilla-firefox (0.99+1.0PR.1+revertedto0.9.3-0ubuntu3) ...
Updating mozilla-firefox chrome registry...done.

** (process:13286): CRITICAL **: file eggdesktopentries.c: line 2223 (egg_desktop_entries_add_group): assertion `egg_desktop_entries_lookup_group (entries, group_name) == NULL' failed

** (process:13286): CRITICAL **: file eggdesktopentries.c: line 2223 (egg_desktop_entries_add_group): assertion `egg_desktop_entries_lookup_group (entries, group_name) == NULL' failed

** (process:13286): CRITICAL **: file eggdesktopentries.c: line 2223 (egg_desktop_entries_add_group): assertion `egg_desktop_entries_lookup_group (entries, group_name) == NULL' failed

---

### Post by BigSmoke on 2005-02-02
You might want to try to move [FONT=Lucida Console]~/.mozilla[/FONT] to another (temporary) location to see if that helps. However, I suspect that your problem is caused by incorrect permissions in [FONT=Lucida Console]/usr/lib/mozilla-firefox[/FONT]. 

Hoping this wil help,

 - Rowan

---

### Post by andbert on 2005-02-03
I got the same error message no matter what....

---

