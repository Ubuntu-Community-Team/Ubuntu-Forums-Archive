---
title: "dpkg problem..."
date: 2006-01-08
forum: General Help
---

### Post by Zaventh on 2006-01-08
Slight problem all of the sudden...

When I run any dpkg commands (and consequently apt commands) I get the following error:

```
Reading package lists... Error!
E: Problem parsing dependency Depends
E: Error occurred while processing kompare (NewVersion1)
E: Problem with MergeList /var/lib/dpkg/status
E: The package lists or status file could not be parsed or opened.

```

I haven't installed kompare recently, but I do have it installed.

If I do a "sudo dpkg-reconfigure kompare" I get the following:

```
dpkg-query: parse error, in file `/var/lib/dpkg/status' near line 20052 package `kompare':
 `Depends' field, syntax error after reference to package `libice.n'
/usr/sbin/dpkg-reconfigure: kompare is not installed
```

But it is installed and working. Dpkg has also been working since today.

---

### Post by Zaventh on 2006-01-08
Not exactly sure what happened but I got it sorted out: 
```
sudo cp /var/backups/dpkg.status.0 /var/lib/dpkg/status
```

EDIT...

Except, now I get this when installing packages...:
```
Preconfiguring packages ...
dpkg: parse error, in file `/var/lib/dpkg/available' near line 14697 package `kubuntu-desktop':
 `Depends' field, invalid package name `2$rts': character `$' not allowed - only letters, digits and -+._ allowed
E: Sub-process /usr/bin/dpkg returned an error code (2)
```


EDIT 2:

Alright... I'm tinkering faster than people are replying... I think I got the available file resolved by doing a "sudo dpkg --clear-avail && sudo apt-get update" ... Hope this helps someone someday.

---

### Post by grinias on 2006-01-09
Thanx for the post my friend :) Since, I suffer often from problems of this kind, it will help me for sure, in the near future.

---

### Post by Zaventh on 2006-01-09
I hate to talk to myself so much... but unfortunately I have the same problems again. What could be causing this corruption? I tried to install fluxbox via apt-get and got the following error:

```
Do you want to continue [Y/n]? y
Use of uninitialized value in substitution (s///) at /usr/share/perl5/Debconf/Format/822.pm line 57, <$__ANONIO__> line 5149.

Preconfiguring packages ...
dpkg: parse error, in file `/var/lib/dpkg/status' near line 29097 package `xserver-xorg-driver-fbdev':
 field name `0dhis' must be followed by colon
E: Sub-process /usr/bin/dpkg returned an error code (2)

```

My aforementioned fix isn't working this time, either..

---

### Post by grinias on 2006-01-18
For me, the problem solved once I uninstalled the gnome desktop and working in pure kubuntu.

---

