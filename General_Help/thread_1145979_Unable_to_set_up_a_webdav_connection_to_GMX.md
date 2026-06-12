---
title: "Unable to set up a webdav connection to GMX"
date: 2009-05-02
forum: General Help
---

### Post by stakh on 2009-05-02
It just beats me. I can't get to access my webdav space at GMX. They even [provide instructions for Konqueror](https://help.gmx.com/storage/network/linux/?si=2thgk.1jNWfl.4796AU.o**):

> 
Integrating as Network Drive via Linux Konqueror

   1. In the Konqueror search field enter the address **webdavs://storage-file-eu.gmx.com/** (or webdavs://storage-file-us.gmx.com if you reside in the USA).
   2. The following dialog box prompts you to enter your GMX E-Mail Address and Password. Click OK.
   3. Your File Storage opens in your Konqueror browser.


Wish it did... In my kubuntu jaunty, using Konqueror for this gives me a black screen, I can't even switch to tty1 (kde is pretty unstable in jaunty, at the moment). So I tried it with dolphin, but it fails authentication.

Did anyone in jaunty manage to get access to a remote webdav space, and to GMX in particular?

---

### Post by stakh on 2009-05-02
Just to add a bit more info:

I tried to use the davfs route: 

```

$ sudo mount -t davfs -o uid=me,gid=me https://storage-file-eu.gmx.com/ /home/myself/GMX
Please enter the username to authenticate with server
https://storage-file-eu.gmx.com/ or hit enter for none.
Username: myself@gmx.net
Please enter the password to authenticate user myself@gmx.net with server
https://storage-file-eu.gmx.com/ or hit enter for none.
Password:
/sbin/mount.davfs: Mounting failed.
401 Authorization Required

```

So it looks like this is an authentication issue. GMX update manager works fine at work (or at least it did, two days ago), so I'm wondering what the problem is. 

Anyone managing to reach GMX via webdav, on any platform? Or to put it under another perspective, does anyone manage to access a secured remote webdav space with jaunty?

---

### Post by stakh on 2009-05-02
Ok, forget about the whole issue, the problem here is GMX, not jaunty or kubuntu.

I setup an account at mydisk.se, and webdavs://mydisk.se/myself works fine in dolphin

I give up on GMX, as mydisk.se not only works out of the box, but also offers double the space.

---

