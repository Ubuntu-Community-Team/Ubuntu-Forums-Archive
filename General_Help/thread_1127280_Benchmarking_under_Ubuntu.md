---
title: "Benchmarking under Ubuntu"
date: 2009-04-16
forum: General Help
---

### Post by Rich_B_uk on 2009-04-16
Hi there chaps and chapesses!

I'm doing some benchmarking this weekend with the aim of supporting some decisions about what specifications a thick diskless client would need. I've discarded testing Network I/O in any detail because the differences between chipsets are likely to be negligible. Likewise, I'm not interested in running any GPU or HDD benchies. 

I simply want a good spread that demonstrates general system performance. I've already chosen Geekbench as it seems to be a top notch utility for this sort of think. I also want to use the Phoronix test suite but the amount of benchies it contains is a bit overwhelming. If anyone here has experience with it (or other FOSS solutions) I'd welcome some examples of well respected and easy to perform benchmarks that might fit the scenario. 

Ideas? :)

As a sidenote, I plan on performing these from a reconstructed and stripped down Live-CD environment, Xubuntu if possible - simply because some of the hardware is going to be pretty low spec.

---

### Post by phoronix on 2009-04-16
> **Rich_B_uk said:**
> I also want to use the Phoronix test suite but the amount of benchies it contains is a bit overwhelming. If anyone here has experience with it (or other FOSS solutions) I'd welcome some examples of well respected and easy to perform benchmarks that might fit the scenario.

Grab the latest Phoronix Test Suite release and then just do:

```
phoronix-test-suite benchmark favorites
```

or 

```
phoronix-test-suite benchmark linux-system
```

are two suites that are quick and easy and good to get you started.

---

### Post by Rich_B_uk on 2009-04-16
Thanks phoronix. I presume those two are predefined profiles/suites (I forget the terminology). 

I'll give them a bash later tonight. If I swap out "benchmark" with "list" it should show me what tests each is actually running?

---

### Post by phoronix on 2009-04-16
> **Rich_B_uk said:**
> Thanks phoronix. I presume those two are predefined profiles/suites (I forget the terminology). 

I'll give them a bash later tonight. If I swap out "benchmark" with "list" it should show me what tests each is actually running?

Those two are two (of the 36 or so) suites. Suites consist of tests with predefined settings.

To see what is contained within a suite, run:

phoronix-test-suite info <name of suite or test>

to see all tests:

phoronix-test-suite list-tests


to see all suites:

phoronix-test-suite list-suites

---

### Post by Rich_B_uk on 2009-04-16
You're a king amongst men Sir (or miss)!

Good work on the SW as well. ;)

---

### Post by phoronix on 2009-04-16
> **Rich_B_uk said:**
> Good work on the SW as well. ;)

Thanks.

Let me know if you have any other questions or problems.

-- Michael

---

### Post by Rich_B_uk on 2009-04-17
Having a bit of trouble installing some packages. To my untrained eye it looks like some of the suite links are broken, or maybe the apps have been updated and so sigs don't mate?

```
Downloading File: gnupg-1.4.9.tar.gz

--2009-04-17 17:08:06--  ftp://ftp.gnupg.org/gcrypt/gnupg/gnupg-1.4.9.tar.gz
           => `gnupg-1.4.9.tar.gz.temp'
Resolving ftp.gnupg.org... 217.69.76.55
Connecting to ftp.gnupg.org|217.69.76.55|:21... connected.
Logging in as anonymous ... Logged in!
==> SYST ... done.    ==> PWD ... done.
==> TYPE I ... done.  ==> CWD /gcrypt/gnupg ... done.
==> SIZE gnupg-1.4.9.tar.gz ... 4664291
==> PASV ... couldn't connect to 217.69.76.55 port 41650: Connection refused

The MD5 check-sum of the downloaded file is incorrect.
Would you like to try downloading the file again (Y/n)? 

```

---

### Post by Rich_B_uk on 2009-04-17
Just as a sidenote, the openSSL test from the cryptography suite went on fine, it's just gnupg posing a problem. I'll post if I come across any more of them.

Problematic:
build-php
gnupg

Working:
build-apache
openssl
compress-lzma
stresscpu2

---

### Post by sdennie on 2009-04-17
I agree that the phronix test suite is your best bet.  As Michael pointed out, they are only daunting until you understand them.  There are various subsystems that can be tested in understandable and meaning full ways via the "suites".

---

### Post by Rich_B_uk on 2009-07-28
Cheers all. I wrote up what I was doing [HERE]("http://up-stream.co.uk/2009/05/adventures-in-benchmarking-part-1-principles/"). There are a few sections but that takes you from the start.

If you want it all here is a [PDF]("http://up-stream.co.uk/mirror/research/benchmarking_gift_of_inefficiency_v3.pdf").

---

