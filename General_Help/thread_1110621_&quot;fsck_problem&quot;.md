---
title: "&quot;fsck problem&quot;"
date: 2009-03-30
forum: General Help
---

### Post by suresh_vandiyur on 2009-03-30
I do let it run and It says...
*checking root file system...
1075
Fsck 1.41.3 (12-oct-2008 )
/Lib/init/rw/rootdev contains a file system with errors, check forced.
/Lib/init/re/rootdev: unattached inode 286889

/lib/init/rw/rootdev: UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY
(i.e., without -a or -p options)
Fsck died with exit status 4

{red colored}* an automatic file system check (fsck) of the root filesystem failed. A manual fsck must be performed, then the system restarted. The fsck should be performed in maintinence mode with the root filesystem mounted in read only mode.
{green or orange (I'm colorblind)}* the root filesystem is currently mounted in read only mode.
A maintinence shell will now be started.
After performing system maintinence press CONTROL-D to terminate the maintinence shell and restart the system.
Bash: no job control in this shell
Root@ubuntu:~# _

This pops up every time... I am at a loss I have no idea what to do... Again any help is appriciated.

Thank you
________****

---

### Post by dcstar on 2009-03-30
> **suresh_vandiyur said:**
> I do let it run and It says...
*checking root file system...
1075
Fsck 1.41.3 (12-oct-2008 )
/Lib/init/rw/rootdev contains a file system with errors, check forced.
/Lib/init/re/rootdev: unattached inode 286889

/lib/init/rw/rootdev: UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY
(i.e., without -a or -p options)
Fsck died with exit status 4

{red colored}* an automatic file system check (fsck) of the root filesystem failed. A manual fsck must be performed, then the system restarted. The fsck should be performed in maintinence mode with the root filesystem mounted in read only mode.
{green or orange (I'm colorblind)}* the root filesystem is currently mounted in read only mode.
A maintinence shell will now be started.
After performing system maintinence press CONTROL-D to terminate the maintinence shell and restart the system.
Bash: no job control in this shell
Root@ubuntu:~# _

This pops up every time... I am at a loss I have no idea what to do... Again any help is appriciated.

Thank you
________****

Boot off a live CD, then:

```
sudo fsck /dev/whatever-it-is
```

---

### Post by suresh_vandiyur on 2009-03-30
> **dcstar said:**
> Boot off a live CD, then:

```
sudo fsck /dev/whatever-it-is
```

Thank u.. is there any other option for this problem?
 in our system dont have cd drive.
but we have the net connection.
is it possible to solve without a cd?????

---

### Post by Jaded_Phoenyx on 2009-04-02
:confused: :confused: :confused: I am having this exact same problem and it started on Monday, March 30th.  I also do not have a cd drive atm because mine has gone out on my laptop.  I'd really like to know if someone knows of an alternate way to fix this problem as well.  ](*,)  its truly driving me bananas.

---

