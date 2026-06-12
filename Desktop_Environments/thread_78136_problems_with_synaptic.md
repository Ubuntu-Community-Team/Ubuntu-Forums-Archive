---
title: "problems with synaptic"
date: 2005-10-17
forum: Desktop Environments
---

### Post by nix4me on 2005-10-17
im getting these errors:

W: GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

What up with this?

nix

---

### Post by aysiu on 2005-10-17
Take out the *us* in your repositories.

---

### Post by dbott67 on 2005-10-17
Lots of posts on this subject.  The answer can be found in this thread:
> This sources.list has worked for others with similar problems, as noted in [this thread]("http://www.ubuntuforums.org/showthread.php?p=411974").

---

### Post by nix4me on 2005-10-17
Worked like a champ.  Thanks.  Weird though.

The us was working a couple days ago.  Oh well, no worries.

nix

---

### Post by dbott67 on 2005-10-17
Glad it worked.

-Dave

---

