---
title: "Java error"
date: 2013-04-06
forum: Desktop Environments
---

### Post by alfirdaous on 2013-04-06
Good morning,

I am trying to run an application from my command line, and it's given this error:

```


Start the PC Monitor Manager (requires Graphical Interface)? [Y/n]y No protocol specified No protocol specified Exception in thread "main" java.lang.InternalError: Can't connect to X11 window server using ':50.0' as the value of the DISPLAY variable.     at sun.awt.X11GraphicsEnvironment.initDisplay(Native Method)     at sun.awt.X11GraphicsEnvironment.access$200(X11GraphicsEnvironment.java:65)     at sun.awt.X11GraphicsEnvironment$1.run(X11GraphicsEnvironment.java:110)     at java.security.AccessController.doPrivileged(Native Method)     at sun.awt.X11GraphicsEnvironment.<clinit>(X11GraphicsEnvironment.java:74)     at java.lang.Class.forName0(Native Method)     at java.lang.Class.forName(Class.java:188)     at java.awt.GraphicsEnvironment.createGE(GraphicsEnvironment.java:102)     at java.awt.GraphicsEnvironment.getLocalGraphicsEnvironment(GraphicsEnvironment.java:81)     at sun.awt.X11.XToolkit.<clinit>(XToolkit.java:119)     at java.lang.Class.forName0(Native Method)     at java.lang.Class.forName(Class.java:188)     at java.awt.Toolkit$2.run(Toolkit.java:870)     at java.security.AccessController.doPrivileged(Native Method)     at java.awt.Toolkit.getDefaultToolkit(Toolkit.java:862)     at java.awt.KeyboardFocusManager.initPeer(KeyboardFocusManager.java:459)     at java.awt.KeyboardFocusManager.<init>(KeyboardFocusManager.java:455)     at java.awt.DefaultKeyboardFocusManager.<init>(DefaultKeyboardFocusManager.java:64)     at java.awt.KeyboardFocusManager.getCurrentKeyboardFocusManager(KeyboardFocusManager.java:225)     at java.awt.KeyboardFocusManager.getCurrentKeyboardFocusManager(KeyboardFocusManager.java:216)     at javax.swing.plaf.synth.SynthLookAndFeel.initialize(SynthLookAndFeel.java:616)     at javax.swing.plaf.nimbus.NimbusLookAndFeel.initialize(NimbusLookAndFeel.java:105)     at javax.swing.UIManager.setLookAndFeel(UIManager.java:535)     at javax.swing.UIManager.setLookAndFeel(UIManager.java:580)     at com.mobilepcmonitor.linux.config.ui.Q.a(Unknown Source)     at com.mobilepcmonitor.linux.config.ui.App.main(Unknown Source)

```

Which java should I install to avoid this error and run the application

using Ubuntu desktop 12.04

Thx in advance

---

### Post by Cheesemill on 2013-04-06
What application are you trying to run?
Which command are you using to try and run the application?
What version of Java do you have installed? Can you post the output of...
```
java -version
```

---

### Post by alfirdaous on 2013-04-06
[this one]("http://www.mobilepcmonitor.com/downloads")

I am using this ./install run

```

# java -version
java version "1.7.0_15"
OpenJDK Runtime Environment (IcedTea7 2.3.7) (7u15-2.3.7-0ubuntu1~12.04.1)
OpenJDK 64-Bit Server VM (build 23.7-b01, mixed mode)

```

---

