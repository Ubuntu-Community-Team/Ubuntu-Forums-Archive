---
title: "Intel HD graphic configuration"
date: 2011-09-16
forum: Dell Ubuntu Support (CLOSED)
---

### Post by florianopolitan on 2011-09-16
Greetings

I have a dell inspiron model N4050 and need help on configuring my video driver intel HD graphic HM57, which seems to be disabled or something, so I can't experience maximum visual effects with my laptop. I'm using an ubuntu 10.10.

Thanks.

---

### Post by realzippy on 2011-09-16
Welcome!
Guess you need a newer kernel,maybe intel driver also...
please post output from
```
lspci | grep VGA
```
and
```
uname -a
```

---

### Post by Zinou87 on 2012-03-18
Hello, I have exactly the same problem
Hardware: Dell Inspiron N4050
Software: UBUNTU 10.10
and here is the output from the codes 
First
```
00:02.0 VGA compatible controller: Intel Corporation Sandy Bridge Integrated Graphics Controller (rev 09)
```
and 
```
Linux zinou-Inspiron-N4050 2.6.35-27-generic-pae #48-Ubuntu SMP Tue Feb 22 21:46:58 UTC 2011 i686 GNU/Linux
```

---

### Post by see4what on 2012-03-27
> **realzippy said:**
> Welcome!
Guess you need a newer kernel,maybe intel driver also...
please post output from
```
lspci | grep VGA
```and
```
uname -a
```

Hi I am a naive to Ubuntu and facing the same problem in Ubuntu 11.10
The output for the specified code is as follow:

00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
And

Linux fazal-Inspiron-N4050 3.0.0-17-generic #30-Ubuntu SMP Thu Mar 8 17:34:21 UTC 2012 i686 i686 i386 GNU/Linux

Please solve the issue. Thanks in anticipation :)

---

