---
title: "Synaptic doesn't work (7.04 Feisty Fawn)"
date: 2008-12-20
forum: General Help
---

### Post by Idanwin on 2008-12-20
I'm still working with 7.04 Feisty Fawn.
The synaptic package manager doesn't work anymore.

First of all all packages are marked "NOT AUTHENTICATED".

Second whenever I try to install a package I get an error message.
When installing abiword, for example, the following error:
> W: Failed to fetch [http://be.archive.ubuntu.com/ubuntu/pool/main/a/abiword/abiword-common_2.4.6-1.1ubuntu2_all.deb](http://be.archive.ubuntu.com/ubuntu/pool/main/a/abiword/abiword-common_2.4.6-1.1ubuntu2_all.deb)
  404 Not Found


W: Failed to fetch [http://be.archive.ubuntu.com/ubuntu/pool/main/a/abiword/abiword_2.4.6-1.1ubuntu2_i386.deb](http://be.archive.ubuntu.com/ubuntu/pool/main/a/abiword/abiword_2.4.6-1.1ubuntu2_i386.deb)
  404 Not Found

When I searched on the internet I saw that the package: [http://be.archive.ubuntu.com/ubuntu/pool/main/a/abiword/abiword_2.4.6-1.1ubuntu2_i386.deb](http://be.archive.ubuntu.com/ubuntu/pool/main/a/abiword/abiword_2.4.6-1.1ubuntu2_i386.deb) doesn't exist.

When trying to install another of the packages it says "**libart 2.0-2**" is not installed.
After searching it in the archives I noticed it *was* already installed.
Abiword kept saying it wasn't.

[getting of topic in the first post already?]

---

### Post by bapoumba on 2008-12-20
[http://old-releases.ubuntu.com/releases/](http://old-releases.ubuntu.com/releases/)
Feisty is not supported any longer, and the repos have been moved.

---

### Post by Idanwin on 2008-12-20
That's nice!
Problem solved (technically).

Is upgrading save?

---

### Post by Woody1987 on 2008-12-20
Upgrading to 8.10 should be perfectly safe, although as a precaution you should back up your /home directory just in case.

---

### Post by Iowan on 2008-12-20
Dunno if you can upgrade direct - you might need to go from 7.04 to 7.10 to 8.04, then to 8.10... or do a fresh install.

---

### Post by dcstar on 2008-12-20
> **Iowan said:**
> Dunno if you can upgrade direct - you might need to go from 7.04 to 7.10 to 8.04, then to 8.10... or do a fresh install.

If you have a separate /home partition then you can basically do a fresh install of any version and still keep your user files.

If you don't have a separate /home then you have to manually back that up before the fresh install (as it is wiped by the standard install if it remains in the root partition).

---

