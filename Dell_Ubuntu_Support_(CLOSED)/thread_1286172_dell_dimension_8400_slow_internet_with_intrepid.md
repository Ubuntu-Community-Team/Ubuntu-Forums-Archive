---
title: "dell dimension 8400 slow internet with intrepid"
date: 2009-10-08
forum: Dell Ubuntu Support (CLOSED)
---

### Post by jmk123 on 2009-10-08
i have an old webserver at my company whose connectivity has been running dog slow for the last few months.  when i do an apt-get update or install, i am getting ~100B/s if at all.  i have tried different servers and it does not improve.  firefox and other browsers are very very slow to load webpages and same with wget.  server hosts wordpress and mysql, and sql queries are also very slow.

top doesn't see any processes that are out of control.  
memory usage seems to be fine (about 2gigs intalled as i recall)
rebooting does nothing.
local intranet connectivity is also effected.  

it was not always like this and may have started when i upgraded to intrepid though i can't say for certain.  most everything else seems to be working fine except inet activity. 
any troubleshooting tips you would recommend?  

thanks!

---

### Post by jmk123 on 2009-10-09
tried disabling ipv6 and no luck. (of course i may have done that incorrectly)
tried resetting mtu size: sudo ifconfig eth0 mtu 1500
that also failed.
will keep banging on this and will post results.  perhaps this can help someone!

---

### Post by jmk123 on 2009-10-15
tried upgrading to 9.04 from disc (remember to download the alternate iso!!) that also failed.  finally put in a new NIC and that did the trick.  apparently the original card was DOA but showing small signs of life every now and again.

---

