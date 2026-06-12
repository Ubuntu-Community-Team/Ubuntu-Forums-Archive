---
title: "apcupsd"
date: 2005-03-31
forum: Desktop Environments
---

### Post by Blackneto on 2005-03-31
> APC UPS Power Management
Controls / monitors the status of an APC UPS under Linux.
Allows your computer or server to run for a specified length of
time on UPS power, and then executes a controlled shutdown in
the case of an extended power failure

I had a bit of trouble with this today. 
the default init.d script has some lines in it:
> echo -n "Please check your configuration and then remove this"
echo    " warning to make apcupsd work"
exit 0

even if you comment it out theres a line just before that:
> . $CONFIG

that needs to be commented out.
otherwise you will end up with an error like:
> /etc/init.d/apcupsd: line 2: UPSCABLE: command not found


Thanks to Adam Kropelin on  [email]apcupsd-users@lists.sourceforge.net[/email] for pointing out this.

HTH...

Leon

---

### Post by labrador on 2005-04-11
This is still broken in the released version of Hoary.

I made these changes to /etc/init.d/apcupsd:

```
# diff apcupsd-original apcupsd
8c8,9
< CONFIG=/etc/default/apcupsd
---
> #CONFIG=/etc/default/apcupsd
> CONFIG=/etc/apcupsd/apcupsd.conf
16c17
< . $CONFIG
---
> #. $CONFIG
18,23c19,24
< if [ $ISCONFIGURED = no ]
< then
<       echo -n "Please check your configuration "
<       echo    " ISCONFIGURED in /etc/default/apcupsd"
<       exit 0
< fi
---
> #if [ $ISCONFIGURED = no ]
> #then
> #     echo -n "Please check your configuration "
> #     echo    " ISCONFIGURED in /etc/default/apcupsd"
> #     exit 0
> #fi
```

---

### Post by jdawdy on 2005-10-29
It appears the Breezy repository version for apcupsd has some bugs, especially regarding USB cables:
From the apcupsd website:
> 
3.10.18 (21 July 2005) [ Source  /  RPMs  /  Win32 ]
Apcupsd version 3.10.18 is a bug-fix only release; there are no new features. Users with USB connections are especially recommended to upgrade. This version contains changes for compatibility with linux 2.6.12 kernels, and a fix for crashes on HPUX systems, a fix for 'control queue full' lockups with certain USB models (650 CS, 800 RS, possibly others). Also included are minor fixes to apctest when used with a blank DEVICE setting (which is the recommended configuration for USB) and a BSD USB shutdown fix for ES models.


I downloaded the source and compiled the program, which went off without a hitch.  
./configure
sudo make
sudo make install
then edit config file (I only changed the device and cable options)

Jim

---

