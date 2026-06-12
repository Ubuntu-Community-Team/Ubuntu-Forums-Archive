---
title: "help cant apt-get update"
date: 2005-12-16
forum: General Help
---

### Post by xloader on 2005-12-16
i type sudo apt-get update
n this came out```
sudo: timestamp too far in the future: Dec 16 22:56:37 2005

```

---

### Post by RAOF on 2005-12-16
Try running "sudo -k" first.  It won't require a password.  Then try "sudo apt-get update" again.

This has probably happened because something has changes your system clock.  sudo doesn't like that, and the -k option tells it to start again, essentially :)

---

### Post by xloader on 2005-12-16
its ok now...thanx..but.the connection timed out..y?

---

### Post by xloader on 2005-12-16
can't update any program.this came out ```
http://archive.ubuntu.com/ubuntu/dists/breezy/Release.gpg: Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
http://archive.ubuntu.com/ubuntu/dists/breezy-updates/Release.gpg
http://security.ubuntu.com/ubuntu/dists/breezy-security/Release.gpg: Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
http://archive.ubuntu.com/ubuntu/dists/breezy-backports/Release.gpg
http://wine.sourceforge.net/apt/binary/Release.gpg: Could not connect to wine.sourceforge.net:80 (1.0.0.0), connection timed out

```

---

