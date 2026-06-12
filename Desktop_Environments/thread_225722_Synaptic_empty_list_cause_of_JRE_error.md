---
title: "Synaptic empty list cause of JRE error"
date: 2006-07-30
forum: Desktop Environments
---

### Post by jaysondin87 on 2006-07-30
E: The package jre needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.
E: Unable to lock the list directory

^^ That's what shows up in my synaptic when i try to run it.. anyone has ideas? I think i messed up installing jre... now i dont ven see the list of packages in synaptic...

Thanks in advance...

---

### Post by jaysondin87 on 2006-07-30
jayson@jays:~$ sudo apt-get remove jre
Reading package lists... Done
Building dependency tree... Done
E: The package jre needs to be reinstalled, but I can't find an archive for it.
jayson@jays:~$

:(

---

### Post by ajgreeny on 2006-07-30
Remove (uninstall) jre if it can be found, then try installing *sun-java5-jre*, which I think is the package name you want.

---

### Post by jaysondin87 on 2006-07-30
I've already installed the right one.. however.. i cant remove the jre package.. check the posts on top.

---

### Post by jaysondin87 on 2006-07-30
sudo dpkg --purge --force-remove-reinstreq jre

---

