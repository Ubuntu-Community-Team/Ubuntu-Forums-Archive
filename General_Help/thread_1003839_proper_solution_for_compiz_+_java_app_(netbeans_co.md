---
title: "proper solution for compiz + java app (netbeans concretely)"
date: 2008-12-06
forum: General Help
---

### Post by marc sturlese on 2008-12-06
Hey there,
Is there a good solution to have java apps like netbeans (I am using 5.5.1 version) with compiz???

Writing in /etc/environment this:
AWT_TOOLKIT="MToolkit"
Blocks the keyboard (in the small boxes like the "search" one)

I have this problem since ages ago and never could find a good fix.
I am using intrepid ibex and carring the problem since dapper...

---

### Post by jamesstansell on 2008-12-07
> **marc sturlese said:**
> Hey there,
Is there a good solution to have java apps like netbeans (I am using 5.5.1 version) with compiz???

Writing in /etc/environment this:
AWT_TOOLKIT="MToolkit"
Blocks the keyboard (in the small boxes like the "search" one)

I have this problem since ages ago and never could find a good fix.
I am using intrepid ibex and carring the problem since dapper...

MToolkit is for Motif so I don't expect you would want to use that.

I thought the compiz problem was fixed by now; I don't use compiz myself and I haven't upgrade to ubuntu 8.10 yet either.  But I thought the sun-java6-* and/or the openjdk6 packages fixed the compiz problems by now.

Which JDK are you using?  If you want to try the recently released 6u11 you should be able to download the packages from the jaunty repository and use dpkg -i to install them on intrepid.  Let me look up that link.

[http://packages.ubuntu.com/jaunty/sun-java6-jdk](http://packages.ubuntu.com/jaunty/sun-java6-jdk)
[https://launchpad.net/ubuntu/jaunty/i386/sun-java6-jdk/6-11-0ubuntu1](https://launchpad.net/ubuntu/jaunty/i386/sun-java6-jdk/6-11-0ubuntu1)

Use whichever link above you like best to download the -jdk package and it's dependencies like -jre and -bin.  I used this method to install them on my 8.04 box and they seem to be working just fine.

There are fancier methods (maybe apt pinning?) that might let you download all the packages with a single command, but this method is effective and isn't too difficult.

---

