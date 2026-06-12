---
title: "request: RealTek audio driver"
date: 2005-12-26
forum: Deferred/Invalid Requests
---

### Post by kozimodo on 2005-12-26
On my Fujitsu S6240 I get sound from the speakers but not the headphone jack.  I have read elsewhere in the forums that installing the newest driver fixes this problem.  But but the automatic install does not seem to work for my configuration  as now I have no sound at all.  And it is not clear how to do the manual install as Ubuntu does not have a modules.conf file. A backport of the driver would be useful for noobs like myself.

---

### Post by jdong on 2006-01-02
This is a kernel space backport, which is simply not done due to the complicity of the backport and the ensuing support mess in case kernels need to be updated and the ABI changes.

---

