---
title: "w32codecs fail to install"
date: 2006-04-07
forum: Desktop Environments
---

### Post by Sef on 2006-04-07
When installing the w32codecs I get his message:

> sef@jokat1:~/Desktop$ sudo dpkg -i w32codecs_20051412-0.0_i386.deb
Password:
dpkg: error processing w32codecs_20051412-0.0_i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 w32codecs_20051412-0.0_i386.deb


The package is on my desktop, and multiverse and universe are open, so what is going on?

---

### Post by trent dillman on 2006-04-07
Try ```
sudo dpkg -i w32*.deb
```

Or maybe that's a Debian (not Ubuntu) .deb....

---

### Post by Rory on 2006-04-07
What repository are you drawing them from?  Check out my Ubuntu Guide Reborn link.  This guide tells you how to install these codecs and which repos to use.  I'm guessing this will be nothing new to you but perhaps a different repo might do the trick for you.

R.

---

### Post by Mustard on 2006-04-07
The error seems to indicate that the package name has been spelt incorrectly ('doesn't exist seems to have been eliminated').

---

### Post by Sef on 2006-04-07
> What repository are you drawing them from?

The one under Restricted Formats.

> The error seems to indicate that the package name has been spelt incorrectly ('doesn't exist seems to have been eliminated').

Thanks Mustard.  Maybe they updated them or something.  Should check it out and see what I can find there.

---

### Post by Mustard on 2006-04-07
[QUOTE=Sef]The one under Restricted Formats.



Thanks Mustard.  Maybe they updated them or something.  Should check it out and see what I can find there.[/QUOTE]

Trent's solution above should work if the package name is different from the instructions you might be working from.  Either that or use the TAB key to autocomplete the name after typing in the first few letters.

---

### Post by Sef on 2006-04-08
Rory: all installed fine except the w32codecs I got this message below:

> sef@jokat1:~$ sudo apt-get install w32codecs
Reading package lists... Done
Building dependency tree... Done
Package w32codecs is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package w32codecs has no installation candidate


---

### Post by Sef on 2006-04-08
Tried it again from ftp.nerim.net and all went well.  Don't know why, just know it did. :)

Thank you Rory, Mustard, and trent dillman for your support.

---

