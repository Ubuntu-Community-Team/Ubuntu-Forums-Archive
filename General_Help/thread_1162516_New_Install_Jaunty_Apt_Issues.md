---
title: "New Install Jaunty Apt Issues"
date: 2009-05-17
forum: General Help
---

### Post by steever on 2009-05-17
Hi I hope someone can help ...

I am getting this error whenever I apt-get update:

> W: GPG error: [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release: The following signatures were invalid: NODATA 2
W: GPG error: [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) jaunty Release: The following signatures were invalid: NODATA 2
W: GPG error: [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) jaunty-updates Release: The following signatures were invalid: NODATA 2

I have tried deleting the apt-sources list and then regenerating it, and I have deleted the auth keys and restored the default ones.

This is a new install of ubuntu jaunty.  Does anyone have a fix that does not involve re-installation?

Thanks in advance

---

### Post by oldos2er on 2009-05-17
Looks like the key for [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) is here: [http://au.archive.ubuntu.com/ubuntu/project/ubuntu-archive-keyring.gpg](http://au.archive.ubuntu.com/ubuntu/project/ubuntu-archive-keyring.gpg)

 Add the key to your keyring via the menus System, Administration, Software Sources, Authentication.

---

