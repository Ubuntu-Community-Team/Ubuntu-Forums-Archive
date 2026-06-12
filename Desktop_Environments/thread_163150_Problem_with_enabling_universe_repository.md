---
title: "Problem with enabling universe repository"
date: 2006-04-20
forum: Desktop Environments
---

### Post by thulanism on 2006-04-20
I have been trying to install FireStarter and Blue Fish from universe, but in vain.

How do I activate the universe repository?

These are the errors:

[http://za.archive.ubuntu.com/ubuntu/dists/breezy/Release.gpg:](http://za.archive.ubuntu.com/ubuntu/dists/breezy/Release.gpg:) Could not connect to za.archive.ubuntu.com:80 (196.4.160.77), connection timed out
[http://za.archive.ubuntu.com/ubuntu/dists/breezy-updates/Release.gpg:](http://za.archive.ubuntu.com/ubuntu/dists/breezy-updates/Release.gpg:) Could not connect to za.archive.ubuntu.com:80 (196.4.160.77), connection timed out
[http://za.archive.ubuntu.com/ubuntu/dists/breezy-backports/Release.gpg:](http://za.archive.ubuntu.com/ubuntu/dists/breezy-backports/Release.gpg:) Could not connect to za.archive.ubuntu.com:80 (196.4.160.77), connection timed out
[http://security.ubuntu.com/ubuntu/dists/breezy-security/Release.gpg:](http://security.ubuntu.com/ubuntu/dists/breezy-security/Release.gpg:) Could not connect to security.ubuntu.com:80 (82.211.81.138), connection timed out
[http://archive.ubuntu.com/ubuntu/dists/breezy/Release.gpg:](http://archive.ubuntu.com/ubuntu/dists/breezy/Release.gpg:) Could not connect to archive.ubuntu.com:80 (85.133.25.7), connection timed out

Please help!!!

---

### Post by sYs^ on 2006-04-20
Did you try any other servers? Try removing za. from your /etc/apt/sources.list then sudo apt-get update and try installing again.

---

### Post by thulanism on 2006-04-20
I removed the za. from source.list, but when I try to update apt-get, I get stuck at 44% (connecting to security.ubuntu.com) until the connection is timed out.

Does anyone know the list of other servers I can try?

Please help?

---

### Post by sYs^ on 2006-04-20
Try to generate a list with this: [http://www.ubuntulinux.nl/source-o-matic](http://www.ubuntulinux.nl/source-o-matic)

---

