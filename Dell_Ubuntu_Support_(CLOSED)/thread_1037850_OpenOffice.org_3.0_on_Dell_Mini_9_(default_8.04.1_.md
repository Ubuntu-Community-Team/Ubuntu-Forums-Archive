---
title: "OpenOffice.org 3.0 on Dell Mini 9 (default 8.04.1 lpia kernel)"
date: 2009-01-12
forum: Dell Ubuntu Support (CLOSED)
---

### Post by ugm6hr on 2009-01-12
Has anyone had success installing OO.org 3.0 on the Dell Mini?  I have the currently updated default lpia 8.04 kernel.

```
$uname -a
Linux ugm6hr 2.6.24-19-lpia #1 SMP Mon Nov 3 15:25:26 UTC 2008 i686 GNU/Linux
```

I've tried using the [i386 .deb]("http://openoffice.bouncer.osuosl.org/?product=OpenOffice.org&os=linuxinteldeb&lang=en-US&version=3.0.0") files after running them through the [deb2lpia]("http://ubuntuforums.org/showthread.php?p=6528287#post6528287") process.

It appears to install, and it even launches the main suite window.  However, trying to do anything at all (e.g. Open new document) causes a crash.  It then just cycles through trying to recover the (blank) new document.  This appears to affect Writer, Impress and Calc (at least), and it also crashes when trying to open the Extensions menu.

---

### Post by sandman652001 on 2009-01-18
I added these repos to my Toshiba NB100(also Lpia based) and it installed fine

deb [http://ppa.launchpad.net/openoffice-pkgs/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ubuntu) hardy main
deb-src [http://ppa.launchpad.net/openoffice-pkgs/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ubuntu) hardy main

---

### Post by ugm6hr on 2009-01-19
Thanks.

That seems to work much better.

Currently version 1:3.0.1~rc1-2ubuntu2~hardy1 

Nice to see that the PPA team are supporting lpia, even though Sun are not.

---

