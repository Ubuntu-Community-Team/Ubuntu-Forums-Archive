---
title: "How do I tell what version of  a package I am running?"
date: 2008-12-16
forum: General Help
---

### Post by ToddAndMargo on 2008-12-16
Hi All,

   In CentOS, I can get my package revision with the "rpm -qa \*name\*"
command.   How do I tell what version of a package I am running
in Ubunto?  Is there a similar command?

Many thanks,
-T

---

### Post by doobiest on 2008-12-16
dpkg-query is what you want

doobiest@LinuxBox:/$ dpkg-query -l libc6

Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Cfg-files/Unpacked/Failed-cfg/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name                                                  Version                                               Description
+++-=====================================================-=====================================================-==========================================================================================================================
ii  libc6                                                 2.8~20080505-0ubuntu7                                 GNU C Library: Shared libraries

---

### Post by pennacook on 2008-12-16
You could use dpkg.
 It will give you version as well.
```
dpkg -l
```

For example:
```

 dpkg -l '*vi*'

```
would give you any packages related to vi.

---

### Post by drs305 on 2008-12-16
Here's another way (don't add the '* | grep "Version" * ' for even more package info):
```
aptitude show <packagename> | grep "Version"

```
Example:
```
me@mycomputer:~$ aptitude show gimp | grep "Version"
Version: 2.6.1-1ubuntu3

```

---

### Post by ToddAndMargo on 2008-12-16
> **doobiest said:**
> dpkg-query is what you want


Thank you!  I have tried both the "-l" and the "-s" options.
Lots of info!

-T

---

