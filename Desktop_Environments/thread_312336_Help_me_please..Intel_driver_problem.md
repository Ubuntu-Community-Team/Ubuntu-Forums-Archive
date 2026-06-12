---
title: "Help me please..Intel driver problem"
date: 2006-12-04
forum: Desktop Environments
---

### Post by gejr on 2006-12-04
I installed these drivers. I downloaded a rpm file and aliened it into .deb and dpkg -i'ed it...it produced a bunch of errors and now my beryl won't work anymore. When running "beryl --replace" i get this:

[HTML]geo@box:~$ beryl --replace
XGL Absent, checking for NVIDIA
Nvidia Absent, assuming AIGLX
beryl: glXBindTexImageEXT is missing
beryl: Failed to manage screen: 0
beryl: No manageable screens found on display :0.0
[/HTML]

Is there any way to revert to the old drivers? or get another working driver running here instead?

---

### Post by igknighted on 2006-12-04
You should be able to remove it with dpkg as well.  I am unsure why you would try to install drivers from an RPM... the intel drivers in the repo's are by far the most complete of any graphics drivers with Ubuntu.  Also, alien is not perfect, so something as critical as a video driver should never be installed from an RPM.

EDIT: use dpgk --help for the proper syntax

---

### Post by gejr on 2006-12-04
I tried dpkg -P <alien converted package.deb>
and got "dpkg: you must specify packages by their own names, not by quoting the names of the files they come in"

Not sure how to do that..and how do I get the intel drivers from the repos? what are they called?

---

### Post by gejr on 2006-12-05
Ended up reinstalling ubuntu..it's becoming a habit now, and every time I manage to make my system cleaner and better =) Too bad I always lose my documents/images/music etc. though...

I should have a different partition for such stuff:)

---

### Post by zgornel on 2006-12-05
> **gejr said:**
> Ended up reinstalling ubuntu..it's becoming a habit now, and every time I manage to make my system cleaner and better =) Too bad I always lose my documents/images/music etc. though...

I should have a different partition for such stuff:) As a matter of fact it's a very good idea to put /home on a different partition or drive so that reinstalling linux won't make you loose settings/documents.

---

