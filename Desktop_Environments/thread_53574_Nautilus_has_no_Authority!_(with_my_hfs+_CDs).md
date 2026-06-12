---
title: "Nautilus has no Authority! (with my hfs+ CDs)"
date: 2005-08-01
forum: Desktop Environments
---

### Post by pizzach on 2005-08-01
I'm fighting to have my x86 laptop load up my hfs+ cdroms/dvds without problems from my oldish PPC Mac.   I've loaded up the hfs utils from synaptic (hfsplus, hfsutils, hfsutils-tcltk, libhfsp-dev, and libhfsp0.) 

I've also edited my fstab to load up the drive automatically which is currently:
/dev/scd0    /media/cdrom0    udf,iso9600,hfsplus    ro,usr,noauto,umask=000    0    0

I can access my cd through the terminal as root.  But I can't play the movies as root because there is no sound.  Not to mention using root to watch movies is sorta abusing it's purpose.  I can copy the movie off of the CD but that is working around the problem.

The question is, is there any way I can access the CD without root-ing into it?  I recently just tried adding umask=000 to my fstab to see if it would help, but it didn't give me read permissions I had hoped for.  This would also fix the problem of nautalus having an "authority" error upon insertion of a CD I think. Right now my system is in japanese but I'm guessing the word is "authority". Sorry  :razz: 

Anywho, any ideas anyone?  Thanks in advance!

---

### Post by adwait on 2005-08-01
The word you are looking for is "permissions".

In /etc/fstab....you could try adding the uid=1000 and gid=1000 (assuming you are the first user created in the system) to the options llist..

---

### Post by pizzach on 2005-08-01
Good call.  The exact error is:

**The folder contents could not be displayed.**
You do not have the permissions necessary to view the contents of "cdrom0"

Got off of my but and examined it in english.  :)
I am the first and only user, but uid and gid did not work. :(  Still the same error.  

If this helps, ls -l yields:
```

-rw-r--r--    1    501    99    282370680    2004-04-20 06:16    myFreakingCoolMovie.mkv

```

A lot of it is obvious but some of it I don't know how it interpret.

---

### Post by adwait on 2005-08-01
According to these results, the file has read access for everyone.....so reading it shouldn't be a problem for anyone......

---

### Post by pizzach on 2005-08-01
What about this?

```

drwx------    1    501    501    25    2004-05-03    15:46    cdrom0

```

---

### Post by adwait on 2005-08-01
Hmm...according to this only the user has authority to access the file...and anybody else can't do anything, not even read the file. Maybe thats your problem....

---

