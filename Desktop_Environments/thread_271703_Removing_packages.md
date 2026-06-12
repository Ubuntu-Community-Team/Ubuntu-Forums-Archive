---
title: "Removing packages"
date: 2006-10-05
forum: Desktop Environments
---

### Post by kampsuniahv on 2006-10-05
When i trie to remove packages that causing some troubles I end up with this.
```
kasutaja@Arvut:~$ sudo apt-get remove libgl1-mesa-dev libgl1-mesa-dri libwxgtk2.4-dev libwxgtk2.6-0 libxine-main1 ubuntu-desktop amule libglu1-mesa-dev libxine-extracodecs python-wxgtk2.6 x-window-system-core xine-ui libsdl1.2-dev libsdl-net1.2-dev
Reading package lists... Done
Building dependency tree... Done
The following packages will be REMOVED
  amule libgl1-mesa-dev libgl1-mesa-dri libglu1-mesa-dev libsdl-net1.2-dev
  libsdl1.2-dev libwxgtk2.4-dev libwxgtk2.6-0 libxine-extracodecs
  libxine-main1 python-wxgtk2.6 ubuntu-desktop x-window-system-core xine-ui
0 upgraded, 0 newly installed, 14 to remove and 0 not upgraded.
8 not fully installed or removed.
Need to get 0B of archives.
After unpacking 67,2MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... dpkg: error processing libsdl-net1.2-dev (--remove):
 files list file for package `libxp6' is missing final newline
Errors were encountered while processing:
 libsdl-net1.2-dev
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by mixmaster on 2006-10-05
Sounds as though you have a corrupt package there.  I would try reinstalling it.

I think the syntax is 

sudo apt-get install --reinstall <package-name>

Hopefully this will overwrite the corrupt file and allow you to uninstall (if you still want to).

---

### Post by kampsuniahv on 2006-10-05
didnt help
```
kasutaja@Arvut:~$ sudo apt-get install --reinstall libsdl-net1.2-dev
Reading package lists... Done
Building dependency tree... Done
You might want to run &#8216;apt-get -f install&#8217; to correct these:
The following packages have unmet dependencies.
  libgl1-mesa-dev: Depends: libgl1-mesa-glx (= 6.5.1~20060817-0ubuntu2) but it is not installable
  libgl1-mesa-dri: Depends: libgl1-mesa-glx (= 6.5.1~20060817-0ubuntu2) but it is not installable
  libwxgtk2.4-dev: Depends: wx2.4-headers (= 2.4.5.1ubuntu1) but 2.4.4.1.1ubuntu2 is to be installed
  libwxgtk2.6-0: Depends: libwxbase2.6-0 (>= 2.6.3.2.1.5) but it is not installable
  libxine-main1: Depends: libxine1 but it is not installable
  ubuntu-desktop: Depends: apport-gtk but it is not installable
                  Depends: f-spot but it is not going to be installed
                  Depends: gnome-keyring-manager but it is not going to be installed
                  Depends: gtk2-engines but it is not installable
                  Depends: hwdb-client-gnome but it is not installable
                  Depends: tomboy but it is not installable
                  Depends: totem-mozilla but it is not installable
                  Depends: usplash-theme-ubuntu but it is not installable
                  Depends: xorg but it is not installable
  x-window-system-core: Depends: xorg but it is not installable
E: Unmet dependencies. Try &#8216;apt-get -f install&#8217; with no packages (or specify a solution).

```

---

