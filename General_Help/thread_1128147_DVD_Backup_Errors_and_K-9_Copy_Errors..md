---
title: "DVD Backup Errors and K-9 Copy Errors."
date: 2009-04-17
forum: General Help
---

### Post by leveliv on 2009-04-17
```
*** libdvdread: CHECK_VALUE failed in ifo_read.c:1575 ***
*** for c_adt->cell_adr_table[i].start_sector < c_adt->cell_adr_table[i].last_sector ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:1571 ***
*** for c_adt->cell_adr_table[i].vob_id > 0 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:1573 ***
*** for c_adt->cell_adr_table[i].cell_id > 0 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:1575 ***

```

This is the error that keeps replaying when I press READ in DVD Back up.


And in K-9 Copy it does the same thing actually, so no need to post that error. It seems to be with LibDVDREAD ...I have .0.9.7x.x.x installed. 

I used to back up my DVDs all the time with this program (k9) so I figured it was just the program but, If anyone can lend a hand, it would be appreciated.  Thanks

---

### Post by leveliv on 2009-04-20
well if anyone wanted to know ..I just updated it via the Updates app and it works fine now, Apparently it was just that version on libdvdread

---

