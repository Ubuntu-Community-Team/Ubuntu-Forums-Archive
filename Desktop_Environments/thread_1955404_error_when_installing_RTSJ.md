---
title: "error when installing RTSJ"
date: 2012-04-09
forum: Desktop Environments
---

### Post by forsubhi on 2012-04-09
I get this error after installing java rts 

```
[user@localhost Desktop]$ java -version
dl failure on line 824Error: failed /home/user/Documents/RealTime/JavaRTS-2.2-fcs-tmp/jrts-2.2_fcs/jre/lib/i386/client/libjvm.so, because libcap.so.1: cannot open shared object file: No such file or directory
```

I followed the instruction given by oracle

---

### Post by forsubhi on 2012-04-09
this day is wonderful day I found the solve again :lolflag:

If you encounter an error with libcap.so.1, please refer to the following hyper-links for a solution. 
[LIST]
[*][http://rtjava.blogspot.com/2010/11/real-time-java-helloworld.html](http://rtjava.blogspot.com/2010/11/real-time-java-helloworld.html)
[*][http://forums.oracle.com/forums/thread.jspa?threadID=1902543&tstart=30](http://forums.oracle.com/forums/thread.jspa?threadID=1902543&tstart=30)
[/LIST]

---

