---
title: "Update Manager Error"
date: 2009-01-16
forum: General Help
---

### Post by Paul Vega on 2009-01-16
Kia Ora

I have been recently getting error messages on running Update Manager. These have been slowly getting larger and now the following is the message:

"W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-backports Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-security/Release](http://archive.ubuntu.com/ubuntu/dists/hardy-security/Release)  

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-backports/Release](http://archive.ubuntu.com/ubuntu/dists/hardy-backports/Release)  

W: Some index files failed to download, they have been ignored, or old ones used instead."

Can anyone tell me how to fix this?

Many thanks - Paul V

---

### Post by zvacet on 2009-01-16
```
sudo apt-get update
```

---

### Post by Paul Vega on 2009-01-17
Many thanks...that did the trick. Has it fixed this issue permanently or will I need to run this command again?

---

