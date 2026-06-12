---
title: "FTP Upload - Hangs with large uploads."
date: 2006-06-17
forum: Desktop Environments
---

### Post by mafitzpatrick on 2006-06-17
I'm trying to transfer a copy of Wordpress ([www.wordpress.org](www.wordpress.org)) up onto a remote server within nautilus.  I can log into the server/etc. just fine and transfer files.  However, when it comes to moving large directories it gets half way through and then literally hangs.

It is impossible to cancel the upload or even close the file-box window (only able to close using xkill for example). This is reproducable - I have restarted my laptop and the problem still occurs.

Any help would be much appreciated, it must be possible to upload this somehow!

---

### Post by mafitzpatrick on 2006-06-17
Solved this by using gFTP & then disabling PASV FTP on this host. Appears to be incompatible - unfortunately cannot find a place to change this from in nautilus remote-server options?

---

### Post by scxtt on 2006-06-17
what "connect to server" method are you using to connect to the 'remote server'?

---

### Post by mafitzpatrick on 2006-06-17
In nautilus I am (was) connecting using Places->Connect to Server and setting up a mounted FTP volume to copy across to.  I was using the FTP option (with username/password).  For reference the host was web host 34sp.com.

---

### Post by scxtt on 2006-06-17
and chance you can use SSH (which makes use of sFTP) instead? ... basically any server that runs SSH (also uses U/P) will allow you to connect via a secure FTP ... don't know if that'll help, but it's worth a try ...

i like gFTP a lot, btw - can't go wrong w/ it ...

---

