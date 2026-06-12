---
title: "Evince: &quot;Failed to execute child process&quot;"
date: 2010-12-30
forum: Desktop Environments
---

### Post by rmcd on 2010-12-30
I have a pdf file with an embedded hyperlink. If I click on the link in acroread, I am given a warning ("The document is trying to connect to ...") and am asked if I wish to proceed. If I click yes, firefox opens the link.

If I click on the link in Evince, I get the message "Failed to execute child process "/opt/firefox/firefox" (Permission denied)" (I have beta 8 of firefox installed). Executables in the firefox directory are root:root 755.

This appears in syslog:

> Dec 30 14:08:03 laptop kernel: [318713.881253] type=1503 audit(1293739683.737:37):  operation="exec" pid=27480 parent=27479 profile="/usr/bin/evince" requested_mask="::x" denied_mask="::x" fsuid=1000 ouid=0 name="/opt/firefox/firefox"

Can someone help me understand why evince is failing to open the link? Thanks!

Bob

---

### Post by Chris_82 on 2011-01-09
This seems to be apparmor not allowing evince to open external documents as it can be a risky if one opens untrusted things..
I think evince's profile could be changed so apparmor will allow opening these files.
I do not (yet) know how to do this..

ps: I am having the same problem with a text file which should be opened by gedit.

cheers.

---

### Post by rmcd on 2011-01-09
Apparmor, ah! Excellent! Thank you!

A solution is:

```
sudo ln -s /etc/apparmor.d/usr.bin.evince /etc/apparmor.d/disable/usr.bin.evince
sudo /etc/init.d/apparmor restart
```

This totally disables apparmor protection for evince. Probably not ideal, but the documentation for apparmor is slow going and I can't see how to change the specific behavior for https links.

Looking at [apparmor docs]("https://help.ubuntu.com/community/AppArmor"), it seems that apparmor_parser will reload the (disabled) profile without restarting apparmor.

---

### Post by Chris_82 on 2011-01-10
> **rmcd said:**
> Apparmor, ah! Excellent! Thank you!

Welcome :-)
> **rmcd said:**
> 
A solution is:
```
sudo ln -s /etc/apparmor.d/usr.bin.evince /etc/apparmor.d/disable/usr.bin.evince
sudo /etc/init.d/apparmor restart
```


I dare say it's more a workaround than a solution..but as long as there is no alternative this is acceptable :-).

cheers.

---

### Post by hunteke on 2011-02-05
> ```
sudo ln -s /etc/apparmor.d/usr.bin.evince /etc/apparmor.d/disable/usr.bin.evince
sudo /etc/init.d/apparmor restart
```

This totally disables apparmor protection for evince.

Note that acroread has *no* apparmor protections, so with the completely disabled solution for Evince, you're no worse off than you were with Adobe's product.  However, if apparmor is a possibility, I still suggest "doing the right thing."  Here's the syntax you need:

```
/usr/bin/firefox   Px,
```

Put that on it's own line, somewhere within the [FONT="Courier New"]/usr/bin/evince { ... }[/FONT] declaration in /etc/apparmor.d/usr.bin.evince.  (I put it on the last line, just before the closing brace.)

You can choose one of [FONT="Courier New"]px[/FONT], [FONT="Courier New"]Px[/FONT], [FONT="Courier New"]ux[/FONT], [FONT="Courier New"]Ux[/FONT], [FONT="Courier New"]ix[/FONT].  If you just want something working, the above should work.  It's the safest of the *x options.  For more info, look to '[FONT="Courier New"]man apparmor.d[/FONT]'

> Probably not ideal, but the documentation for apparmor is slow going and I can't see how to change the specific behavior for https links.

I don't immediately see a way to block http vs https.  In fact, other than blocking all TCP connections but on port 443, there is no way, because one of the things that SSL provides is complete, end-to-end encryption.  In other words, there's no way for apparmor to detect that an https connection is being made.  All it would know is that it didn't understand the information it saw going out.

---

### Post by hugmenot on 2011-02-07
No, put that rule into /etc/apparmor.d/local/usr.bin.evince.

Here the associated README:

```
# This directory is intended to contain profile additions and overrides for
# inclusion by distributed profiles to aid in packaging AppArmor for
# distributions.
#
# The shipped profiles in /etc/apparmor.d can still be modified by an
# administrator and people should modify the shipped profile when making
# large policy changes, rather than trying to make those adjustments here.
#
# For simple access additions or the occasional deny override, adjusting them
# here can prevent the package manager of the distribution from interfering
# with local modifications. As always, new policy should be reviewed to ensure
# it is appropriate for your site.
#
# For example, if the shipped /etc/apparmor.d/usr.sbin.smbd profile has:
#   #include <local/usr.sbin.smbd>
#
# then an administrator can adjust /etc/apparmor.d/local/usr.sbin.smbd to
# contain any additional paths to be allowed, such as:
#
#   /var/exports/** lrwk,
#
# Keep in mind that 'deny' rules are evaluated after allow rules, so you won't
# be able to allow access to files that are explicitly denied by the shipped
# profile using this mechanism.
/etc/apparmor.d/local/README (END) 

```

---

