---
title: "Software Install Problem"
date: 2006-08-24
forum: Desktop Environments
---

### Post by javarunner on 2006-08-24
After downloading a tarball (.tar.gz) I issue the following cmd:
tar -xzvf filename.tar.gz
This unpacks the archive and creates a directory called filename.
I then cd to that directory and issue the following:
./configure
Instead of preparing for a 'make', the system responds with 'no such file or directory'.
Why would the system think that ./configure is a directory, or perhaps that whatever ./configure is doing is running into a missing directory problem
I'm stuck.  Can anyone help.
Thanks.

---

### Post by crackseller on 2006-08-24
Not all sources come with a configure script. Check the README or INSTALL file of the package, it should tell you how to handle it.

---

