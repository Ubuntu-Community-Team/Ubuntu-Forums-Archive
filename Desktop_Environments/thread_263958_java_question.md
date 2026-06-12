---
title: "java question"
date: 2006-09-23
forum: Desktop Environments
---

### Post by DarkDancer on 2006-09-23
I have this program that is done in Java. I am not sure how to start it. The .jar is ted.jar, what is the command?

---

### Post by T_W on 2006-09-24
Try 

```
java -jar ted.jar
```

Note, this will only work if the app is packaged as an executable jar file.

---

### Post by DarkDancer on 2006-09-24
Thanks, that command returns this:

> Exception in thread "main" java.lang.UnsatisfiedLinkError: no tray in java.library.path
        at java.lang.ClassLoader.loadLibrary(ClassLoader.java:1682)
        at java.lang.Runtime.loadLibrary0(Runtime.java:822)
        at java.lang.System.loadLibrary(System.java:992)
        at org.jdesktop.jdic.tray.internal.impl.GnomeTrayAppletService.<clinit>(Unknown Source)
        at org.jdesktop.jdic.tray.internal.impl.ServiceManagerStub.getService(Unknown Source)
        at org.jdesktop.jdic.tray.internal.ServiceManager.getService(Unknown Source)
        at org.jdesktop.jdic.tray.TrayIcon.<init>(Unknown Source)
        at org.jdesktop.jdic.tray.TrayIcon.<init>(Unknown Source)
        at ted.TedMainDialog.initGUI(TedMainDialog.java:143)
        at ted.TedMainDialog.<init>(TedMainDialog.java:127)
        at ted.TedMain.main(TedMain.java:40)


---

### Post by DarkDancer on 2006-09-24
Any help? Any at all?

---

### Post by DarkDancer on 2006-09-24
Ok, found out what the problem is, I think, the program tries to put an icon in the syustray which doesn't work with all forms of linux, they plan to put in a command line in the next version of it so that you can tell it not too, but since the messages were dated march 12th, I hold out little hope on that.

---

