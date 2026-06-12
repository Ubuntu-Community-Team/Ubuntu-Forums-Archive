---
title: "How do I properly only use Sun Java?"
date: 2009-04-12
forum: General Help
---

### Post by paradigm2 on 2009-04-12
Right now the system uses OpenJDK as well as another java library.  I would like to use only sun java 6 because all the java applications I use work best with it.

I know that I can install the package and also manually add a symbolic link in /etc/alternatives/java but is this truly the proper way to do that?  Is there a cleaner way?

---

### Post by soltanis on 2009-04-12
Verify that this package is installed:

sun-java6-jre

And remove the openjdk-6-jre, default-jre, default-jdk if the are installed. Remove gcj if it is installed.

You might need to reinstall the sun-java6-jre package.

---

### Post by paradigm2 on 2009-04-12
> **soltanis said:**
> Verify that this package is installed:

sun-java6-jre

And remove the openjdk-6-jre, default-jre, default-jdk if the are installed. Remove gcj if it is installed.

You might need to reinstall the sun-java6-jre package.

On my non-production system I did that, except I left gcj in (My gut feeling tells me not to remove that package).  I noticed that even after removing openjdk-6 an entry was still left in update-binfmts.  I had to manually remove the entry for jar after doing a complete removal of openjdk, then I had to reboot and install sun java.  Then it still went to gcj, so I needed to remove the old symbolic link in /etc/alternatives/java and manually link it to the proper sun jre.

The whole thing was very messy and I figured there must be a better way.

I notice a bug has been filed regarding update-binfmts and as has been observed by myself, this happens with both sun java and openjdk.  Neither seem to do a proper cleanup:

[https://lists.ubuntu.com/archives/universe-bugs/2009-February/050028.html](https://lists.ubuntu.com/archives/universe-bugs/2009-February/050028.html)
[Bug 328174] [NEW] Uninstalling sun-java6-* does not remove the binfmts-entry for "jar"

Does anyone see a better way to handle this.  I am also partially worried that by doing this on my non-production system I might have broke something.  At this point the entry for jar in update-binfmts seems correct,as is the symbolic link I manually added in /etc/alternatives.  Does anyone see any potential issues with this manual workaround I did?  Or again a better way to do it on my production system?

---

### Post by kostkon on 2009-04-12
Just open a terminal and give the following command
```
sudo update-java-alternatives -s java-6-sun
```
and Sun Java will become the default Java in your system. Also, Firefox will use the Sun Java plugin.

---

### Post by txcrackers on 2009-04-12
And you can quite safely remove gcj.

---

### Post by paradigm2 on 2009-04-12
> **kostkon said:**
> Just open a terminal and give the following command
```
sudo update-java-alternatives -s java-6-sun
```
and Sun Java will become the default Java in your system. Also, Firefox will use the Sun Java plugin.

Perfect.  I knew there had to be an easier way. Thank you.

---

