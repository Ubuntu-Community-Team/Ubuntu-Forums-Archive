---
title: "Matlab activation problem"
date: 2009-10-29
forum: Education &amp; Science
---

### Post by hmuralid on 2009-10-29
Hello,

I installed Matlab using WINE. After the installation, when the activation window popped up, since I had the activation license I clicked the manual option and to give the path of the license file, when I pressed browse an error message "There was an unexpected exception.See the log file." popped up. Also I tried typing the path myself. But it shows "Access Denied" for any path. Here's the log file below. Please help me!!

(Oct 28, 2009 22:47:49)MATHWORKS ACTIVATION IS EXITING WITH A STATUS OF 0 
(Oct 28, 2009 22:48:30)MATHWORKS ACTIVATION IS STARTING UP. 
(Oct 28, 2009 22:48:40)3184 
sun.awt.shell.Win32ShellFolder2.getFileChooserIcon(Unknown Source) 
sun.awt.shell.Win32ShellFolderManager2.get(Unknown Source) 
sun.awt.shell.ShellFolder.get(Unknown Source) 
com.sun.java.swing.plaf.windows.WindowsLookAndFeel$LazyWindowsIcon.createValue(Unknown Source) 
javax.swing.UIDefaults.getFromHashtable(Unknown Source) 
javax.swing.UIDefaults.get(Unknown Source) 
javax.swing.MultiUIDefaults.get(Unknown Source) 
javax.swing.UIDefaults.getIcon(Unknown Source) 
javax.swing.UIManager.getIcon(Unknown Source) 
javax.swing.plaf.basic.BasicFileChooserUI.installIcons(Unknown Source) 
javax.swing.plaf.basic.BasicFileChooserUI.installDefaults(Unknown Source) 
javax.swing.plaf.basic.BasicFileChooserUI.installUI(Unknown Source) 
com.sun.java.swing.plaf.windows.WindowsFileChooserUI.installUI(Unknown Source) 
javax.swing.JComponent.setUI(Unknown Source) 
javax.swing.JFileChooser.updateUI(Unknown Source) 
javax.swing.JFileChooser.setup(Unknown Source) 
javax.swing.JFileChooser.<init>(Unknown Source) 
javax.swing.JFileChooser.<init>(Unknown Source) 
com.mathworks.instwiz.WILicenseFileChooser.<init>(WILicenseFileChooser.java:20) 
com.mathworks.activationclient.view.options.ActivationOptionsPanelImpl$6.actionPerformed(ActivationOptionsPanelImpl.java:88) 
javax.swing.AbstractButton.fireActionPerformed(Unknown Source) 
javax.swing.AbstractButton$Handler.actionPerformed(Unknown Source) 
javax.swing.DefaultButtonModel.fireActionPerformed(Unknown Source) 
javax.swing.DefaultButtonModel.setPressed(Unknown Source) 
javax.swing.plaf.basic.BasicButtonListener.mouseReleased(Unknown Source) 
java.awt.Component.processMouseEvent(Unknown Source) 
javax.swing.JComponent.processMouseEvent(Unknown Source) 
java.awt.Component.processEvent(Unknown Source) 
java.awt.Container.processEvent(Unknown Source) 
java.awt.Component.dispatchEventImpl(Unknown Source) 
java.awt.Container.dispatchEventImpl(Unknown Source) 
java.awt.Component.dispatchEvent(Unknown Source) 
java.awt.LightweightDispatcher.retargetMouseEvent(Unknown Source) 
java.awt.LightweightDispatcher.processMouseEvent(Unknown Source) 
java.awt.LightweightDispatcher.dispatchEvent(Unknown Source) 
java.awt.Container.dispatchEventImpl(Unknown Source) 
java.awt.Window.dispatchEventImpl(Unknown Source) 
java.awt.Component.dispatchEvent(Unknown Source) 
java.awt.EventQueue.dispatchEvent(Unknown Source) 
java.awt.EventDispatchThread.pumpOneEventForFilters(Unknown Source) 
java.awt.EventDispatchThread.pumpEventsForFilter(Unknown Source) 
java.awt.EventDispatchThread.pumpEventsForHierarchy(Unknown Source) 
java.awt.EventDispatchThread.pumpEvents(Unknown Source) 
java.awt.EventDispatchThread.pumpEvents(Unknown Source) 
java.awt.EventDispatchThread.run(Unknown Source)

---

### Post by XCan on 2009-10-29
Can't you use the linux version? Although Matlab's fairly highly rated in [http://appdb.winehq.org/objectManager.php?sClass=application&iId=49](http://appdb.winehq.org/objectManager.php?sClass=application&iId=49) I can't see the big idea of running it through Wine.

---

### Post by hmuralid on 2009-10-29
@XCAN : I'll have to buy the linux version and it'll cost $99 for the student version, which I cant afford!!

@Wich : I have the license file but I'm unable to activate because it gives an error which I mentioned before.

---

### Post by samden on 2009-10-29
Have you tried putting the licence file within ~/.wine/drive_c and referring to it using Windows syntax (e.g. C:\licence.txt)? Or have you been trying to reference it somewhere else in your system using Linux syntax (e.g. ~/licence.txt)? 

Perhaps Matlab when running within Wine cannot see anything outside the fake C drive, and won't recognise Linux file references.

---

### Post by hmuralid on 2009-10-29
@Samden: I tried it. It tells me that path doesnt exist. As for the "browse" tab, same exception error.

---

### Post by Amix on 2009-11-03
I think **Freemat** do all what can matlab do,!

---

