---
title: "Java webstart launcher: Permission denied"
date: 2010-08-03
forum: Desktop Environments
---

### Post by bodypilot on 2010-08-03
Hello all,

I'm running BT747 ([www.bt747.org]("http://www.bt747.org")), a gps data logger software.
It's a Java application.

I can start it using the Java Webstart options ([http://www.bt747.org/webinstall](http://www.bt747.org/webinstall)), I can start it by downloading any of the webstart files (specifically [this one]("http://soft.bt747.org/BT747_J2SE_Latest_AutoUpdate.jnlp")) to my desktop (or home folder) and double-clicking it but I can not start it from a launcher in my menu because I'll then get a "Failed to execute childproces /home/username/BT747_J2SE_Latest_AutoUpdate.jnlp’. Permission denied." warning.

What's going on?

Regards.

PS. Using Ubuntu 9.10

---

### Post by bodypilot on 2010-08-05
Well,

that was easier than I first thought.
The starter should be:
javaws /home/username/BT747_J2SE_Latest_AutoUpdate.jnlp
in stead of:
/home/username/BT747_J2SE_Latest_AutoUpdate.jnlp

Problem solved.

---

