---
title: "Will samba or nfs work for sharing with mac?"
date: 2006-07-04
forum: Desktop Environments
---

### Post by tefflox on 2006-07-04
How can I set up a network share with a mac?  In the system -> admin -> shared folders it says i need one of these programs, but to share with windows or unix.  Mac is unix-like, so should I use one of these programs?

{update:  I've set it so it should be accessible via nfs://host/path/to/share, the only command to which the mac responds: "Could not connect to the server because the name or password is incorrect."  I'm at a loss, and really appreciate the help this forum offers.

---

### Post by simonn on 2006-07-04
Have a look at:

[http://www.atmos.washington.edu/~salathe/osx_unix/nfsmount.html](http://www.atmos.washington.edu/~salathe/osx_unix/nfsmount.html)

particularily: 

"First, you need to have the administrator of the unix system give your machine permission to mount volumes on that system. You will have very disappointing results otherwise. Also, if you did not set your uid number to that on the unix system (see previous step), you will not have owner privileges for your files on the mounted volume."

Your mac will use the uid number and password you are logged in as to log into the linux box. The uid is the number which corresponds to your user id.

---

