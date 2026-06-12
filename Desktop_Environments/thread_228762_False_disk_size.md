---
title: "False disk size"
date: 2006-08-03
forum: Desktop Environments
---

### Post by jd65pl on 2006-08-03
Hi,

This is what i have done

1. Copied my ubuntu install using partimage
2. Restructured my partitions on hd0
3. Restored my ubuntu install to my new partition

The only problem I am experiencing is that it appears that my partition has 21gb used?!? when infact my ubuntu was only previously 3gb!?

This is shown when i view the drive in gparted and the resource manager.

Does anyone have any ideas?

Thanks

J

---

### Post by hikaricore on 2006-11-07
You may want to check you /var/logs directory for any large files as well as the file .xsession-errors in your ~ directory, if something is spitting errors into a file this can easily fill your hard drive in a matter of hours.  Had this happen after I upgraded to edgy awhile back, my .xsession-errors file was 11.4gb.

* edit: i just noticed I was replying to a post from August, thought it said November >.<  *

---

### Post by jd65pl on 2006-11-07
> **hikaricore said:**
> You may want to check you /var/logs directory for any large files as well as the file .xsession-errors in your ~ directory, if something is spitting errors into a file this can easily fill your hard drive in a matter of hours.  Had this happen after I upgraded to edgy awhile back, my .xsession-errors file was 11.4gb.

* edit: i just noticed I was replying to a post from August, thought it said November >.<  *
Yeah I sort of fixed this only, problem was that zero blocks of data had been written to the disk so it looked as if it had been used. Only solution was to reformat the disk and start again!

---

