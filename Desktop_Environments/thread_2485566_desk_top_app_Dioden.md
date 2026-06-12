---
title: "desk top app Dioden"
date: 2023-04-02
forum: Desktop Environments
---

### Post by John_Carver on 2023-04-02
A message at login said "clipit" not a workable app.
Substituted Dioden but can't find it

---

### Post by #&amp;thj^% on 2023-04-02
Spelling....;)
Something about app indicator vs. system tray. ... Diodon seems to be a direct replacement for the deprecated clipit:
```
diodon | 1.0.2-0ubuntu2 | trusty/universe  | source, amd64, arm64, armhf, i386, powerpc, ppc64el
 diodon | 1.3.0-1ubuntu1 | xenial/universe  | source, amd64, arm64, armhf, i386, powerpc, ppc64el
 diodon | 1.8.0-1        | bionic/universe  | source, amd64, arm64, armhf, i386, ppc64el, s390x
 diodon | 1.9.0-1        | focal/universe   | source, amd64, arm64, armhf, ppc64el, riscv64, s390x
 diodon | 1.12.0-1       | jammy/universe   | source, amd64, arm64, armhf, ppc64el, riscv64, s390x
 diodon | 1.13.0-1       | kinetic/universe | source, amd64, arm64, armhf, ppc64el, riscv64, s390x
 diodon | 1.13.0-1       | lunar/universe   | source, amd64, arm64, armhf, ppc64el, riscv64, s390x


```
```
apt show diodon
Package: diodon
Version: 1.13.0-1
Priority: optional
Section: universe/utils
Origin: Ubuntu
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Oliver Sauder <os@esite.ch>
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Installed-Size: 1,092 kB
Depends: libdiodon0 (= 1.13.0-1), zeitgeist-core (>= 0.9.14), dconf-gsettings-backend | gsettings-backend, libayatana-appindicator3-1 (>= 0.5.3), libc6 (>= 2.34), libglib2.0-0 (>= 2.46), libgtk-3-0 (>= 3.22), libpeas-1.0-0 (>= 1.1.1)
Homepage: https://launchpad.net/diodon
Download-Size: 67.4 kB
APT-Sources: http://archive.ubuntu.com/ubuntu lunar/universe amd64 Packages
Description: GTK+ Clipboard manager
 Diodon is a lightweight clipboard manager for Linux written in Vala which
 "aims to be the best integrated clipboard manager for the Gnome/Unity desktop".
 .
 Diodon features include Ubuntu indicator, clipboard sync (primary selection
 and Ctrl+C / Ctrl+V clipboard) and a zeitgeist integration for an infinite
 clipboard history.
```

```

apt policy diodon
diodon:
  Installed: (none)
  Candidate: 1.13.0-1
  Version table:
     1.13.0-1 500
        500 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lunar/universe amd64 Packages


me on Sun Apr 02 at 12:48 PM in ~ branch: (HEAD) 
>> apt policy clipit
clipit:
  Installed: (none)
  Candidate: 1.4.4+git20190202-2
  Version table:
     1.4.4+git20190202-2 500
        500 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lunar/universe amd64 Packages

```

---

### Post by John_Carver on 2023-04-04
Spelling always an issue with me
I was sure of the spelling at the time but lost agan
Thank you
Found it

---

### Post by ActionParsnip on 2023-04-04
If solved, please mark as so

---

