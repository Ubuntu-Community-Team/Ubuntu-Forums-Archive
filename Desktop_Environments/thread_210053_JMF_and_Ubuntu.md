---
title: "JMF and Ubuntu"
date: 2006-07-06
forum: Desktop Environments
---

### Post by jitesh on 2006-07-06
Can anyone tell me if the Java Media Framework is supported on Ubuntu. All my attempts to install it so far has failed.

---

### Post by tiato on 2008-01-25
I did not find a response to this Q on various threads.

Following the Sun recommended installation instructions for the Linux Performance Pack. I had the same trouble as most when using the Diagnostics Applet:

[http://java.sun.com/products/java-media/jmf/2.1.1/jmfdiagnostics.html](http://java.sun.com/products/java-media/jmf/2.1.1/jmfdiagnostics.html)

Classes Not Found

Native Libraries Not Found

After hours of google I found the following thread which helped me finalize the installation and receive a successful diagnostics:

[http://forum.java.sun.com/thread.jspa?threadID=741521&messageID=4255204](http://forum.java.sun.com/thread.jspa?threadID=741521&messageID=4255204)

I really hope this helps. 

I am running:
Ubuntu 7.10 Gutsy Gibbons
JDK 1.6.0
JMF-2.1.1e

I had to install JMF to use with ArtOfIllusion in order to be able to output to a Quicktime format. AOI is working without a hitch.

---

