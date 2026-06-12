---
title: "how do i install a .deb?"
date: 2005-01-13
forum: General Help
---

### Post by kwanbis on 2005-01-13
hi, i'm fairly new to linux (i only installed mandrake/redhat/suse in the past for some minutes to try), but i'm finally desided to use it, and as debian is the distro i like most, i thought ubuntu should do ;) ... so ... i installed it into my Notebook with no visible problem, connected to the internet (in fact, i'm posting from there), and such ... but now i want to install a .deb package i downloaded, as i can't seem to make apt-get work (i have to read more, but basically, it does not connects to the internet using the proxy) ... but have no idea what to do, (i have been googling it) ... help please?

---

### Post by kwanbis on 2005-01-13
[QUOTE=kwanbis]hi, i'm fairly new to linux (i only installed mandrake/redhat/suse in the past for some minutes to try), but i'm finally desided to use it, and as debian is the distro i like most, i thought ubuntu should do ;) ... so ... i installed it into my Notebook with no visible problem, connected to the internet (in fact, i'm posting from there), and such ... but now i want to install a .deb package i downloaded, as i can't seem to make apt-get work (i have to read more, but basically, it does not connects to the internet using the proxy) ... but have no idea what to do, (i have been googling it) ... help please?[/QUOTE]
 ok ... dpkg -i file.deb ... appears to be the answer ... =)

---

### Post by Johan on 2005-01-13
[QUOTE=kwanbis]ok ... dpkg -i file.deb ... appears to be the answer ... =)[/QUOTE]
 Yep, that's it! Strange that apt-get doesn't work. If your internet connection is configured properly it really should work.

---

### Post by az on 2005-01-13
apt-get uses a database.  A file you download into your home directory has nothing to do with that database.  If you add a repository to your sources.list file and then do an
apt-get update

your database is updated with the new packages. You then apt-get them.

Dpkg is the backend to the package management.  apt uses dpkg.

---

