---
title: "scim and m17n"
date: 2006-09-20
forum: Desktop Environments
---

### Post by cesera on 2006-09-20
I am trying to setup m17n support in skim. I have installed the scim-m17n package, but don't seem to be able to find any way of accesing the input methods provided by libm17n. Does anyone have any ideas as to what I need to do next? I am using kubuntu dapper.

---

### Post by omiazad on 2006-10-01
Hey Cesera!
We have a designation of this Ubuntu, which is LTS. What does it mean. You won't get any supprt by a sort time? You have to wait long for the support?

Mods
This guy faced the problem in May and today I faced the same problem. But I'm very sad to see no one came up with a solution so far. 

This IS a Ubuntu build problem. After we add m17n, we cannot see anything related to m17n in SCIM. But it works in Debian. So what is the solution?

Anyone? Anything? Helloooooooooooooooooo...

---

### Post by thedarklord on 2006-10-04
Hellow , omiazad hope u remember me

---

### Post by zmr on 2007-01-26
Maybe this information is a few months too late, but Dapper made a mistake with its distibution of m17n library and database (the m17n-lib and m17n-db) files; they are mismatched so that one is version 1.3 and the other is 1.2. As a result SCIM and UIM can't use m17n without fixing some files. I am not sure exactly what you need to do in SCIM, but for UIM a solution is documented here:

[http://www.m17n.org/mlarchive/m17n-lib/200610/msg00008.html](http://www.m17n.org/mlarchive/m17n-lib/200610/msg00008.html)

I have voiced this problem to Ubuntu but am not sure it's got any attention or if a bug report has been made elsewhere. The problem is fixed in Edgy - both the lib and db files are version 1.3.

---

### Post by haseeb on 2008-02-04
scim seems not working with m17n in my case. i am using ubuntu 7.1 64bit.

---

