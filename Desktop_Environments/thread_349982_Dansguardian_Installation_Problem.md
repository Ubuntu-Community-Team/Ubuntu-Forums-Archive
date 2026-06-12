---
title: "Dansguardian Installation Problem"
date: 2007-01-30
forum: Desktop Environments
---

### Post by jantzens on 2007-01-30
I'm following the HOWTO on how to install Dansguardian. When I get to Step 2 e)...I get the following:

scott@scott-laptop:~$ sudo dpkg-reconfigure dansguardian
Password:
Stopping DansGuardian: dansguardian.
Starting DansGuardian: LibClamAV Warning: ************************************************** ******
LibClamAV Warning: *** This version of the ClamAV engine is outdated. ***
LibClamAV Warning: *** DON'T PANIC! Read [http://www.clamav.net/faq.html](http://www.clamav.net/faq.html) ***
LibClamAV Warning: ************************************************** ******
LibClamAV Warning: ************************************************** ******
LibClamAV Warning: *** This version of the ClamAV engine is outdated. ***
LibClamAV Warning: *** DON'T PANIC! Read [http://www.clamav.net/faq.html](http://www.clamav.net/faq.html) ***
LibClamAV Warning: ************************************************** ******
Error connecting to parent proxy
invoke-rc.d: initscript dansguardian, action "start" failed.

I've reinstalled Dansguardian, tried to reinstall clamav and libclamav, but I can't figure out how to get it to work.

Any help would be appreciated.

SJ

---

### Post by tonhou on 2007-01-31
Have you tried a restart of the computer?

Do you  particularly want to use Clamav?

You may find that all is well, and as suggested further on in howto you can disable clamav in dansguardian conf file.

--Tony

---

