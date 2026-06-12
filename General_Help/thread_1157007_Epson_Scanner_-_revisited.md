---
title: "Epson Scanner - revisited"
date: 2009-05-12
forum: General Help
---

### Post by leopoldb on 2009-05-12
DO NOT WASTE TIME READING THIS

I have a red face, DoctorMo had already created a phantabulous fix for ths problem and I hadn't searched first.
Bad me, lesson learned.

Leopold B.





Epson V500 scanner support is a moving ball.

Installing the Avasys iscan support was not fruitful on 8.10 so I stopped trying.  Recently I upgraded to 9.04 and decided to try again.  I noted that Avasys indicated 9.04 support.  Yay.

It failed with a libltdl3 dependency problem.   With some searching this made sense as libltdl3 has been replaced with libltdl7.  I have to believe that that broke a bunch of packages.
Hilariously, I found that Avasys provided a way around the libltdl3 problem on 8.10 on April 9 ([http://avasys.jp/hp/page000001300/hpg000001286.htm](http://avasys.jp/hp/page000001300/hpg000001286.htm)).  If I hadn't upgraded to Jaunty I'd likely be happily scanning.  Oh well.

So, can anybody help with this l3 vs l7 situation in Jaunty?

Thanks all,

Leopold B.

---

### Post by DoctorMO on 2009-05-18
Glad you found the iscan package I uploaded to my PPA useful. :-)

---

