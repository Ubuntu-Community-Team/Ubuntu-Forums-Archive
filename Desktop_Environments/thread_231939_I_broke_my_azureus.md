---
title: "I broke my azureus"
date: 2006-08-08
forum: Desktop Environments
---

### Post by raven65az on 2006-08-08
Upon initial installation, I had Azureus working just dandy.  However after some further installations and updates, it is not working properly:( 
When I launch it, I get the splash screen, and the gui, but then it closes in a second!
I have uninstalled and reinstalled, but no joy.
Here is my shell output.

Configuring environment...
Loading Azureus:
java -Xms16m -Xmx128m -cp "/home/raven/downloads/azureus/Azureus2.jar:/home/raven/downloads/azureus/swt.jar" -Djava.library.path="/home/raven/downloads/azureus" -Dazureus.install.path="/home/raven/downloads/azureus" org.gudy.azureus2.ui.swt.Main ''
Exception in thread "main" org.eclipse.swt.SWTError: No more handles [gtk_init_check() failed]
        at org.eclipse.swt.SWT.error(SWT.java:2968)
        at org.eclipse.swt.widgets.Display.createDisplay(Display.java:757)
        at org.eclipse.swt.widgets.Display.create(Display.java:746)
        at org.eclipse.swt.graphics.Device.<init>(Device.java:141)
        at org.eclipse.swt.widgets.Display.<init>(Display.java:429)
        at org.eclipse.swt.widgets.Display.<init>(Display.java:420)
        at org.gudy.azureus2.ui.swt.mainwindow.SWTThread.<init>(SWTThread.java:77)
        at org.gudy.azureus2.ui.swt.mainwindow.SWTThread.createInstance(SWTThread.java:58)
        at org.gudy.azureus2.ui.swt.mainwindow.Initializer.<init>(Initializer.java:108)
        at org.gudy.azureus2.ui.swt.Main.<init>(Main.java:147)
        at org.gudy.azureus2.ui.swt.Main.main(Main.java:162)
Azureus TERMINATED.

Any ideas would be greatly appreciated.
Scott (Raven)

---

### Post by raven65az on 2006-08-08
Fixed the issue with an alternate installation mentioned elsewhere in the forum.
Thanks anyway!
Scott

---

