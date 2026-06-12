---
title: "Azureus Problem."
date: 2005-10-19
forum: Desktop Environments
---

### Post by Syphin on 2005-10-19
Yep, another azureus thread. ><

Anyways, ive seen threads with a similer problem, but i just cant seem to get mine fixed.

Whenever i start azureus for the first time after a freash install the screen comes up blank, and a 'gudy' error shows in the small azureus popup.  So i close the app, and restart it.  It works, the error doesnt come up, and everything shows like its supposed to.

But when i resize the window, the actual contents of the window doesnt move with the resize like it should. (Screenshot attached)
Heres what i get from the terminal when i run it that way:

When it is first opened:
```

changeLocale: no message properties for Locale 'English (United States)' (en_US), using 'English (default)'
**** DHT: Anti-spoof currently disabled for old clients ****
com.aelitis.azureus.plugins.jpc.JPCException: cache connection connect failure
        at com.aelitis.azureus.plugins.jpc.cache.impl.JPCCacheImpl.connect(JPCCacheImpl.java:107)
        at com.aelitis.azureus.plugins.jpc.cache.impl.JPCCacheManagerImpl$1$1.cacheDiscovered(JPCCacheManagerImpl.java:85)
        at com.aelitis.azureus.plugins.jpc.discovery.impl.JPCDiscoveryImpl.setCacheAddress(JPCDiscoveryImpl.java:282)
        at com.aelitis.azureus.plugins.jpc.discovery.impl.JPCDiscoveryImpl.discoverCache(JPCDiscoveryImpl.java:195)
        at com.aelitis.azureus.plugins.jpc.discovery.impl.JPCDiscoveryImpl.<init>(JPCDiscoveryImpl.java:86)
        at com.aelitis.azureus.plugins.jpc.discovery.JPCDiscoveryFactory.create(JPCDiscoveryFactory.java:44)
        at com.aelitis.azureus.plugins.jpc.cache.impl.JPCCacheManagerImpl$1.run(JPCCacheManagerImpl.java:63)
        at org.gudy.azureus2.pluginsimpl.local.utils.UtilitiesImpl$2.runSupport(UtilitiesImpl.java:214)
        at org.gudy.azureus2.core3.util.AEThread.run(AEThread.java:54)
Caused by: java.net.ConnectException: Connection refused
        at sun.nio.ch.SocketChannelImpl.checkConnect(Native Method)
        at sun.nio.ch.SocketChannelImpl.finishConnect(Unknown Source)
        at com.aelitis.azureus.core.networkmanager.impl.ConnectDisconnectManager.finishConnect(ConnectDisconnectManager.java:235)
        at com.aelitis.azureus.core.networkmanager.impl.ConnectDisconnectManager.access$700(ConnectDisconnectManager.java:42)
        at com.aelitis.azureus.core.networkmanager.impl.ConnectDisconnectManager$3.selectSuccess(ConnectDisconnectManager.java:173)
        at com.aelitis.azureus.core.networkmanager.impl.VirtualChannelSelectorImpl.select(VirtualChannelSelectorImpl.java:412)
        at com.aelitis.azureus.core.networkmanager.VirtualChannelSelector.select(VirtualChannelSelector.java:240)
        at com.aelitis.azureus.core.networkmanager.impl.ConnectDisconnectManager.runSelect(ConnectDisconnectManager.java:348)
        at com.aelitis.azureus.core.networkmanager.impl.ConnectDisconnectManager.mainLoop(ConnectDisconnectManager.java:95)
        at com.aelitis.azureus.core.networkmanager.impl.ConnectDisconnectManager.access$100(ConnectDisconnectManager.java:42)
        at com.aelitis.azureus.core.networkmanager.impl.ConnectDisconnectManager$2.runSupport(ConnectDisconnectManager.java:84)
        ... 1 more
```

