---
title: "how do I find out if my dvb card is supported"
date: 2006-08-25
forum: Desktop Environments
---

### Post by spottyrover on 2006-08-25
I am trying to get my dntv live pro card to work in ubuntu 6.06 using the 2.6.15-26-386 kernel.

1)what do I need to do to check that the kernel has the driver I need.
2)how do I load it


I tried this 

install dvb-util
mkdir /home/david/.tzap
scan /usr/share/doc/dvb-utils/examples/scan/dvb-t/au-Adelaide >/home/david/.tzap/channels.conf
and got this error

using '/dev/dvb/adapter0/frontend0' and '/dev/dvb/adapter0/demux0'
main:1884: FATAL: failed to open '/dev/dvb/adapter0/frontend0': 2 No such file or directory



with kanotix it all just worked with kernell 2.6.17 so I do not know what I need to do

thanks for your help
dave

---

