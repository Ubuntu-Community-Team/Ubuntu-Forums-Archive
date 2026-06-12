---
title: "Broken java app (SAPGUI) after switch from Gnome3 to Unity"
date: 2012-07-19
forum: Desktop Environments
---

### Post by Lazra on 2012-07-19
Hello,

Until lately, I was working under gnome3 on my Ubuntu 12.04 64 bits. I had all my tools installed there and working correctly, especially SAPGUI 7.20rev5 (for connection to SAP Systems), which is based on java.

Recently, I felt that I had under-tested Unity and decided to give it a try for a few weeks. Mostly everything was OK as Unity was still installed, so i only had to select Unity at logon screen.

However, under Unity, SAPGUI does not work. As it is an essential tool for my work, I tried to come back to gnome3, but the application is not working there anymore too, giving me the same java error.

The error is some java NullPointerException (see below)
Does anyone have any idea why switching desktop caused this issue ? (I don't see any other event that could be the root cause: no new program installed, no java update, no configuration modification ...)

The error displayed when I launch SAPGUI from console:
```

Exception in thread "AWT-EventQueue-0" java.lang.NullPointerException
    at sun.awt.X11.XToolkit.getScreenInsets(Unknown Source)
    at com.sap.platin.base.config.Defaults.calcDefaultValue(Defaults.java:185)
    at com.sap.platin.base.config.Defaults.getDefaultValue(Defaults.java:88)
    at com.sap.platin.base.config.SettingsTable.put(SettingsTable.java:127)
    at com.sap.platin.base.util.AbstractPersistentHashMap.readData(AbstractPersistentHashMap.java:809)
    at com.sap.platin.base.util.AbstractPersistentHashMap.init(AbstractPersistentHashMap.java:217)
    at com.sap.platin.base.util.AbstractPersistentHashMap.init(AbstractPersistentHashMap.java:201)
    at com.sap.platin.base.config.SettingsTable.<init>(SettingsTable.java:33)
    at com.sap.platin.base.config.GuiConfiguration.readSettingsTable(GuiConfiguration.java:769)
    at com.sap.platin.base.config.GuiConfiguration.readTables(GuiConfiguration.java:634)
    at com.sap.platin.base.config.GuiConfiguration.init(GuiConfiguration.java:540)
    at com.sap.platin.base.config.GuiConfiguration.<init>(GuiConfiguration.java:92)
    at com.sap.platin.base.config.GuiConfiguration.getCurrent(GuiConfiguration.java:106)
    at com.sap.platin.base.config.GuiConfiguration.getTable(GuiConfiguration.java:227)
    at com.sap.platin.base.config.GuiConfiguration.getStringValue(GuiConfiguration.java:388)
    at com.sap.platin.base.config.GuiConfiguration.getStringValue(GuiConfiguration.java:383)
    at com.sap.platin.base.config.GuiConfiguration.getStringValue(GuiConfiguration.java:375)
    at com.sap.platin.base.plaf.DesignLookAndFeel.getCurrentDesign(DesignLookAndFeel.java:1065)
    at com.sap.platin.base.plaf.DesignLookAndFeel.getDefaults(DesignLookAndFeel.java:150)
    at javax.swing.UIManager.setLookAndFeel(Unknown Source)
    at com.sap.platin.base.logon.GuiImpl$1.run(GuiImpl.java:101)
    at java.awt.event.InvocationEvent.dispatch(Unknown Source)
    at java.awt.EventQueue.dispatchEventImpl(Unknown Source)
    at java.awt.EventQueue.access$000(Unknown Source)
    at java.awt.EventQueue$3.run(Unknown Source)
    at java.awt.EventQueue$3.run(Unknown Source)
    at java.security.AccessController.doPrivileged(Native Method)
    at java.security.ProtectionDomain$1.doIntersectionPrivilege(Unknown Source)
    at java.awt.EventQueue.dispatchEvent(Unknown Source)
    at com.sap.platin.micro.event.GuiEventQueue.dispatchEvent(GuiEventQueue.java:79)
    at java.awt.EventDispatchThread.pumpOneEventForFilters(Unknown Source)
    at java.awt.EventDispatchThread.pumpEventsForFilter(Unknown Source)
    at java.awt.EventDispatchThread.pumpEventsForHierarchy(Unknown Source)
    at java.awt.EventDispatchThread.pumpEvents(Unknown Source)
    at java.awt.EventDispatchThread.pumpEvents(Unknown Source)
    at java.awt.EventDispatchThread.run(Unknown Source)
Exception in thread "AWT-EventQueue-0" java.lang.NullPointerException
    at sun.awt.X11.XToolkit.getScreenInsets(Unknown Source)
    at com.sap.platin.base.config.Defaults.calcDefaultValue(Defaults.java:185)
    at com.sap.platin.base.config.Defaults.getDefaultValue(Defaults.java:88)
    at com.sap.platin.base.config.GuiConfiguration.getIntValue(GuiConfiguration.java:431)
    at com.sap.platin.base.config.GuiConfiguration.getIntValue(GuiConfiguration.java:425)
    at com.sap.platin.base.logon.GuiLogon.getLogonFrame(GuiLogon.java:1310)
    at com.sap.platin.base.logon.GuiLogonManager.getLogonFrame(GuiLogonManager.java:50)
    at com.sap.platin.base.logon.GuiLogonManager.setVisibleLogonFrame(GuiLogonManager.java:62)
    at com.sap.platin.base.logon.GuiImpl$2.run(GuiImpl.java:157)
    at java.awt.event.InvocationEvent.dispatch(Unknown Source)
    at java.awt.EventQueue.dispatchEventImpl(Unknown Source)
    at java.awt.EventQueue.access$000(Unknown Source)
    at java.awt.EventQueue$3.run(Unknown Source)
    at java.awt.EventQueue$3.run(Unknown Source)
    at java.security.AccessController.doPrivileged(Native Method)
    at java.security.ProtectionDomain$1.doIntersectionPrivilege(Unknown Source)
    at java.awt.EventQueue.dispatchEvent(Unknown Source)
    at com.sap.platin.micro.event.GuiEventQueue.dispatchEvent(GuiEventQueue.java:79)
    at java.awt.EventDispatchThread.pumpOneEventForFilters(Unknown Source)
    at java.awt.EventDispatchThread.pumpEventsForFilter(Unknown Source)
    at java.awt.EventDispatchThread.pumpEventsForHierarchy(Unknown Source)
    at java.awt.EventDispatchThread.pumpEvents(Unknown Source)
    at java.awt.EventDispatchThread.pumpEvents(Unknown Source)
    at java.awt.EventDispatchThread.run(Unknown Source)

```Checkscript output:
```
/opt/SAPClients/SAPGUI/bin$ ./guilogon -checkscript
guilogon -checkscript output:
Before processing:
  PLATINHOME      = 
  PLATIN_JAVA     = 
  uname           = Linux
  PATH            = /home/adrien/bin:/usr/lib/lightdm/lightdm:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
After processing:
  THISSCRIPTPATH  = /opt/SAPClients/SAPGUI7.20rev5/bin/guilogon
  PLATINHOME      = /opt/SAPClients/SAPGUI7.20rev5
  PLATIN_JAVA     = java
  PLATIN_DEBUG    = 
  JRE_ARGS        = -Xms32M -Xmx256M
  START_JARS      = /opt/SAPClients/SAPGUI7.20rev5/jar/GuiStartS.jar
  STARTCLASS      = com.sap.platin.Gui
  RFC_TRACE       = 
Command to start:
  java -Xms32M -Xmx256M -cp /opt/SAPClients/SAPGUI7.20rev5/jar/GuiStartS.jar com.sap.platin.Gui  

```Thanks in advance for your help !

---

### Post by Lazra on 2012-07-26
Follow-up update:

I tried to install it on a fresh Ubuntu 12.04 64bits VM with Unity (in a virtual machine), and it runs without any issue: install openjdk-6-jre and use the .jar file provided by SAP and that's it.

I then tried to remove/re-install openjdk-6-jre on my main machine, and re-install SAPGUI, and I still have the same error when I try to use it.

As a workaround for now I can use the install in the VM, but it's not very convenient ...

---

### Post by Lazra on 2012-08-07
Solved !

I downloaded oracle's java 6 binaries from oracle's website ( [http://java.com/en/download/manual_v6.jsp](http://java.com/en/download/manual_v6.jsp) - Linux x64 .bin file) and deployed it in /opt/jre1.6.0_33 . Then I set the environment variable PLATIN_JAVA to /opt/jre1.6.0_33/bin/java and SAPGUI launch normally, without error.

I don't know why it's working with openjdk-6 in my test VM and not on my physical machine though.

I don't know how to mark the post as solved.

---

