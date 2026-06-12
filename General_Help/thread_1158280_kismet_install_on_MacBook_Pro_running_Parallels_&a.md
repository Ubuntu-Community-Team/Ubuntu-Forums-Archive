---
title: "kismet install on MacBook Pro running Parallels &amp; Ubuntu 9.04"
date: 2009-05-13
forum: General Help
---

### Post by wrytous on 2009-05-13
Hi, I'm having trouble getting kismet installed and running on my new MacBook Pro running Parallels & Ubuntu 9.04 (Jaunty Jackalope).

Are there any tutorial docs or other howto's out there?

Thanks,
-wrytous

---

### Post by WIGGMPk on 2009-05-13
I believe Kismet is in the repositories, so it should just be:

```
sudo apt-get install kismet
```

Configuring Kismet to work properly can be tricky if your not familiar with your wireless device drivers.

These websites should give you the information you need to get everything working properly. Its just a matter of determining what wireless drivers your using and putting them into the config file.

```
http://www.kismetwireless.net/documentation.shtml
http://ubuntuforums.org/showthread.php?t=412145
http://www.twistedethics.com/2007/04/25/how-to-setup-kismet-in-ubuntu-704/
```

---

