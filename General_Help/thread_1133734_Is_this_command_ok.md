---
title: "Is this command ok?"
date: 2009-04-23
forum: General Help
---

### Post by runnner on 2009-04-23
I ftp upload a zip file to an ubuntu server, for example, thefile.zip, can I uncompress the zip file use "#tar zvf thefile.zip", Thanks for help!

---

### Post by unutbu on 2009-04-23
Rather, try

```
unzip thefile.zip
```
instead.

---

### Post by Nepherte on 2009-04-23
Here's some more info: tar is used for .tar, tar.gz and tar.bz2 archives. The z option in your command:
```
tar **z**vf
```
indicates it's a tar.gz archive. If you use j instead of z, it's about a .tar.bz2 archive.

In your case, unzip is the way to go as mentioned above.

---

### Post by runnner on 2009-04-23
Thank you!

---

