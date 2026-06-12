---
title: "X session fails in Gnome after upgrade"
date: 2005-02-16
forum: Desktop Environments
---

### Post by rosslaird on 2005-02-16
Well, I did my regular update this morning (Hoary), and now Gnome fails to load. The X session errors file says this:

SESSION-MANAGER=/local/ross:/tmp/.ICE-unix/7287

I removed .ICEauthority to no effect.

Xfce works fine, and I'm posting from within that (very nice) desktop.

Any ideas what's going on?

Thanks.

Ross

---

### Post by nanaban on 2005-02-16
[QUOTE=rosslaird]Well, I did my regular update this morning (Hoary), and now Gnome fails to load. The X session errors file says this:

SESSION-MANAGER=/local/ross:/tmp/.ICE-unix/7287

I removed .ICEauthority to no effect.

Xfce works fine, and I'm posting from within that (very nice) desktop.

Any ideas what's going on?

Thanks.

Ross[/QUOTE]
 Same here, I remember synaptic asking if I want to replace some gnome xml file with the new one and I picked yes.

---

### Post by nanaban on 2005-02-16
On the mailing list, a developer suggested downgrade libesd0 or wait for the new one.

How do I downgrade a package using apt-get?

---

### Post by MrRoboto on 2005-02-16
same here.. now I try to downgrade

---

### Post by Kareema on 2005-02-16
[QUOTE=MrRoboto]same here.. now I try to downgrade[/QUOTE]
Try updating - new version has just been uploaded. And it's all workin again...

---

### Post by MrRoboto on 2005-02-16
[QUOTE=Kareema]Try updating - new version has just been uploaded. And it's all workin again...[/QUOTE]
 upgraded, it works

---

### Post by dragonfly on 2005-02-16
Hmmm....
No upgrade un the us server yet.
What server are you guys using?

Tx.

---

### Post by rosslaird on 2005-02-16
At 12:15pm, Pacific Standard time, these sources worked:

```
deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Alpha i386 Binary-1 (20050204)]/ unstable main restricted


deb http://archive.ubuntu.com/ubuntu hoary main restricted
deb-src http://archive.ubuntu.com/ubuntu hoary main restricted

deb http://archive.ubuntu.com/ubuntu hoary universe
deb-src http://archive.ubuntu.com/ubuntu hoary universe

deb http://security.ubuntu.com/ubuntu hoary-security main restricted
deb-src http://security.ubuntu.com/ubuntu hoary-security main restricted

deb http://security.ubuntu.com/ubuntu hoary-security universe
deb-src http://security.ubuntu.com/ubuntu hoary-security universe

# Other sources #

deb http://archive.ubuntu.com/ubuntu/ warty multiverse
deb-src http://archive.ubuntu.com/ubuntu/ warty multiverse

deb ftp://ftp.nerim.net/debian-marillat/ stable main
deb ftp://ftp.nerim.net/debian-marillat/ unstable main
deb ftp://ftp.nerim.net/debian-marillat/ testing main

# os-works.com #

deb http://www.os-works.com/debian testing main
deb-src http://www.os-works.com/debian testing main

# gnome-sshman #
deb ftp://ftp.oronetes.net/debian main/
```

---

### Post by dragonfly on 2005-02-16
Thanks.
It's fixed. :D

---

