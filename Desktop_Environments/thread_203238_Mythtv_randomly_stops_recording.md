---
title: "Mythtv randomly stops recording"
date: 2006-06-24
forum: Desktop Environments
---

### Post by vigleik on 2006-06-24
I've installed mythtv 0.19 (compiled from source) on my old desktop, and it's working just fine, most of the time. But at random times it "forgets" all the upcoming recordings, like it's lost contact with the database or something. I wiped the hard drive and reinstalled, but the problem persists.

I know getting help with this problem is a longshot, but has anyone else experienced this? Or better, does anyone know if this is/will be fixed in 0.19.1 or 0.20?

Vigleik

---

### Post by vigleik on 2006-07-01
In case anyone else has the same problem, it's caused by mysql5 behaving differently than mysql4, and the mythtv developers struggled with this for a while. Updating to a newer version (stable 0.19 branch, which contains bug fixes from 0.19) from [http://svn.mythtv.org/trac/](http://svn.mythtv.org/trac/) seems to have fixed the problem.

Vigleik

---

