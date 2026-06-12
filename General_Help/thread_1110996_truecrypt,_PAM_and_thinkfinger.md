---
title: "truecrypt, PAM and thinkfinger"
date: 2009-03-30
forum: General Help
---

### Post by daking874 on 2009-03-30
Hi I'm running Ubuntu 8.10 on a Thinkpad X41 laptop. All seemed fine (although I hadn't yet run truecrypt to set up a secure file) until I installed the thinkfinger package to get the fingerprint reader up and running.

This caused problems first-off as the installation routine hadn't correctly set up /etc/pam.d/common-auth so sudo was double asking for a password and always failing. I resolved this by manually editing common-auth.

Now everything seems to work except truecrypt which loads up fine but when I try to mount a file is asks for the volume password, then the password for administrator privileges. It now always "failed to obtain administrator privileges".

I can see it has something to do with thinkfinger from the syslog:

Code:
Mar 30 12:48:41 ian-laptop kernel: [  326.344048] input: Virtual ThinkFinger Keyboard as /devices/virtual/input/input15
Mar 30 12:48:41 ian-laptop kernel: [  326.685289] sudo[6047]: segfault at 35 ip b7fc6472 sp b762a360 error 4 in libc-2.8.90.so[b7f55000+158000]


which is similar to the error previously when common-auth was not set correctly.

Anyone have any advice? I'll post common-auth in a moment

---

### Post by daking874 on 2009-03-30
Incidentally, from a terminal, typing in sudo asks for my Password or finger swipe which works but su only asks for a password (finger swipe doesn't work) despite the /etc/pam.d/su file having "@include common-auth"

Final point which may be relevant, I cannot use a finger swipe to unlock the screen saver despite having edited gnome-screensaver.

I think something is up with my PAM configuration but any expertise on this would be great.

---

### Post by daking874 on 2009-03-30
and my common-auth file


```
#
# /etc/pam.d/common-auth - authentication settings common to all services
#
# This file is included from other service-specific PAM config files,
# and should contain a list of the authentication modules that define
# the central authentication scheme for use on the system
# (e.g., /etc/shadow, LDAP, Kerberos, etc.).  The default is to use the
# traditional Unix authentication mechanisms.
#
# As of pam 1.0.1-5, this file is managed by pam-auth-update by default.
# To take advantage of this, it is recommended that you configure any
# local modules either before or after the default block, and use
# pam-auth-update to manage selection of other modules.  See
# pam-auth-update(8) for details.

# here are the per-package modules (the "Primary" block)
auth   sufficient   pam_thinkfinger.so
auth   [success=1 default=ignore]   pam_unix.so try_first_pass nullok_secure
# here's the fallback if no module succeeds
auth   requisite         pam_deny.so
# prime the stack with a positive return value if there isn't one already;
# this avoids us returning an error just because nothing sets a success code
# since the modules above will each just jump around
auth   required         pam_permit.so
# and here are more per-package modules (the "Additional" block)
# end of pam-auth-update config
```

---

### Post by daking874 on 2009-03-30
finally I can run truecrypt from the terminal using sudo truecrypt (and, ironically, a finger swipe) create a volume, edit the volume owner (otherwise I cannot write anything to the volume as it is owned by root) remount and copy data to it.

A little painful but at least its limping along...

I've also posted this to the truecrypt forum [http://forums.truecrypt.org/viewtopic.php?p=66249#66249]("http://forums.truecrypt.org/viewtopic.php?p=66249#66249")

---

### Post by daking874 on 2009-04-01
bump. anyone? There must be a genius at this kind of thing out there somewhere...

---

### Post by daking874 on 2009-04-04
rebump

---

### Post by captain_171 on 2009-05-05
So i did not get your question. is the question that you can not mount the true-crypt volume with user permissions so that the user can RWX is that the question?

---

### Post by goodman3 on 2009-05-05
I next try it with an **truecrypt** file bacause you can chose the algorithms and 
  **...** **pam** authentication for keyring with **thinkfinger**, Blue_Ice

---

