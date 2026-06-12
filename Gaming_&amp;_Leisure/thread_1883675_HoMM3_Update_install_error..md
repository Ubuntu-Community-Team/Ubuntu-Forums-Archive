---
title: "HoMM3 Update install error."
date: 2011-11-19
forum: Gaming &amp; Leisure
---

### Post by nucdaddy on 2011-11-19
I'm trying to run the HoMM3 update and get the following error message :(:

/usr/local/games/Heroes3$ sudo sh heroes3-1.3.1a-unified-x86.run --keep
Creating directory heroes3-1.3.1a-unified-x86
Verifying archive integrity...tail: cannot open `+6' for reading: No such file or directory
Error in check sums 814399959 1999548749

The subdirectory "heroes3-1.3.1a-unified-x86" is set up but nothing else.

Can anyone help?

---

### Post by donkyhotay on 2011-11-21
Error fails when verifying the archive indicating you have a corrupt compressed file. If this is a download try downloading again, if it's a disc you probably have a bad disc.

---

### Post by nucdaddy on 2011-11-22
Thanks for the advice but no joy.  I downloaded the update from two different locations and get the same error message when trying to execute.

Any other advice?

---

### Post by xukosky on 2011-12-06
Try with the following command before running the HoMM3 update:
export _POSIX2_VERSION=199209

For more information: [http://www.megastep.org/makeself/](http://www.megastep.org/makeself/)

---

### Post by nucdaddy on 2011-12-14
Thanks for that info on makeself and setting the environment variable "_POSIX2_VERSON"  By all rights and everything I've read that should have worked.  Unfortunately it didn't and you're right, the problem is with the "tail" command.  It's parsing an argument (i.e. "+6") as a file.  I can't get any of the other "makeself" arguments (e.g. --verbose, --list, --info, --noexec, etc.) to work either.  I just keep getting the same error message.  Apparently Ubuntu doesn't recognize that environment variable for what ICCULUS says it should do (i.e. recognize earlier applications of "head" and "tail").

Do you know of any other way to break out this archive or do I need to load an older version of Linux?:confused:

Thanks again for your help.

Nucdaddy

---

### Post by 1204 on 2013-02-12
Well this is old thread but search engines finds it. So here is Loki_patched update which works. DL **[heroes3-1.3.1a-unified-x86-lokipatch.tar.gz]("http://www.upload.ee/files/3066573/heroes3-1.3.1a-unified-x86-lokipatch.tar.gz.html")**. Extract
```
tar -xf heroes3-1.3.1a-unified-x86-lokipatch.tar.gz
cd heroes3-1.3.1a-unified-x86-lokipatch
sh ./update.sh
```This is good guide to install homm3 and play with sound [http://forums.debian.net/viewtopic.php?f=16&t=80366](http://forums.debian.net/viewtopic.php?f=16&t=80366)

---

