---
title: "clamdscan -- skipping network mounts, and unnecessary directories"
date: 2009-02-09
forum: General Help
---

### Post by mohnkern on 2009-02-09
Hello.  I'm currently running clamdscan on a machine that has several network mounts on it.  I'd like to do a scan that skips these, plus skips the other directories that it doesn't need to scan (/proc, /dev and /mnt)

Is there an expression I can use to in the --exclude-dirs= directive to list all of them on one, or do I need to do multiple --exclude-dirs?


Thanks for the help.

---

### Post by LowSky on 2009-02-09
You machine really doesnt nee antivirus, but the easier thing to do is tell it what directorites to scan, then telling it which one not to.

Dont have it scan Root, instead just scan the /home, /usr folders, and if you need a certain disk then point directly to it

---

### Post by mohnkern on 2009-02-09
Yeah, agreed, don't really need antivirus, but office is requiring scans (yes, its a bit strange).

I think I've figured out how to do it with clamscan.  Problem is, we have mount points we want to skip that are beneath points like home.  It's an odd configuration, which is why we wanted to go the exclusion route.

---

