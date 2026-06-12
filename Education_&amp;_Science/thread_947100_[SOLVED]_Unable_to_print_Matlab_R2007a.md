---
title: "[SOLVED] Unable to print Matlab R2007a"
date: 2008-10-14
forum: Education &amp; Science
---

### Post by QED314159 on 2008-10-14
When trying to print in Matlab I get the following:
 
```

Exception in thread "AWT-EventQueue-0" java.lang.NullPointerException: null attribute
	at sun.print.IPPPrintService.isAttributeValueSupported(IPPPrintService.java:1147)
	at sun.print.ServiceDialog$OrientationPanel.updateInfo(ServiceDialog.java:2121)
	at sun.print.ServiceDialog$PageSetupPanel.updateInfo(ServiceDialog.java:1263)
	at sun.print.ServiceDialog.updatePanels(ServiceDialog.java:437)
	at sun.print.ServiceDialog.initPrintDialog(ServiceDialog.java:195)
	at sun.print.ServiceDialog.<init>(ServiceDialog.java:124)
	at javax.print.ServiceUI.printDialog(ServiceUI.java:188)
	at com.mathworks.widgets.text.print.PrintSettings.showPrintDialog(PrintSettings.java:665)
	at com.mathworks.mde.cmdwin.XCmdWndView.print(XCmdWndView.java:1623)
	at com.mathworks.mde.cmdwin.CmdWinEditorKit$PrintAction.actionPerformed(CmdWinEditorKit.java:1348)
	at javax.swing.AbstractButton.fireActionPerformed(AbstractButton.java:1995)
	at javax.swing.AbstractButton$Handler.actionPerformed(AbstractButton.java:2318)
	at javax.swing.DefaultButtonModel.fireActionPerformed(DefaultButtonModel.java:387)
	at javax.swing.DefaultButtonModel.setPressed(DefaultButtonModel.java:242)
	at javax.swing.AbstractButton.doClick(AbstractButton.java:357)
	at com.mathworks.mwswing.plaf.MBasicMenuItemUI.doClick(MBasicMenuItemUI.java:1145)
	at com.mathworks.mwswing.plaf.MBasicMenuItemUI$MouseInputHandler.mouseReleased(MBasicMenuItemUI.java:973)
	at java.awt.Component.processMouseEvent(Component.java:6041)
	at javax.swing.JComponent.processMouseEvent(JComponent.java:3265)
	at java.awt.Component.processEvent(Component.java:5806)
	at java.awt.Container.processEvent(Container.java:2058)
	at java.awt.Component.dispatchEventImpl(Component.java:4413)
	at java.awt.Container.dispatchEventImpl(Container.java:2116)
	at java.awt.Component.dispatchEvent(Component.java:4243)
	at java.awt.LightweightDispatcher.retargetMouseEvent(Container.java:4322)
	at java.awt.LightweightDispatcher.processMouseEvent(Container.java:3986)
	at java.awt.LightweightDispatcher.dispatchEvent(Container.java:3916)
	at java.awt.Container.dispatchEventImpl(Container.java:2102)
	at java.awt.Component.dispatchEvent(Component.java:4243)
	at java.awt.EventQueue.dispatchEvent(EventQueue.java:599)
	at java.awt.EventDispatchThread.pumpOneEventForFilters(EventDispatchThread.java:273)
	at java.awt.EventDispatchThread.pumpEventsForFilter(EventDispatchThread.java:183)
	at java.awt.EventDispatchThread.pumpEventsForHierarchy(EventDispatchThread.java:173)
	at java.awt.EventDispatchThread.pumpEvents(EventDispatchThread.java:168)
	at java.awt.EventDispatchThread.pumpEvents(EventDispatchThread.java:160)
	at java.awt.EventDispatchThread.run(EventDispatchThread.java:121)

```

I previously had a locking assertion failure which was fixed by adding export MATLAB_JAVA=/usr/lib/jvm/java-6-sun/jre/ to $MATLABROOT/bin/matlab

Any help would be most appreciated.

Thanks.

---

### Post by hubie on 2008-10-17
I don't know if it worked out for that person, but check out the link I gave over in [this thread]("http://ubuntuforums.org/showthread.php?p=5567724#post5567724").

---

### Post by QED314159 on 2008-11-08
Thanks for the link, I put this off for so long that I decided to upgrade to 8.10 and the problem is now resolved.

---

