---
title: "Why &quot;write failed&quot; when merely blanking dvd+rw?"
date: 2009-04-21
forum: General Help
---

### Post by logos34 on 2009-04-21
here's what I get when I nullify a dvd+rw:

> $ **growisofs -Z /dev/dvd=/dev/zero**
WARNING: /dev/dvd already carries isofs!
About to execute 'builtin_dd if=/dev/zero of=/dev/dvd obs=32k seek=0'
/dev/dvd: "Current Write Speed" is 4.1x1352KBps.
    1605632/4700372992 ( 0.0%) @0.0x, remaining 341:25 RBU 100.0% UBU   2.0%
    1605632/4700372992 ( 0.0%) @0.0x, remaining 487:44 RBU 100.0% UBU 100.0%
    1605632/4700372992 ( 0.0%) @0.0x, remaining 682:50 RBU 100.0% UBU 100.0%
    1605632/4700372992 ( 0.0%) @0.0x, remaining 829:09 RBU 100.0% UBU 100.0%
    8454144/4700372992 ( 0.2%) @1.5x, remaining 184:59 RBU 100.0% UBU  67.3%
   27426816/4700372992 ( 0.6%) @4.1x, remaining 68:09 RBU 100.0% UBU  59.2%
   45416448/4700372992 ( 1.0%) @3.9x, remaining 46:07 RBU 100.0% UBU  55.1%
   64389120/4700372992 ( 1.4%) @4.1x, remaining 35:59 RBU 100.0% UBU  53.1%
   82411520/4700372992 ( 1.8%) @3.9x, remaining 31:45 RBU 100.0% UBU  59.2%
  101253120/4700372992 ( 2.2%) @4.1x, remaining 28:00 RBU 100.0% UBU  55.1%

...

 4600266752/4700372992 (97.9%) @3.9x, remaining 0:18 RBU 100.0% UBU  59.2%
 4619141120/4700372992 (98.3%) @4.1x, remaining 0:15 RBU 100.0% UBU  55.1%
 4637065216/4700372992 (98.7%) @3.9x, remaining 0:11 RBU 100.0% UBU  55.1%
 4655972352/4700372992 (99.1%) @4.1x, remaining 0:08 RBU 100.0% UBU  53.1%
 4674060288/4700372992 (99.4%) @3.9x, remaining 0:04 RBU 100.0% UBU  55.1%
 4692836352/4700372992 (99.8%) @4.1x, remaining 0:01 RBU 100.0% UBU  57.1%
[COLOR="Red"]:-[ WRITE@LBA=230540h failed with SK=5h/ASC=21h/ACQ=02h]: Invalid argument
:-( write failed: Invalid argument[/COLOR]
/dev/dvd: flushing cache
/dev/dvd: stopping de-icing
/dev/dvd: writing lead-out
/dev/dvd: reloading tray

$ 

Why?  I can successfully format with 

dvd+rw-format -force /dev/dvd

No error messages.  (I have a reason for formatting rather than simply overwriting it as usual)

---

