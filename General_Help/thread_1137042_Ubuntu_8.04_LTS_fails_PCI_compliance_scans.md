---
title: "Ubuntu 8.04 LTS fails PCI compliance scans"
date: 2009-04-25
forum: General Help
---

### Post by DigiConstructor on 2009-04-25
I recently upgraded our systems from CentOS 4.2 with PHP4 to Ubuntu 8.04 LTS PHP5, but I am being told by Security Metrics and Comodo that we have a huge security vulnerability because of the PHP version.
I have applied all the latest Ubuntu patches, updates and upgrades as of 4/25/09.
We are being told that since we are using a PHP version < 5.2.9, we are using a version of PHP that has multiple critical security vulnerabilities and are failing PCI compliance scans primarily due to this.
I will report these to Comodo as false positives for now, because I looked into it and we do show only 5.2.4-2, but also that it is protected by the Suhosin Patch 0.9.6.2 of the Hardened-PHP Project.
Comodo says that 5.2.4 is affected by multiple critical security vulnerabilities.  I believe these known vulnerabilities may be addressed by the hardened PHP patch, and the version is just indicative of enhancement features not present, and not security holes.

Is this even a flaw to report, that Ubuntu 8.04 LTS is failing PCI compliant tests because of the PHP version number being reported?  I am trying to let Comodo know this information but I think Ubuntu should know too.

Can someone help me?
Thank you

---

### Post by kostkon on 2009-04-25
Despite the fact that the PHP versions are older, security patches are applied to them for any new vulnerabilities, e.g. check [this recent security update]("http://www.ubuntu.com/usn/USN-761-1") that came 5 days ago.

But, that's the only info I can give, sorry.

---

### Post by DigiConstructor on 2009-04-25
Thank you.
I contested it as a false positive.  In looking up reasoning for the lower version number, it was noted that the older PHP version still had patches applied, and lists the older version number to indicate feature enhancements not present.
It's weird that PCI security scans from two companies are so generic they do not take patches into regard and only look at the version number though.
I don't think this is a bug to report and mostly wondered who to let know that [HackerGuardian]("http://www.hackerguardian.com/index-new.html") sees the old version number itself as a security risk.  I've advised them to look deeper at the patches applied, since the scan indicated patches as well.

This does help as it confirms that security patches are applied, regardless of the PHP version reported.
Thanks again!:popcorn:

---

