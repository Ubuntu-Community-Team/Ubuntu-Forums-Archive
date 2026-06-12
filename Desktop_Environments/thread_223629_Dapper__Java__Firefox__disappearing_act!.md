---
title: "Dapper / Java / Firefox / disappearing act!"
date: 2006-07-26
forum: Desktop Environments
---

### Post by ddales on 2006-07-26
Ok, I'm having a problem with java apps within firefox.  It seems that every time firefox tries to open a java applet, firefox crashes and just disappears.  No error message.  No nothing.  It just closes!

#java -version
java version "1.5.0_06"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_06-b05)
Java HotSpot(TM) Client VM (build 1.5.0_06-b05, mixed mode, sharing)

#firefox -version
Mozilla Firefox 1.5.0.4, Copyright (c) 1998 - 2006 mozilla.org

# uname -a
Linux DDA 2.6.15-26-386 #1 PREEMPT Mon Jul 17 19:52:53 UTC 2006 i686 GNU/Linux

Nothing in any of my /var/log files to indicate what the problem might be!

---

### Post by ddales on 2006-07-26
Cool, I finally got an error message that I could capture.  I started mozilla from command line.  Went to the page that was giving me grief  ([http://www.eventim.com](http://www.eventim.com) and click on a sallplan (seating arrangement). 

Here is the output from the error message:

# An unexpected error has been detected by HotSpot Virtual Machine:
#
#  SIGSEGV (0xb) at pc=0xb19d1b02, pid=6982, tid=2969926576
#
# Java VM: Java HotSpot(TM) Client VM (1.5.0_06-b05 mixed mode, sharing)
# Problematic frame:
# C  [libfontmanager.so+0x34b02]
#
# An error report file with more information is saved as /tmp/hs_err_pid6982.log
#
# If you would like to submit a bug report, please visit:
#   [http://java.sun.com/webapps/bugreport/crash.jsp](http://java.sun.com/webapps/bugreport/crash.jsp)
#
INTERNAL ERROR on Browser End: Plugin instance index out of bounds -14657

System error?:: Success

---

### Post by ddales on 2006-07-26
I used Synaptic to remove the Sun-Java 1.5 packages.

I then used Synaptic to find and install the Java 1.4 packages.

All is now well with Firefox and Java

---