When I try to resize the window:
```

DEBUG::Wed Oct 19 19:07:41 CDT 2005
  java.lang.ClassCastException: org.eclipse.swt.layout.GridData
        at org.eclipse.swt.layout.FillLayout.computeChildSize(FillLayout.java:141)
        at org.eclipse.swt.layout.FillLayout.computeSize(FillLayout.java:119)
        at org.eclipse.swt.widgets.Composite.computeSize(Composite.java:192)
        at org.eclipse.swt.custom.SashFormLayout.computeSize(SashFormLayout.java:39)
        at org.eclipse.swt.widgets.Composite.computeSize(Composite.java:192)
        at org.eclipse.swt.custom.CTabFolderLayout.computeSize(CTabFolderLayout.java:53)
        at org.eclipse.swt.widgets.Composite.computeSize(Composite.java:192)
        at org.eclipse.swt.layout.FormData.computeSize(FormData.java:127)
        at org.eclipse.swt.layout.FormLayout.layout(FormLayout.java:318)
        at org.eclipse.swt.layout.FormLayout.layout(FormLayout.java:284)
        at org.eclipse.swt.widgets.Composite.updateLayout(Composite.java:1133)
        at org.eclipse.swt.widgets.Shell.resizeBounds(Shell.java:1071)
        at org.eclipse.swt.widgets.Shell.gtk_size_allocate(Shell.java:876)
        at org.eclipse.swt.widgets.Widget.windowProc(Widget.java:1375)
        at org.eclipse.swt.widgets.Display.windowProc(Display.java:3442)
        at org.eclipse.swt.internal.gtk.OS._g_main_context_iteration(Native Method)
        at org.eclipse.swt.internal.gtk.OS.g_main_context_iteration(OS.java:1158)
        at org.eclipse.swt.widgets.Display.readAndDispatch(Display.java:2570)
        at org.gudy.azureus2.ui.swt.mainwindow.SWTThread.<init>(SWTThread.java:114)
        at org.gudy.azureus2.ui.swt.mainwindow.SWTThread.createInstance(SWTThread.java:58)
        at org.gudy.azureus2.ui.swt.mainwindow.Initializer.<init>(Initializer.java:107)
        at org.gudy.azureus2.ui.swt.Main.<init>(Main.java:71)
        at org.gudy.azureus2.ui.swt.Main.main(Main.java:98)
```

Now i have the my nvidia driver installed and setup correctly, as well as Sun-Java 1.5jre.

```

syphin@MainPC:~$ sudo update-alternatives --config java

There are 3 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
      1        /usr/bin/gij-wrapper-4.0
 +    2        /usr/lib/jvm/java-gcj/bin/java
*     3        /usr/lib/j2re1.5-sun/bin/java

Press enter to keep the default[*], or type selection number: 3
Using `/usr/lib/j2re1.5-sun/bin/java' to provide `java'.
syphin@MainPC:~$ java -version
java version "1.5.0_05"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_05-b05)
Java HotSpot(TM) Client VM (build 1.5.0_05-b05, mixed mode, sharing)
```

Any help would be appreceated :)

---

### Post by yjsoon on 2005-10-20
I'm facing the same resizing problem with Azureus and Sun's Java 1.5 package. The window does resize if you leave it at the desired new size and restart Azureus, at least.

---

### Post by pinoyskull on 2005-10-20
i have the same resizing problem with azureus and sun's java 1.5, but other than that, it works fine :)

---

### Post by Syphin on 2005-10-21
Ive tried it with with the diff java versions also..  they all seem to have it happen for me.

But when i downloaded the source from the azureus site, and ran it that way, it seemed to work like it should. (atleast i think, not at home right now to re-check).
But ya, other then that, it works fine, just alittle annoying. :p

---

### Post by shenki on 2005-10-21
I also see this, running the latest nvidia drivers (1.0-7676), compositing (xcompmgr -n), with sun's latest java

shenki@miranda:~$ java -version
java version "1.5.0_05"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_05-b05)

One way to get around the problem, is to close all of the tabs in Azureus, resize, and then open back up the ones you want.

---

