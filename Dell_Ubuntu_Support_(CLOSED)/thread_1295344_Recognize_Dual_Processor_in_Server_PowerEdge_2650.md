---
title: "Recognize Dual Processor in Server PowerEdge 2650"
date: 2009-10-19
forum: Dell Ubuntu Support (CLOSED)
---

### Post by bianggio22 on 2009-10-19
Hi actually i've installed ubuntu 9.04 in DELL PowerEdge 2650 Intel Xeon Dual Core of 3.06 Ghz, now whe i executed the commando top i can see only one CPU. I've executed these commands too but i not sure if Ubuntu recognized really the Dual Core processors:
 
_[COLOR=#0000ff]root@server:~# grep cores /proc/cpuinfo[/COLOR]_
_[COLOR=#0000ff]cpu cores : 1[/COLOR]_
_[COLOR=#0000ff]cpu cores : 1[/COLOR]_
_[COLOR=#0000ff]cpu cores : 1[/COLOR]_
_[COLOR=#0000ff]cpu cores : 1[/COLOR]_
_[COLOR=#0000ff]root@server:~# grep "core id" /proc/cpuinfo[/COLOR]_
_[COLOR=#0000ff]core id : 0[/COLOR]_
_[COLOR=#0000ff]core id : 0[/COLOR]_
_[COLOR=#0000ff]core id : 0[/COLOR]_
_[COLOR=#0000ff]core id : 0[/COLOR]_
_[COLOR=#0000ff]root@server:~# grep -i core /proc/cpuinfo[/COLOR]_
_[COLOR=#0000ff]core id : 0[/COLOR]_
_[COLOR=#0000ff]cpu cores : 1[/COLOR]_
_[COLOR=#0000ff]core id : 0[/COLOR]_
_[COLOR=#0000ff]cpu cores : 1[/COLOR]_
_[COLOR=#0000ff]core id : 0[/COLOR]_
_[COLOR=#0000ff]cpu cores : 1[/COLOR]_
_[COLOR=#0000ff]core id : 0[/COLOR]_
_[COLOR=#0000ff]cpu cores : 1[/COLOR]_
 
 
 
Thanks a lot for you Help

---

### Post by bianggio22 on 2009-10-19
My kernel is Linux server 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:57:59 UTC 2009 i686 GNU/Linux

---

### Post by trundlenut on 2009-10-22
I have installed 8.04 server on my PE2800 (2x2.8ghz Xeons) and that recognises 4 cores OK.

---

### Post by urugTON on 2009-10-24
Would you start top at the command line?  When it is running enter a "1" (no quotes of course).  Tell us how many cpus are reported after entering the "1".  Copy and paste the screen if you can.

---

