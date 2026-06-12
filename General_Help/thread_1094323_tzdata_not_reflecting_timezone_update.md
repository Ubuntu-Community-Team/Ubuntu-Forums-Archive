---
title: "tzdata not reflecting timezone update"
date: 2009-03-12
forum: General Help
---

### Post by jimmer72 on 2009-03-12
Sorry if this is answered in another post. 

Here's what I've done so far:

1. downloaded tzdata-2009b.tar.gz
2. extracted all files
3. zic northamerica
4. zic backward

This should update everything right? Wrong.

my output for 'zdump -v /usr/share/zoneinfo/NZ | grep 2009' is:

/usr/share/zoneinfo/NZ  Sat Apr  4 13:59:59 2009 UTC = Sun Apr  5 02:59:59 2009 NZDT isdst=1 gmtoff=46800
/usr/share/zoneinfo/NZ  Sat Apr  4 14:00:00 2009 UTC = Sun Apr  5 02:00:00 2009 NZST isdst=0 gmtoff=43200
/usr/share/zoneinfo/NZ  Sat Sep 26 13:59:59 2009 UTC = Sun Sep 27 01:59:59 2009 NZST isdst=0 gmtoff=43200
/usr/share/zoneinfo/NZ  Sat Sep 26 14:00:00 2009 UTC = Sun Sep 27 03:00:00 2009 NZDT isdst=1 gmtoff=46800

I am running v8.10 - Hardy. Any thoughts?

---

