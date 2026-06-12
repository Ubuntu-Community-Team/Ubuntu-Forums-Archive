---
title: "apt-get upgrade errors"
date: 2006-08-17
forum: Desktop Environments
---

### Post by JCorrea920 on 2006-08-17
I can run

```
apt-get update
```

just fine. But when I run

```
apt-get upgrade
```

I get errors while processing the upgrade and at the end I get this:

```
Errors were encountered while processing:
 tetex-base
 tetex-bin
 tetex-extra
 jadetex
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

What could this be:?:  Where should I start looking for solutions:?:   :confused:

---

### Post by philippe_carlo on 2006-08-17
What does
```

apt-get install -f

```
give you?

---

### Post by stinedvd on 2006-09-21
I get the same errors.  Here is a little more of the errors:
###############################################################################
fmtutil: Error! Not all formats have been built successfully.
Visit the log files in directory
  /var/lib/texmf/web2c
for details.
###############################################################################

This is a summary of all `failed' messages and warnings:
`etex -ini  -jobname=jadetex -progname=jadetex &latex jadetex.ini' failed

fmtutil failed. Output has been stored in
/tmp/tetex.postinst.XXgWjvGk
Please include this file if you report a bug.
dpkg: error processing tetex-base (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of tetex-bin:
 tetex-bin depends on tetex-base (>= 3.0-4); however:
  Package tetex-base is not configured yet.
dpkg: error processing tetex-bin (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of tetex-extra:
 tetex-extra depends on tetex-base (>= 3.0-11); however:
  Package tetex-base is not configured yet.
 tetex-extra depends on tetex-bin (>= 2.99); however:
  Package tetex-bin is not configured yet.
dpkg: error processing tetex-extra (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of jadetex:
 jadetex depends on tetex-bin (>= 2.0.1-1); however:
  Package tetex-bin is not configured yet.
 jadetex depends on tetex-extra (>= 2.0.1-2); however:
  Package tetex-extra is not configured yet.
dpkg: error processing jadetex (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 tetex-base
 tetex-bin
 tetex-extra
 jadetex
E: Sub-process /usr/bin/dpkg returned an error code (1)


Any Ideas?

---

### Post by stinedvd on 2006-09-21
ok found the fix.  Here's what I did.
ran 
$sudo apt-get remove tetex-base
$sudo apt-get install tetex-base

re-ran 
$sudo apt-get install ubuntu-base
$sudo apt-get install ubuntu-desktop

no more errors.

---

