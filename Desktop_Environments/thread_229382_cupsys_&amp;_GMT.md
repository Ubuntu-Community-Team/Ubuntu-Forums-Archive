---
title: "cupsys &amp; GMT"
date: 2006-08-04
forum: Desktop Environments
---

### Post by jmkuhn on 2006-08-04
Using Ubuntu Dapper.

I have a bug when printing PostScript files created with GMT (Generic
Mapping Tools).  I create PostScript file with the following command:

/usr/lib/gmt/bin/psxy --PAPER_MEDIA=letter -R1/7.5/1/10 -JX6.5i/9i -Ba1f0.25WSne -P /dev/null > test.ps

The resulting test.ps file previews correctly in gv and every other
PS viewer I have tried.  When I print the file, the resulting page
has my figure magnified about 4x such that the lower left of the
figure fills the entire page.  I get the same result on 4 different
PostScript printers (different models and manufacturers).

Other PostScript files generated in OOo or Firefox print correctly.

If I copy the test.ps file to an Ubuntu Hoary system (or old Debian,
HP-UX, Mac OSX ...) the file prints correctly on the same 4 printers.

Any ideas?
John

---

