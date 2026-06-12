---
title: "Mince Exception in thread &quot;main&quot; java.lang.Error"
date: 2019-10-20
forum: Gaming &amp; Leisure
---

### Post by hazard-droid on 2019-10-20
Hi, so I was trying to run Minecraft on my distro and I ran into this error, I have openjdk-8-jre installed still I get this error when I try java -jar minecraft.jar in the terminal.

[BootstrapStarter] Current dir: /mnt/Yasir Rehman/Downloads/Games/MineCraft/.
Exception in thread "main" java.lang.Error: tlauncher.bootstrap.classpath is not defined
    at ru.turikhay.tlauncher.bootstrap.launcher.ProcessStarter.getSystemClasspath(ProcessStarter.java:98)
    at ru.turikhay.tlauncher.bootstrap.BootstrapStarter.start(BootstrapStarter.java:37)
    at ru.turikhay.tlauncher.bootstrap.BootstrapStarter.main(BootstrapStarter.java:19)



**Sorry for the typo in the title. :lolflag:**

---

### Post by hazard-droid on 2019-10-20
Okay I got it working I just uninstalled java and reinstalled with jdk and it worked sudo apt install openjdk-8-jdk openjdk-8-jre

---

### Post by zimbuf on 2019-10-20
Hmm, interesting. If it couldn't find the bootstrap classloader, my thought is that the openjdk-8-jre package must not be properly packaged.

Java programs (and thereby Minecraft plugins) usually explicitly call the bootstrap classloader in order to reflexively read items from the resource folder in the jar. There's no reason you should have needed the jdk package. My best guess is that the jre package is missing some binaries from $JAVA_HOME/bin

But I'm glad you got it working! What version/distro were you running on?

---

