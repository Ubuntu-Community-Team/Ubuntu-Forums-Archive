---
title: "Copying to/from samba shares is very slow"
date: 2006-10-06
forum: Desktop Environments
---

### Post by jrjazzman on 2006-10-06
I have a Windows share that is mounted with smbfs.  Copying files to and from this share is incredibly slow.  I'm running Dapper 6.06.  any ideas how to spped things up?

---

### Post by TyphoonJoe on 2006-10-06
What is "debug level" set to?  That can greatly impact performance.  If it is set high try changing to a 0 or 1. 

Also, this seems to be a fairly common issue so if people are slow with replies I reccomend using google.

---

### Post by jrjazzman on 2006-10-06
I don't have a debug setting in smb.conf.  Where would it be?

---

### Post by TyphoonJoe on 2006-10-06
Could you share your smb.conf?  

Also I'll be away from the internet for a few days- so good luck.  Try google or hopefully someone else will help.

---

### Post by der_joachim on 2006-10-07
> **jrjazzman said:**
> I have a Windows share that is mounted with smbfs.  Copying files to and from this share is incredibly slow.  I'm running Dapper 6.06.  any ideas how to spped things up?

Try mounting that share with CIFS instead of smbfs. There are some HOWTO's on this forum. 

Good luck.

---

