---
title: "Random computer hangs - I suspect when java apps are running"
date: 2010-03-23
forum: Desktop Environments
---

### Post by hise0001 on 2010-03-23
I have a java based banking program that at the most inopportune time decides to lock up and require me to reboot.

It doesn't seem to happen when other programs are running so I'm testing the theory that it's related to sun-java6.

to configure the bank program I have to create a symbolic link to the jre directory.  I'm using sun-java6, so the link is pointing to "/usr/lib/jvm/java-6-sun/jre"

where should I direct this symbolic link to use openjdk-6-jre which is also installed.

Thanks

---

### Post by hise0001 on 2010-03-28
Not sure if this should be considered solved...

I never found the path to which I should set the symbolic link; however, I read in another thread where someone mentioned that there are conflicts when sun-java and openjdk are installed together.

I uninstalled openjdk and haven't experienced any hangs.  I need to give it a few more days.

---

