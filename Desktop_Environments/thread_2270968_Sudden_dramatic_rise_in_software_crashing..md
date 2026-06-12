---
title: "Sudden dramatic rise in software crashing."
date: 2015-03-26
forum: Desktop Environments
---

### Post by Sslaxx on 2015-03-26
Using 14.10 with the latest updates I'm suddenly experiencing a lot more crashes with Inkscape and Gedit (and probably other software too, but I haven't used anything else since updating). Has anyone else been experiencing this?

Also as a result getting screen corruption ala [https://dl.dropboxusercontent.com/u/67740160/Inkscape_Screen_Corruption.png](https://dl.dropboxusercontent.com/u/67740160/Inkscape_Screen_Corruption.png)

---

### Post by JohnnyComeL8ly on 2015-03-26
What does the list of packages look like from the last instance of an update in /var/log/apt/history.log   I'll show you mine:
```
Start-Date: 2015-03-26  18:05:03
Commandline: apt upgrade
Install: libssh2-1:amd64 (1.4.3-3, automatic)
Upgrade: libgnutls-openssl27:amd64 (3.2.16-1ubuntu2.1, 3.2.16-1ubuntu2.2), liblxqt-data:amd64 (0.9.0+bzr290+201503191035~ubuntu14.10.1, 0.9.0+bzr292+201503250049~ubuntu14.10.1), vlc-plugin-notify:amd64 (2.2.0~pre2-4build1, 2.2.0-0ubuntu0.14.10.1), libgnutls-deb0-28:amd64 (3.2.16-1ubuntu2.1, 3.2.16-1ubuntu2.2), libgnutls-deb0-28:i386 (3.2.16-1ubuntu2.1, 3.2.16-1ubuntu2.2), lxqt-globalkeys:amd64 (0.9.0+bzr136+201503201105~ubuntu14.10.1, 0.9.0+bzr137+201503261520~ubuntu14.10.1), libqt5xdg1:amd64 (1.1.0+bzr168+201503211931~ubuntu14.10.1, 1.1.0+bzr170+201503260141~ubuntu14.10.1), libvlccore8:amd64 (2.2.0~pre2-4build1, 2.2.0-0ubuntu0.14.10.1), libarchive13:amd64 (3.1.2-9, 3.1.2-9ubuntu0.1), vlc-nox:amd64 (2.2.0~pre2-4build1, 2.2.0-0ubuntu0.14.10.1), liblxqt0:amd64 (0.9.0+bzr290+201503191035~ubuntu14.10.1, 0.9.0+bzr292+201503250049~ubuntu14.10.1), lxqt-session:amd64 (0.9.0+bzr226+201503211131~ubuntu14.10.1, 0.9.0+bzr227+201503242331~ubuntu14.10.1), vlc-plugin-samba:amd64 (2.2.0~pre2-4build1, 2.2.0-0ubuntu0.14.10.1), libqt5xdg-data:amd64 (1.1.0+bzr168+201503211931~ubuntu14.10.1, 1.1.0+bzr170+201503260141~ubuntu14.10.1), vlc-data:amd64 (2.2.0~pre2-4build1, 2.2.0-0ubuntu0.14.10.1), lxqt-notificationd:amd64 (0.9.0.0.0+bzr102+201503191044~ubuntu14.10.1, 0.9.0.0.0+bzr104+201503242116~ubuntu14.10.1), lxqt-panel:amd64 (0.9.0.0.0+bzr755+201503230246~ubuntu14.10.1, 0.9.0.0.0+bzr760+201503251448~ubuntu14.10.1), vlc:amd64 (2.2.0~pre2-4build1, 2.2.0-0ubuntu0.14.10.1), libvlc5:amd64 (2.2.0~pre2-4build1, 2.2.0-0ubuntu0.14.10.1)
End-Date: 2015-03-26  18:05:18
```

---

### Post by JohnnyComeL8ly on 2015-03-26
I ask, because you might be able to see that a new X.org package was installed or something....

---

