---
title: "cpan WWW::CheckSite tests fail"
date: 2008-12-02
forum: General Help
---

### Post by dguido on 2008-12-02
The following was done as the root user on Ubuntu 8.10:

```
test WWW::CheckSite
Running test for module 'WWW::CheckSite'
Running make for A/AB/ABELTJE/WWW-CheckSite-0.018.tar.gz
  Has already been unwrapped into directory /root/.cpan/build/WWW-CheckSite-0.018-OwnggQ
  Has already been made
Running make test
PERL_DL_NONLAZY=1 /usr/bin/perl "-MExtUtils::Command::MM" "-e" "test_harness(0, 'blib/lib', 'blib/arch')" t/*.t
t/00util..........ok
t/01spider........ok
t/02spider........ok 9/19Error GETing http://localhost:48047/doesnotexist.html: NOT OK at /root/.cpan/build/WWW-CheckSite-0.018-OwnggQ/blib/lib/WWW/CheckSite/Spider.pm line 220
# Looks like you planned 19 tests but only ran 10.
# Looks like your test died just after 10.
t/02spider........dubious
        Test returned status 255 (wstat 65280, 0xff00)
DIED. FAILED tests 11-19
        Failed 9/19 tests, 52.63% okay
t/10validator.....ok 7/38Error GETing http://localhost:54321/doesnotexist.html: NOT OK at /root/.cpan/build/WWW-CheckSite-0.018-OwnggQ/blib/lib/WWW/CheckSite/Spider.pm line 220
# Looks like you planned 38 tests but only ran 7.
# Looks like your test died just after 7.
t/10validator.....dubious
        Test returned status 255 (wstat 65280, 0xff00)
DIED. FAILED tests 8-38
        Failed 31/38 tests, 18.42% okay
t/11validator.....ok 6/21Error GETing http://localhost:54321/doesnotexist.html: NOT OK at /root/.cpan/build/WWW-CheckSite-0.018-OwnggQ/blib/lib/WWW/CheckSite/Spider.pm line 220
# Looks like you planned 21 tests but only ran 9.
# Looks like your test died just after 9.
t/11validator.....dubious
        Test returned status 255 (wstat 65280, 0xff00)
DIED. FAILED tests 10-21
        Failed 12/21 tests, 42.86% okay
t/20checksite.....ok
t/pod_coverage....ok
t/pod_ok..........ok
Failed Test     Stat Wstat Total Fail  List of Failed
-------------------------------------------------------------------------------
t/02spider.t     255 65280    19   18  11-19
t/10validator.t  255 65280    38   62  8-38
t/11validator.t  255 65280    21   24  10-21
Failed 3/8 test scripts. 52/132 subtests failed.
Files=8, Tests=132, 21 wallclock secs ( 6.14 cusr +  0.54 csys =  6.68 CPU)
Failed 3/8 test programs. 52/132 subtests failed.
make: *** [test_dynamic] Error 255
  ABELTJE/WWW-CheckSite-0.018.tar.gz
  /usr/bin/make test -- NOT OK
//hint// to see the cpan-testers results for installing this module, try:
  reports ABELTJE/WWW-CheckSite-0.018.tar.gz
Failed during this command:
 ABELTJE/WWW-CheckSite-0.018.tar.gz           : make_test NO
```

Can anyone else get this module to pass?

Thanks

btw, it builds and works fine on Cygwin.

---

### Post by dguido on 2008-12-07
bump

---

### Post by acicalla on 2009-11-13
Why was the reply just bump..... ? I'm having a similar issue attempting to get WWW::CheckSite to install.  I'm trying to find and understand the solution so that I can get this module installed for a script that requires it.

---

