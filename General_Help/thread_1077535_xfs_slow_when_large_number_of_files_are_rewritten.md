---
title: "xfs slow when large number of files are rewritten"
date: 2009-02-22
forum: General Help
---

### Post by wfjm on 2009-02-22
I've used xfs for / and /home for a new 8.10 installation (/boot is ext3).

I observed that the file system gets slow when a large number (many thousand) of existing files are re-written. So I setup a simple test, which writes 2000 files with 8kB each. I tried on a ext3 and a xfs file system, and ran it several times. The 1st pass created the files, the other ones re-write them. Results:

```
ext3 1st:  real 0m0.180s  user 0m0.060s  sys 0m0.120s
ext3 2nd:  real 0m0.195s  user 0m0.040s  sys 0m0.150s

xfs 1st:   real 0m4.348s  user 0m0.030s  sys 0m0.140s
xfs 2nd:   real 0m1.847s  user 0m0.080s  sys 0m0.160s
xfs 3rd:   real 0m35.437s  user 0m0.070s  sys 0m0.130s
```

--> xfs gets real slow in the 3rd (sometime also 2nd) round, 
--> when files are re-written rather than created. Also, the
--> disk gets noisy in the 3rd try, indicating a lot of seeks.

Changing the test script such that a file is always deleted before it is written avoid this drastic performance drop, one ends up with about 9sec for 2000 files, and no noise from the disk.

xfs is 'all default' as they come with 8.10.

Is that 'works as designed', or is there a way to improve this very unsatisfactory performance behavior.

---

