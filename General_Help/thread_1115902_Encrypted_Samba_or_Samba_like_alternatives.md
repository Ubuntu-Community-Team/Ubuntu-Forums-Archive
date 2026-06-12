---
title: "Encrypted Samba or Samba like alternatives?"
date: 2009-04-04
forum: General Help
---

### Post by paradigm2 on 2009-04-04
Hello.  I use a community wireless router to access the internet from one of my machines in a far corner of the house.  My laptop usually is plugged in.  What concerns me is that anyone with the router key passphrase could in theory sniff and see every file I transfer over my samba shares between these two computers.  I know that the password is encrypted, but that isn't enough for me.

Now I know Samba is typically used by windows users.  And I also know about SSH tunneling (I'm trying to avoid that since it appears that in doing this between two linux machines I would need to do something like bind samba to non-standard ports and then set up the tunnel -- I guess if you have a guide for that or help where you can show me what to put in smb.conf to make it bind to another port, then that will work too).

I know of scp and sftp, put I want to be able to play my music files for example from the other computer right away.  I don't want to have to transfer them manually first.

There has to be a better *nix like way to do this?  HAs anyone made an encrypted samba or some other such program?

---

### Post by albinootje on 2009-04-04
> **paradigm2 said:**
>  I know of scp and sftp, put I want to be able to play my music files for example from the other computer right away.  I don't want to have to transfer them manually first.

You didn't say what OS the server and client(s) have, but for (at least) Linux there's sshfs.
It's pretty cool.
```

sudo apt-get install sshfs
man sshfs

```
See also : [http://en.wikipedia.org/wiki/SSHFS](http://en.wikipedia.org/wiki/SSHFS) which mentions options for MacOSX and MS-Windows.

---

### Post by paradigm2 on 2009-04-04
> **albinootje said:**
> You didn't say what OS the server and client(s) have, but for (at least) Linux there's sshfs.
It's pretty cool.
```

sudo apt-get install sshfs
man sshfs

```
See also : [http://en.wikipedia.org/wiki/SSHFS](http://en.wikipedia.org/wiki/SSHFS) which mentions options for MacOSX and MS-Windows.


Sorry.  Both Ubuntu v. 9.04 Jaunty Beta.

Thank you, yes Sshfs looks like it will be perfect!  As long as I can mount it on a local partition or at least otherwise fully access the files within the native applications.

I KNEW there had to be a better way... :)

---

