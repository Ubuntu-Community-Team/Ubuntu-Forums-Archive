---
title: "Automatix + Update Manager"
date: 2006-01-01
forum: General Help
---

### Post by thessem on 2006-01-01
When the updater or Automatix installs packagers, where on the filesystem are they stored?

I'm just wondering this because I have a dialup internet connection and multiple ubuntu computers and I dont like having to download huge packages more than once.

---

### Post by mazelado on 2006-01-01
Check in /var/cache/apt/archives.

You can also use apt-get with the '-d' option to tell it to download the packages and not install them. Then you could use dpkg to install the packages you downloaded.

---

### Post by thessem on 2006-01-02
Thanks mazelado, you have solved half my problem.

The automatix packages don't seem to be in /var/cache/apt/archives, any idea on how to find them?

---

