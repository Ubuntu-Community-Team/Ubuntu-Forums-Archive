---
title: "OpenJDK or Sun Java"
date: 2011-02-02
forum: Desktop Environments
---

### Post by HappyLinux on 2011-02-02
OK, I'm a little confused and would like some clarification.

You typically have Sun Java Runtime Environment, the current being Version 6 Update 23. However, Ubuntu 10.10 comes with something called OpenJDK.

After it took me a long time to finally get Sun Java Runtime Environment Version 6 Update 21 installed (cannot install the newest version for some odd reason), I find out that OpenJDK does the same stuff.

Is there any difference between the two?
Do I remove one or the other? Or keep them both?

---

### Post by lykeion on 2011-02-02
For the end-user there is no difference, and technically the difference is very small, ~99% of their code is shared. For a Java developer OpenJDK will give you new features faster, whereas Sun JDK should give you more stability. I'd say that the main difference is that OpenJDK is open source and Sun Java is licenced.

You can have both installed and use *update-java-alternatives* command to switch between them. 

And I shouldn't worry about getting the latest u23 version of Sun Java, this is what Oracle (who own Sun Java now) say themselves on the [release notes]("http://www.oracle.com/technetwork/java/javase/6u23releasenotes-191058.html"):
> Java SE 6u23 does not contain any additional fixes for security vulnerabilities to its previous release, Java SE 6u22. Users who have Java SE 6u22 have the latest security fixes and do not need to upgrade to this release to be current on security fixes.
The current version of Sun Java in the Ubuntu Partner repository is 6u22. I don't know how you got 6u21 installed.

---

### Post by gradinaruvasile on 2011-02-02
99% ? I had problems running Sip Communicator, Mucommander and other smaller  java apps on OpenJdk (almost all of them). Many dont even start.

---

### Post by lykeion on 2011-02-02
@gradinaruvasile
Tried running both programs you mentioned (muCommander, SIP Communicator) using OpenJDK without any problems.

---

### Post by HappyLinux on 2011-02-02
> **lykeion said:**
> For the end-user there is no difference, and technically the difference is very small, ~99% of their code is shared. For a Java developer OpenJDK will give you new features faster, whereas Sun JDK should give you more stability. I'd say that the main difference is that OpenJDK is open source and Sun Java is licenced.

You can have both installed and use *update-java-alternatives* command to switch between them. 

And I shouldn't worry about getting the latest u23 version of Sun Java, this is what Oracle (who own Sun Java now) say themselves on the [release notes]("http://www.oracle.com/technetwork/java/javase/6u23releasenotes-191058.html"):

The current version of Sun Java in the Ubuntu Partner repository is 6u22. I don't know how you got 6u21 installed.

I had to manually insert a repository for it. Not sure whether it's the correct one, but it's the only one I could find after an hours googling. You'll find the source list I have in the attached screen shot.

---

### Post by lykeion on 2011-02-02
If you enable Canonical Partners repository (top one in your attached image) you'll get Sun Java 6u22. You can disable the Sun Java Community Team PPA after that.

---

### Post by HappyLinux on 2011-02-03
OK, thanks.

---

