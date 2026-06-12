---
title: "My minecraft wont work..."
date: 2011-09-05
forum: Gaming &amp; Leisure
---

### Post by Theyellowk123 on 2011-09-05
i cant get Minecraft to work, it used to work but then it started giving me this message...

java.io.IOException: Cannot run program "javaw": java.io.IOException: error=2, No such file or directory
    at java.lang.ProcessBuilder.start(ProcessBuilder.java:475)
    at net.minecraft.MinecraftLauncher.main(MinecraftLauncher.java:31)
Caused by: java.io.IOException: java.io.IOException: error=2, No such file or directory
    at java.lang.UNIXProcess.<init>(UNIXProcess.java:164)
    at java.lang.ProcessImpl.start(ProcessImpl.java:81)
    at java.lang.ProcessBuilder.start(ProcessBuilder.java:468)
    ... 1 more
Exception in thread "main" java.awt.HeadlessException
    at java.awt.GraphicsEnvironment.checkHeadless(GraphicsEnvironment.java:173)
    at java.awt.Window.<init>(Window.java:476)
    at java.awt.Frame.<init>(Frame.java:419)
    at net.minecraft.LauncherFrame.<init>(LauncherFrame.java:27)
    at net.minecraft.LauncherFrame.main(LauncherFrame.java:158)
    at net.minecraft.MinecraftLauncher.main(MinecraftLauncher.java:36)

](*,)

---

### Post by jfed on 2011-09-05
It seems like something happened and....now you don't have java. Just check quick here to be sure:

[http://java.com/en/download/installed.jsp?jre_version=1.6.0_24&vendor=Sun+Microsystems+Inc.&os=Linux&os_version=2.6.35-22-generic](http://java.com/en/download/installed.jsp?jre_version=1.6.0_24&vendor=Sun+Microsystems+Inc.&os=Linux&os_version=2.6.35-22-generic)

That will tell you if you have it, if you don't, and if there is a newer version available. Just check to see if you have it first.

---

### Post by Theyellowk123 on 2011-09-05
k i got it to launch but now it crashes and gives me this message...




      Minecraft has crashed!      
      ----------------------      

Minecraft has stopped running because it encountered a problem.

If you wish to report this, please copy this entire text and email it to [email]support@mojang.com[/email].
Please include a description of what you did when the error occured.



--- BEGIN ERROR REPORT a1dce528 --------
Generated 9/5/11 3:01 PM

Minecraft: Minecraft Beta 1.7.3
OS: Linux (i386) version 2.6.38-11-generic
Java: 1.6.0_22, Sun Microsystems Inc.
VM: OpenJDK Server VM (mixed mode), Sun Microsystems Inc.
LWJGL: 2.4.2
[failed to get system properties (java.lang.NullPointerException)]

java.lang.IllegalStateException: Only one LWJGL context may be instantiated at any one time.
	at org.lwjgl.opengl.Display.create(Display.java:846)
	at org.lwjgl.opengl.Display.create(Display.java:784)
	at org.lwjgl.opengl.Display.create(Display.java:765)
	at net.minecraft.client.Minecraft.a(SourceFile:294)
	at net.minecraft.client.Minecraft.run(SourceFile:716)
	at java.lang.Thread.run(Thread.java:679)
--- END ERROR REPORT 5fb274f ----------

---

