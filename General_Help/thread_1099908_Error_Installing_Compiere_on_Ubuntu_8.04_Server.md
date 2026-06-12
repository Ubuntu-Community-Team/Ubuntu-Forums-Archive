---
title: "Error Installing Compiere on Ubuntu 8.04 Server"
date: 2009-03-18
forum: General Help
---

### Post by officerswift on 2009-03-18
Hey guys,

I'm trying to install Compiere on my Ubuntu 8.04 LS, but I keep running into problems and can't seem to find an answer. If I run the setup script, I get the following output:

root@ubuntu-server:/Compiere2# ./RUN_setup.sh
Install Compiere Server
===================================
Setup Dialog
===================================
*** 2009-03-18 16:12:16.363 Compiere Log (CLogConsole) ***
16:12:16.362   CLogMgt.setLevel: CONFIG
Exception in thread "main" java.lang.NoClassDefFoundError: Could not initialize class sun.awt.X11GraphicsEnvironment
        at java.lang.Class.forName0(Native Method)
        at java.lang.Class.forName(Class.java:169)
        at java.awt.GraphicsEnvironment.getLocalGraphicsEnvironment(GraphicsEnvironment.java:68)
        at sun.awt.X11.XToolkit.<clinit>(XToolkit.java:89)
        at java.lang.Class.forName0(Native Method)
        at java.lang.Class.forName(Class.java:169)
        at java.awt.Toolkit$2.run(Toolkit.java:836)
        at java.security.AccessController.doPrivileged(Native Method)
        at java.awt.Toolkit.getDefaultToolkit(Toolkit.java:828)
        at sun.swing.SwingUtilities2$AATextInfo.getAATextInfo(SwingUtilities2.java:120)
        at javax.swing.plaf.metal.MetalLookAndFeel.initComponentDefaults(MetalLookAndFeel.java:1556)
        at javax.swing.plaf.basic.BasicLookAndFeel.getDefaults(BasicLookAndFeel.java:130)
        at javax.swing.plaf.metal.MetalLookAndFeel.getDefaults(MetalLookAndFeel.java:1591)
        at javax.swing.UIManager.setLookAndFeel(UIManager.java:537)
        at javax.swing.UIManager.setLookAndFeel(UIManager.java:577)
        at javax.swing.UIManager.initializeDefaultLAF(UIManager.java:1331)
        at javax.swing.UIManager.initialize(UIManager.java:1418)
        at javax.swing.UIManager.maybeInitialize(UIManager.java:1406)
        at javax.swing.UIManager.getInstalledLookAndFeels(UIManager.java:421)
        at javax.swing.UIManager.installLookAndFeel(UIManager.java:460)
        at javax.swing.UIManager.installLookAndFeel(UIManager.java:479)
        at org.compiere.plaf.CompierePLAF.<clinit>(CompierePLAF.java:307)
        at org.compiere.install.Setup.main(Setup.java:253)

*** 2009-03-18 16:12:16.634 Compiere Log (CLogConsole) ***
===================================
Make .sh executable
===================================
./RUN_setup.sh: line 44: utils/RUN_UnixEnv.sh: No such file or directory

At first I was getting an error that my DISPLAY variable was not set, but I manually set it to: export DISPLAY=0.0

Any thoughts on a solution to this error?

---

### Post by taurus on 2009-03-18
Is there a RUN_UnixEnv.sh in utils directory?

```
ls -la utils
```
Assuming you are still in /Compiere2 when you ran that command.

---

### Post by officerswift on 2009-03-23
No, but there is a RUN_UnixEnvTemplate.sh file.

If I run it, I get 

root@ubuntu-server:/Compiere2/utils# ./RUN_UnixEnvTemplate.sh
Set Unix Environment
===================================
Setup Client Environment
===================================
Please add COMPIERE_HOME and JAVA_HOME to your environment
You chould also have set LD_LIBRARY_PATH


but both variables are already set

root@ubuntu-server:/Compiere2/utils# echo $JAVA_HOME
/usr/lib/jvm/java-6-sun-1.6.0.07

root@ubuntu-server:/Compiere2/utils# echo $COMPIERE_HOME
/Compiere2


thoughts?

---

