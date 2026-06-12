---
title: "My cpan is broken"
date: 2008-12-08
forum: General Help
---

### Post by pedrotuga on 2008-12-08
Ok, maybe this should go in the programming section instead, if so, I would kindly ask the moderators to move this topic.

So, I was trying to install this cpan module called WebService::RTMAgent, but I am not being able to...
Each time i start a cpan session it prompts me with some questions asking if I want to overwrite some config files or whatever...

Is there any easy way to fix/clean this?

Here's the console output:

```
$ sudo cpan
[sudo] password for p: 

There seems to be running another CPAN process (pid 8435).  Contacting...
Other job not responding. Shall I overwrite the lockfile '/home/p/.cpan/.lock'? (Y/n) [y] y

cpan shell -- CPAN exploration and modules installation (v1.9205)
ReadLine support enabled

cpan[1]> install WebService::RTMAgent
CPAN: Storable loaded ok (v2.18)
Going to read /home/p/.cpan/Metadata
  Database was generated on Sun, 07 Dec 2008 23:26:53 GMT
Running install for module 'WebService::RTMAgent'
Running make for R/RU/RUTSCHLE/WebService-RTMAgent-0.5.tar.gz
CPAN: Digest::SHA loaded ok (v5.45)
CPAN: Compress::Zlib loaded ok (v2.008)
Checksum for /home/p/.cpan/sources/authors/id/R/RU/RUTSCHLE/WebService-RTMAgent-0.5.tar.gz ok
Scanning cache /home/p/.cpan/build for sizes
............................................................................DONE
WebService-RTMAgent-0.5/
WebService-RTMAgent-0.5/lib/
WebService-RTMAgent-0.5/lib/WebService/
WebService-RTMAgent-0.5/lib/WebService/RTMAgent.pm
WebService-RTMAgent-0.5/t/
WebService-RTMAgent-0.5/t/response.addtask
WebService-RTMAgent-0.5/t/request.getlist
WebService-RTMAgent-0.5/t/request.failrq
WebService-RTMAgent-0.5/t/request.addtask
WebService-RTMAgent-0.5/t/boilerplate.t
WebService-RTMAgent-0.5/t/response.failrq
WebService-RTMAgent-0.5/t/00-load.t
WebService-RTMAgent-0.5/t/pod-coverage.t
WebService-RTMAgent-0.5/t/request.badparam
WebService-RTMAgent-0.5/t/pod.t
WebService-RTMAgent-0.5/t/request.invalidfrob
WebService-RTMAgent-0.5/t/response.timeline
WebService-RTMAgent-0.5/t/request.getfrob
WebService-RTMAgent-0.5/t/config
WebService-RTMAgent-0.5/t/request.checktoken
WebService-RTMAgent-0.5/t/request.timeline
WebService-RTMAgent-0.5/t/request.gettoken
WebService-RTMAgent-0.5/t/response.invalidfrob
WebService-RTMAgent-0.5/t/undo.t
WebService-RTMAgent-0.5/t/response.getfrob
WebService-RTMAgent-0.5/t/response.badtoken
WebService-RTMAgent-0.5/t/request.unknown
WebService-RTMAgent-0.5/t/response.getlist
WebService-RTMAgent-0.5/t/request.badtoken
WebService-RTMAgent-0.5/t/response.unknown
WebService-RTMAgent-0.5/t/init.t
WebService-RTMAgent-0.5/t/requests.t
WebService-RTMAgent-0.5/t/request.tasklist
WebService-RTMAgent-0.5/t/response.badparam
WebService-RTMAgent-0.5/t/response.checktoken
WebService-RTMAgent-0.5/t/response.tasklist
WebService-RTMAgent-0.5/t/response.gettoken
WebService-RTMAgent-0.5/t/auth.t
WebService-RTMAgent-0.5/Changes
WebService-RTMAgent-0.5/MANIFEST
WebService-RTMAgent-0.5/.cvsignore
WebService-RTMAgent-0.5/Makefile.PL
WebService-RTMAgent-0.5/README
WebService-RTMAgent-0.5/META.yml
CPAN: File::Temp loaded ok (v0.18)

  CPAN.pm: Going to build R/RU/RUTSCHLE/WebService-RTMAgent-0.5.tar.gz

Checking if your kit is complete...
Looks good
WARNING: Setting ABSTRACT via file 'lib/WebService/RTMAgent.pm' failed
 at /usr/share/perl/5.10/ExtUtils/MakeMaker.pm line 529
Writing Makefile for WebService::RTMAgent
Could not read '/home/p/.cpan/build/WebService-RTMAgent-0.5-c9L3Nn/META.yml'. Falling back to other methods to determine prerequisites
cp lib/WebService/RTMAgent.pm blib/lib/WebService/RTMAgent.pm
Manifying blib/man3/WebService::RTMAgent.3pm
  RUTSCHLE/WebService-RTMAgent-0.5.tar.gz
  /usr/bin/make -- OK
Warning (usually harmless): 'YAML' not installed, will not store persistent state
Running make test
PERL_DL_NONLAZY=1 /usr/bin/perl "-MExtUtils::Command::MM" "-e" "test_harness(0, 'blib/lib', 'blib/arch')" t/*.t
t/00-load.........ok 1/1# Testing WebService::RTMAgent 0.5, Perl 5.010000, /usr/bin/perl
t/00-load.........ok                                                         
t/auth............frobbed -- getting token
t/auth............ok 1/7frobbed -- getting token                             
token token
t/auth............ok                                                         
t/boilerplate.....ok                                                         
        3/3 unexpectedly succeeded
TODO PASSED tests 1-3

t/init............ok 1/4Use of uninitialized value in concatenation (.) or string at /home/p/.cpan/build/WebService-RTMAgent-0.5-c9L3Nn/blib/lib/WebService/RTMAgent.pm line 293.
Use of uninitialized value in concatenation (.) or string at /home/p/.cpan/build/WebService-RTMAgent-0.5-c9L3Nn/blib/lib/WebService/RTMAgent.pm line 280.
t/init............NOK 4/4                                                    
#   Failed test 'Don't start if config file isn't XML'
#   at t/init.t line 62.
Use of uninitialized value at /home/p/.cpan/build/WebService-RTMAgent-0.5-c9L3Nn/blib/lib/WebService/RTMAgent.pm line 351
# Looks like you failed 1 test of 4.
t/init............dubious                                                    
	Test returned status 1 (wstat 256, 0x100)
DIED. FAILED test 4
	Failed 1/4 tests, 75.00% okay (less 2 skipped tests: 1 okay, 25.00%)
t/pod-coverage....skipped
        all skipped: Test::Pod::Coverage 1.08 required for testing POD coverage
t/pod.............skipped
        all skipped: Test::Pod 1.22 required for testing POD
t/requests........ok 1/12request:                                            
POST http://www.rememberthemilk.com/services/rest/
Content-Type: application/x-www-form-urlencoded

method=rtm.tasks.add&nam=adding&api_key=key&auth_token=10438&timeline=114114&api_sig=3340edd30a22e9b2c67ff206283d0b67


response:
HTTP/1.1 200 OK
Connection: keep-alive
Date: Mon, 24 Dec 2007 11:49:10 GMT
Server: nginx/RTM
Vary: Accept-Encoding
Content-Type: text/xml; charset="utf-8"
Client-Date: Mon, 24 Dec 2007 11:50:39 GMT
Client-Peer: 75.126.232.204:80
Client-Response-Num: 1
Client-Transfer-Encoding: chunked
Keep-Alive: timeout=300

<?xml version="1.0" encoding="UTF-8"?>
<rsp stat="fail"><err code="4000" msg="Task name provided is invalid."/></rsp>




t/requests........ok                                                         
t/undo............ok                                                         
Failed Test Stat Wstat Total Fail  List of Failed
-------------------------------------------------------------------------------
t/init.t       1   256     4    1  4
 (3 subtests UNEXPECTEDLY SUCCEEDED), 2 tests and 2 subtests skipped.
Failed 1/8 test scripts. 1/34 subtests failed.
Files=8, Tests=34,  2 wallclock secs ( 0.84 cusr +  0.13 csys =  0.97 CPU)
Failed 1/8 test programs. 1/34 subtests failed.
make: *** [test_dynamic] Error 255
  RUTSCHLE/WebService-RTMAgent-0.5.tar.gz
  /usr/bin/make test -- NOT OK
//hint// to see the cpan-testers results for installing this module, try:
  reports RUTSCHLE/WebService-RTMAgent-0.5.tar.gz
Warning (usually harmless): 'YAML' not installed, will not store persistent state
Running make install
  make test had returned bad status, won't install without force
Failed during this command:
 RUTSCHLE/WebService-RTMAgent-0.5.tar.gz      : make_test NO

cpan[2]> 


```

---

### Post by rbo83 on 2009-01-22
I experienced the same problem. Seems to be a problem with a Perl script. Are you trying to install this for the Enigma desktop ?

---

### Post by pedrotuga on 2009-01-24
I never heard of such thing, so I believe my answer is no.

I don't remember how, but somehow I got this module installed. I think I used the -force option.

---

### Post by rbo83 on 2009-01-27
Isee. I discovered that the Ubuntu 'cpan' command (shell script) does not support the 'force' option, so I used the perl MCPAN approach.

Enigma is a sexy desptop just advertised on Linux. see
[http://tkramar.blogspot.com/2009/01/enigma-ported-to-linux.html](http://tkramar.blogspot.com/2009/01/enigma-ported-to-linux.html)

---

