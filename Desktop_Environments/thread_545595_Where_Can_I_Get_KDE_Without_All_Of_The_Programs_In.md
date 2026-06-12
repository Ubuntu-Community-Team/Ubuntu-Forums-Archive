---
title: "Where Can I Get KDE Without All Of The Programs Included?"
date: 2007-09-07
forum: Desktop Environments
---

### Post by kh1116 on 2007-09-07
I already have GNOME, so I don't need all of the programs, I just want the desktop environment. Is there such a thing?

---

### Post by rfruth on 2007-09-07
not that I know of :(

---

### Post by vanden12 on 2007-09-07
I think Synaptic Package Manager just has plane old kde with no apps installed...

just search Kde...

---

### Post by yabbadabbadont on 2007-09-07
```
/home/daffy $ aptitude show kdebase
Package: kdebase
State: not installed
Version: 4:3.5.6-0ubuntu20.2
Priority: optional
Section: kde
Maintainer: Jonathan Riddell <jriddell@ubuntu.com>
Uncompressed Size: 98.3k
Depends: kappfinder (>= 4:3.5.6-0ubuntu20.2), kate (>= 4:3.5.6-0ubuntu20.2), kcontrol (>= 4:3.5.6-0ubuntu20.2), kdebase-bin (>=
         4:3.5.6-0ubuntu20.2), kdebase-data (>= 4:3.5.6-0ubuntu20.2), kdebase-kio-plugins (>= 4:3.5.6-0ubuntu20.2), kdepasswd
         (>= 4:3.5.6-0ubuntu20.2), kdeprint (>= 4:3.5.6-0ubuntu20.2), kdesktop (>= 4:3.5.6-0ubuntu20.2), kfind (>=
         4:3.5.6-0ubuntu20.2), khelpcenter (>= 4:3.5.6-0ubuntu20.2), kicker (>= 4:3.5.6-0ubuntu20.2), klipper (>=
         4:3.5.6-0ubuntu20.2), kmenuedit (>= 4:3.5.6-0ubuntu20.2), konqueror-nsplugins (>= 4:3.5.6-0ubuntu20.2), konqueror (>=
         4:3.5.6-0ubuntu20.2), konsole (>= 4:3.5.6-0ubuntu20.2), kpager (>= 4:3.5.6-0ubuntu20.2), kpersonalizer (>=
         4:3.5.6-0ubuntu20.2), ksmserver (>= 4:3.5.6-0ubuntu20.2), ksplash (>= 4:3.5.6-0ubuntu20.2), ksysguard (>=
         4:3.5.6-0ubuntu20.2), ktip (>= 4:3.5.6-0ubuntu20.2), kwin (>= 4:3.5.6-0ubuntu20.2), libkonq4 (>= 4:3.5.6-0ubuntu20.2),
         hal, pmount
Recommends: kdm (>= 4:3.5.6-0ubuntu20.2)
Suggests: kdebase-doc-html (>= 4:3.5.6-0ubuntu20.2)
Description: base components from the official KDE release
 KDE (the K Desktop Environment) is a powerful Open Source graphical desktop environment for Unix workstations. It combines
 ease of use, contemporary functionality, and outstanding graphical design with the technological superiority of the Unix
 operating system. 
 
 This metapackage includes the nucleus of KDE, namely the minimal package set necessary to run KDE as a desktop environment.
 This includes the window manager, taskbar, control center, a text editor, file manager, web browser, X terminal emulator, and
 many other programs and components.

```
;)

---

### Post by kh1116 on 2007-09-07
ok i found out how to, just in case anyone ever searches this, i did it with this: [https://help.ubuntu.com/community/InstallingKDE](https://help.ubuntu.com/community/InstallingKDE)

basically i ran: sudo apt-get install kde-core kubuntu-default-settings

---

### Post by maybeway36 on 2007-09-07
Yeah, kde-core is minimal KDE and kubuntu-defult-settings is the decorations for Kubuntu. Good idea :) I should try using that.

---

