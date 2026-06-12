---
title: "repository error"
date: 2005-06-11
forum: Desktop Environments
---

### Post by vaskark on 2005-06-11
I recently re-installed hoary, updated my apt-get sources, and have been getting errors like this:

Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/universe/g/gftp/gftp-text_2.0.18-2_i386.deb]("http://us.archive.ubuntu.com/ubuntu/pool/universe/g/gftp/gftp-text_2.0.18-2_i386.deb")  MD5Sum mismatch

Anyone know what I can do to fix it?

---

### Post by Seth on 2005-06-11
[QUOTE=vaskark]I recently re-installed hoary, updated my apt-get sources, and have been getting errors like this:

Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/universe/g/gftp/gftp-text_2.0.18-2_i386.deb]("http://us.archive.ubuntu.com/ubuntu/pool/universe/g/gftp/gftp-text_2.0.18-2_i386.deb")  MD5Sum mismatch

Anyone know what I can do to fix it?[/QUOTE]
 US and CA archives are on the fritz.

Sudo gedit /etc/apt/sources.list and change all us.archive to just archive.

[http://archive.ubuntu.com/whatever](http://archive.ubuntu.com/whatever)

---

### Post by vaskark on 2005-06-11
Worked. Thanks.

---

