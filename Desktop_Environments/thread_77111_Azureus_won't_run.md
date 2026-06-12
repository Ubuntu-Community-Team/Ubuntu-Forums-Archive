---
title: "Azureus won't run"
date: 2005-10-16
forum: Desktop Environments
---

### Post by Jaivaz on 2005-10-16
When I run Azureus the screen is literally blank. I used "[HOW-TO: Building your own Java 1.5 package](http://ubuntuforums.org/showthread.php?t=76735&highlight=fakeroot)" and "[ HOWTO: Installing Azureus on Breezy](http://ubuntuforums.org/showthread.php?t=75272&highlight=azureus)" and when I run Azureus I get this odd [error](http://www.jaivaz.x10hosting.com/Screenshot.png).

---

### Post by yage on 2005-10-16
Could you try starting azureus from a Terminal and paste the output here?

---

### Post by Jaivaz on 2005-10-16
```
horace@Gorgoth:~$ azureus
changeLocale: no message properties for Locale 'English (United States)' (en_US), using 'English (default)'
DEBUG::Sun Oct 16 09:16:19 CDT 2005::com.aelitis.azureus.core.diskmanager.cache.impl.CacheFileManagerImpl::<init>::119:
  Invalid cache size parameter (-34603008), caching disabled
    NativeConstructorAccessorImpl::newInstance0::-2,NativeConstructorAccessorImpl::newInstance::-1,DelegatingConstructorAccessorImpl::newInstance::-1,Constructor::newInstance::-1,Class::newInstance0::-1,Class::newInstance::-1,CacheFileManagerFactory::getSingleton::75,CacheFileManagerFactory::getSingleton::46,DiskManagerFileInfoImpl::<init>::80,DiskManagerImpl::filesExist::501,DiskManagerImpl::filesExist::402,DownloadManagerImpl::filesExistErrorMessage::762,DownloadManagerImpl::filesExist::752,DownloadManagerImpl::setOnlySeeding::725,DownloadManagerImpl::readTorrent::626,DownloadManagerImpl::<init>::305,DownloadManagerFactory::create::64,GlobalManagerImpl::loadDownloads::1163,GlobalManagerImpl::<init>::265,GlobalManagerFactory::create::39,AzureusCoreImpl::start::160,Initializer::run::270,SWTThread$1::runSupport::107,AERunnable::run::38,Thread::run::-1
**** DHT: Anti-spoof currently disabled for old clients ****
DEBUG::Sun Oct 16 09:16:25 CDT 2005
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
        at org.eclipse.swt.internal.gtk.OS._gtk_widget_show(Native Method)
        at org.eclipse.swt.internal.gtk.OS.gtk_widget_show(OS.java:7262)
        at org.eclipse.swt.widgets.Shell.setVisible(Shell.java:1382)
        at org.eclipse.swt.widgets.Shell.open(Shell.java:948)
        at org.gudy.azureus2.ui.swt.mainwindow.MainWindow.openMainWindow(MainWindow.java:729)
        at org.gudy.azureus2.ui.swt.mainwindow.MainWindow.access$1000(MainWindow.java:59)
        at org.gudy.azureus2.ui.swt.mainwindow.MainWindow$20.runSupport(MainWindow.java:1491)
        at org.gudy.azureus2.core3.util.AERunnable.run(AERunnable.java:38)
        at org.eclipse.swt.widgets.RunnableLock.run(RunnableLock.java:35)
        at org.eclipse.swt.widgets.Synchronizer.runAsyncMessages(Synchronizer.java:123)
        at org.eclipse.swt.widgets.Display.runAsyncMessages(Display.java:2844)
        at org.eclipse.swt.widgets.Display.readAndDispatch(Display.java:2575)
        at org.gudy.azureus2.ui.swt.mainwindow.SWTThread.<init>(SWTThread.java:114)
        at org.gudy.azureus2.ui.swt.mainwindow.SWTThread.createInstance(SWTThread.java:58)
        at org.gudy.azureus2.ui.swt.mainwindow.Initializer.<init>(Initializer.java:107)
        at org.gudy.azureus2.ui.swt.Main.<init>(Main.java:71)
        at org.gudy.azureus2.ui.swt.Main.main(Main.java:98)

DEBUG::Sun Oct 16 09:16:26 CDT 2005
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

---

### Post by taurus on 2005-10-16
Try download azureus by hand, [http://azureus.sourceforge.net/download.php](http://azureus.sourceforge.net/download.php), unpack it, and run it from that directory, and see what happens...  It works perfectly fine for me.

---

### Post by yage on 2005-10-16
Azureus is not using a suitable java version. As you can see from your output its using the eclipse version... In a Terminal try:```
java -version
``` It should print out ```
java version "1.5.0_05"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_05-b05)
Java HotSpot(TM) Client VM (build 1.5.0_05-b05, mixed mode, sharing)

```
If it's showing another version try reinstalling it... 
If this does'nt fix it check that you have your PATH set corectly

Btw. my output from running Azureus from at Terminal:
```
Starting Azureus...
Java exec found in PATH. Verifying...
Suitable java version found [java = 1.5.0_05]
Configuring environment...
Loading Azureus:
java -Xms16m -Xmx128m -cp "/opt/azureus/Azureus2.jar:/opt/azureus/swt.jar:/opt/azureus/swt-mozilla.jar:/opt/azureus/swt-pi.jar" -Djava.library.path="/opt/azureus" -Dazureus.install.path="/opt/azureus" org.gudy.azureus2.ui.swt.Main ''
**** DHT: Anti-spoof currently disabled for old clients ****
```

---

### Post by Joey French on 2005-10-16
Man, I was just about to post this, but I found this thread. I guess I should load it up by hand. It takes a few tries to start, I've installed it and reinstalled it via apt and for some reason, I noticed this on another thread, when you resize the window, the app doesn't resize with it?

---

### Post by yage on 2005-10-16
[QUOTE=Joey French]Man, I was just about to post this, but I found this thread. I guess I should load it up by hand. It takes a few tries to start, I've installed it and reinstalled it via apt and for some reason, I noticed this on another thread, when you resize the window, the app doesn't resize with it?[/QUOTE]
That sound more like a graphics problem to me... what kind of hardware do you have? I did run azureus with the default nv driver of xorg an hade kind of the same problem. With the Nvidia driver installed it's smooth

---

### Post by Jaivaz on 2005-10-16
Thanks, I got it to work now. I just ran **sudo update-alternatives --config java**, chose to use ** /usr/local/jre1.5.0_05/bin/java** and fixed the Java PATH in the azureus file to **/usr/local/jre1.5.0_05/bin/** and fixed my launcher to open **./azureus/azureus**. Thanks for your help.

---

### Post by yjsoon on 2005-10-19
[QUOTE=yage]That sound more like a graphics problem to me... what kind of hardware do you have? I did run azureus with the default nv driver of xorg an hade kind of the same problem. With the Nvidia driver installed it's smooth[/QUOTE]

Actually, I'm facing the same problem as Joey French, wrt the resizing problem. It's "stuck" at a certain resolution no matter how I resize the window -- when I resize the window to be larger, the extra space is all white (scrollbars are still where they were originally). Graphics refresh also seems slower, somehow.

I'm running Breezy with the Nvidia driver (not nv).

---

### Post by docomo on 2005-10-19
I had this problem and the only thing I had to do was run 

sudo update-alternatives --config java 

...as Jaivaz wrote above.

---

### Post by Joey French on 2005-10-27
Fixed my Azureus with a hand install from the Azureus home page. It works great, I think the one in Breezy repo is buggy. I would suggest installing by hand to all who are having this problem.

---

