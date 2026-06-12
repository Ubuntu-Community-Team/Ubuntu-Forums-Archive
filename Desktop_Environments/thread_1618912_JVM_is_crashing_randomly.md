---
title: "JVM is crashing randomly"
date: 2010-11-11
forum: Desktop Environments
---

### Post by elapouya on 2010-11-11
Hello,

Since I installed Ubuntu 10.04 on my PC, I have eclipse crashing every hour or more without apparent action.
In the logs, I see that the cause is related to JAVA :

```
#
# A fatal error has been detected by the Java Runtime Environment:
#
#  SIGSEGV (0xb) at pc=0x00007f95f32ce9c0, pid=2382, tid=140280562099984
#
# JRE version: 6.0_18-b18
# Java VM: OpenJDK 64-Bit Server VM (16.0-b13 mixed mode linux-amd64 )
# Derivative: IcedTea6 1.8.2
# Distribution: Ubuntu 10.04.1 LTS, package 6b18-1.8.2-4ubuntu2
# Problematic frame:
# V  [libjvm.so+0x5309c0]
#
# An error report file with more information is saved as:
# /home/elapouya/perso/projects/django/rsame/hs_err_pid2382.log
#
# If you would like to submit a bug report, please include
# instructions how to reproduce the bug and visit:
#   [https://bugs.launchpad.net/ubuntu/+source/openjdk-6/](https://bugs.launchpad.net/ubuntu/+source/openjdk-6/)
#
```

[www.eclipse.org](http://www.eclipse.org) knows this bug and it is RECOMMENDED to use 1.6.0.10 or more, or go jdk 1.5
I installed the latest JVM official but still crashes. I 6.0_18-b18 (I do not know if this is 1.6.0.10 ...)
So I installed an older version: 1.5.0_19, but I still have random crashes:

```
#
# An unexpected error has been detected by HotSpot Virtual Machine:
#
#  SIGSEGV (0xb) at pc=0x00007fc833c91dfe, pid=8630, tid=140496587896592
#
# Java VM: Java HotSpot(TM) 64-Bit Server VM (1.5.0_19-b02 mixed mode)
# Problematic frame:
# V  [libjvm.so+0x5b1dfe]
#
# An error report file with more information is saved as hs_err_pid8630.log
#
# If you would like to submit a bug report, please visit:
#   [http://java.sun.com/webapps/bugreport/crash.jsp](http://java.sun.com/webapps/bugreport/crash.jsp)
#
```

I did an apt-get upgrade to be up-to-date, but it continues to crash:

What do you recommend?

---

