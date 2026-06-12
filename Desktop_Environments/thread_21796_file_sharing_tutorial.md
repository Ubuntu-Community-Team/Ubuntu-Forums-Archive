---
title: "file sharing tutorial?"
date: 2005-03-23
forum: Desktop Environments
---

### Post by fizgig on 2005-03-23
Anyone know how to share folders while using kubuntu?  All the options in the file sharing section of kcontrol are grayed out.

---

### Post by fizgig on 2005-03-24
my bad.  One of the samba packages wasn't installed.  A couple were but I guess I needed more.

---

### Post by Raecer on 2005-03-25
You try adding Smb4k makes sharing easy.     :)

---

### Post by cwaldbieser on 2005-04-01
I get the following error when trying to share folders from my home directory:

> sharing folder '/home/carl/temp' failed.

An error occurred while trying to share folder '/home/carl/temp'.  Make sure that the Perl script 'fileshareset' is set to suid root.

I tried using smb4k, but I can't quite seem to figure out how to use it to share my own folders.  I was able to browse remote shares, but I have had some success doing that other ways (like smb:// URLs in konqueror).  The documentation is humorous, but not very helpful.

Needless to say, I checked the fileshareset script, and it appears to have the permissions set correctly.  I always thought setting a script suid root was some sort of a no-no, though.

Anyone have any idea why I am getting this error?

---

### Post by cwaldbieser on 2005-04-02
I just got the perl-suid package and that fixed the error.  However, the package states that it is deprecated and support will probably be removed in 5.10.

---

