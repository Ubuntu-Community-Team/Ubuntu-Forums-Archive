---
title: "Error Fixing on Hard drive ruins everything! :' (  dpkg/status error"
date: 2009-01-13
forum: General Help
---

### Post by winrowc on 2009-01-13
Ubuntu shut down improperly yesterday, and when it restarted it checked for errors on the harddrive. When it did eventually start working again, the package manager was broken with the error:

'E:Encountered a section with no Package: header, E: Problem with MergeList /var/lib/dpkg/status, E:The package lists or status file could not be parsed or opened.'

I have tried various fixes, by replacing status with status-old and status-bad and nothing has worked. Is my only solution to reinstall ubuntu? CUPS also disappeared so I have to go through the whole process of reinstalling the printer, as well as the VIA motherboard audio drivers, which can't be done unless the package manager is fixed. Doing it manually (sudo apt-get...)just leads to the same dpkg/status error.

---

### Post by dcstar on 2009-01-13
> **winrowc said:**
> Ubuntu shut down improperly yesterday, and when it restarted it checked for errors on the harddrive. When it did eventually start working again, the package manager was broken with the error:

'E:Encountered a section with no Package: header, E: Problem with MergeList /var/lib/dpkg/status, E:The package lists or status file could not be parsed or opened.'
.........

My "available" file seems identical to my "status" file, perhaps you could copy yours and see if that helps?

---

### Post by winrowc on 2009-01-14
At first I thought it had worked as I can now see the packages that could be installed, but alas it comes up with the same errors. The status file can't have "Size" in it and all sorts of different syntax things are wrong that can't be fixed. How else can I repair this file? I never thought I could render Ubuntu completely useless by fixing supposed errors on the harddrive(which I don't think were really there, the improper shutdown was due to holding the power button down, not a crash). I can't reinstall, I don't have anywhere to backup all my stuff. Can I just delete this status file and redownload all the updates?

---

### Post by winrowc on 2009-01-14
I replaced the status file with one in the Var/backups folder from January 4 which should have been fine, but still errors. Why is it telling me there is something wrong with a copy of a "status" file that worked fine before?

---

### Post by winrowc on 2009-01-14
Can anyone help me? There is no way that I can do a backup to reinstall as I don't have any other hard drives, so this is my only option.

---

