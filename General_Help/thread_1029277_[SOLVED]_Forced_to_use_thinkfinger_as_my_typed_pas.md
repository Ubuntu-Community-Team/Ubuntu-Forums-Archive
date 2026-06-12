---
title: "[SOLVED] Forced to use thinkfinger as my typed password no longer works"
date: 2009-01-03
forum: General Help
---

### Post by clw3388 on 2009-01-03
Hi guys.. Kinda a strange issue hoping someone can help.
I upgraded ubuntu to 8.10 last night and now my thinkfinger is kinda tweaked...
First it wouldn't work at all so i went here 
[https://launchpad.net/~jon-oberheide/+archive](https://launchpad.net/~jon-oberheide/+archive)

as it is a "known issue" and Jon had a great fix to get think to work which it does now.. 

Problem is i can only use the biometric for my password authentication..
Example:
```
sudo ls
Password or swipe finger: 
Sorry, try again.
Password or swipe finger: 
```
 my password errors out when typed but my finger works fine on top of that once errored out the first time neither method works until action is canceled and restarted or a new terminal is started..


Im thinking i got something screwed up in my /etc/pam.d/common-auth

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
auth    sufficient      pam_thinkfinger.so
auth    required        pam_unix.so try_first_pass nullok_secure
# here's the fallback if no module succeeds
auth	requisite			pam_deny.so
# prime the stack with a positive return value if there isn't one already;
# this avoids us returning an error just because nothing sets a success code
# since the modules above will each just jump around
auth	required			pam_permit.so
# and here are more per-package modules (the "Additional" block)
# end of pam-auth-update config

Has anyone else exerienced this or know how to fix?? suggestions?

(rather early here so i hope i made sense need coffee)

---

### Post by Dr Small on 2009-01-03
Fingerprint readers were invented for users with fat fingers. Could this be your case? :D Just kidding.

---

### Post by clw3388 on 2009-01-03
> **Dr Small said:**
> Fingerprint readers were invented for users with fat fingers. Could this be your case? :D Just kidding.

Lol i wish that was the case.. It be much easier to fix :)

---

### Post by konungursvia on 2009-01-03
Can you not use your finger to authenticate yourself, then change passwords?

---

### Post by clw3388 on 2009-01-03
I did try this both from the users and groups from X and from a command prompt...
It accepts my swipe as authentication but then tells me to bugger even after changed...

I Did edit out 2 lines in common-auth and all seems to be working now? still a strange one... 
##auth	requisite			pam_deny.so
##auth	required			pam_permit.so

With these 2 edited out both swipe and my pw work fine... not sure why..
Well so long as its working now i guess..

Thanks for your responses peeps :)

---

