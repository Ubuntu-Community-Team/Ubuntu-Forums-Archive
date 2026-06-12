---
title: "Splashy in Breezy?"
date: 2006-03-26
forum: Desktop Environments
---

### Post by BrianB on 2006-03-26
How do I set up splashy in breezy, I've read the HOWTO for hoary but can't find the lib++dfb-0.9-22 deb anywhere?

---

### Post by Bazon on 2006-03-26
1. Uninstall *Usplash* via Synaptic.
(You may have to uninstall *Ubuntu-Desktop* as well, but that really doesn't hurt...)

2. Download these files in a new folder:
[http://splashy.alioth.debian.org/debian/pool/main/s/splashy/splashy_0.1.8-0+12_i386.deb](http://splashy.alioth.debian.org/debian/pool/main/s/splashy/splashy_0.1.8-0+12_i386.deb)
[http://splashy.alioth.debian.org/debian/pool/main/s/splashy/splashy-themes_0.1.8-0+12_all.deb](http://splashy.alioth.debian.org/debian/pool/main/s/splashy/splashy-themes_0.1.8-0+12_all.deb)
(Versionnumber may vary in the future, search [here](http://splashy.alioth.debian.org/debian/pool/main/s/splashy/) in that case...)

3. Change to that directory in your terminal and type:
sudo dpkg -i *.deb

4. If you want to configure in /etc/splashy/ (easy to understand config files)

That should be all, at least worked for me :)

---

