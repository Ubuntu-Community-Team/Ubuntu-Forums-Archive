---
title: "'bundled' software and the update manager"
date: 2010-10-13
forum: Desktop Environments
---

### Post by EricLorenz on 2010-10-13
Hi everyone-

I wasn't sure where to post this (as I did not see a forum specifically devoted to software on Ubuntu) so I thought I'd start here. I switched to Evolution a few months ago, and for the most part love it. However, I notice that the version that Ubuntu has as 'current' is 2.28.3, while the current released version is 2.30/2.32.

My question is, how/who determines what/when software packages installed w/Ubuntu are updated. I would like to go to the current version, but it seems to not be available for Ubuntu yet? Or is it, and maybe my install is configured incorrectly as to not detect it?

Thanks in advance for the help.

Eric

---

### Post by DougieFresh4U on 2010-10-13
Don't know what version of Evolution as I don't use it but are your settings in Synaptic>Settings:

---

### Post by EricLorenz on 2010-10-13
Hi-

Now they are...almost. Changed the upgrade to 'normal release' and checked proposed releases, but not sure about unsupported releases....what will that do for me?

So, would that mean that Ubuntu is not supporting the 'current' release of evolution yet?

Thanks,
Eric

> **DougieFresh4U said:**
> Don't know what version of Evolution as I don't use it but are your settings in Synaptic>Settings:

---

### Post by mcduck on 2010-10-13
The basic rule is that after a release, the program versions in Ubuntu releases are not updated. You only get updates to fix more serious bugs, and for security fixes.

This allows better testing of all programs together, and makes Ubuntu more stable platform. (There *are* other Linux distributions that use rolling-release scheme instead and thus always offer you the latest and greatest versions of all programs, if you prefer that over stability.)

Anyway, there are ways how some programs can be updated, as long as the update fits certain conditions. And I believe Canonical even made the rules a bit looser recently so we might see a few more programs in the repositories updated to latest versions in the future. But the best way to go if you need the latest version for some program are the PPA repositories. Whatever you need, most likely someone is already providing a PPA with up-to-date versions of it. ;)

Just don't expect latest versions of all programs to appear in the official repositories. That's not going to happen.

---

