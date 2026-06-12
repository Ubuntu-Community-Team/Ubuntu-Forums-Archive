---
title: "Eclipse 3.2.2 Pydev, nothing works (Jaunty)"
date: 2009-06-12
forum: General Help
---

### Post by Asday on 2009-06-12
I try to do pretty much anything, and I get a generic error message telling me to check the logs.  The same problem exists after "eclipse -clean" and also after "sudo apt-get purge eclipse; sudo apt-get install eclipse"

In the logs, I get something similar to this:

```
eclipse.buildId=M20070212-1330
java.fullversion=GNU libgcj 4.3.3
BootLoader constants: OS=linux, ARCH=x86, WS=gtk, NL=en_GB
Command-line arguments:  -os linux -ws gtk -arch x86

Error
Fri Jun 12 11:06:11 GMT+01:00 2009
Problems occurred when invoking code from plug-in: "org.eclipse.jface".

java.lang.NoSuchMethodError: method org.eclipse.swt.widgets.Tree.select with signature (Lorg.eclipse.swt.widgets.TreeItem;)V was not found.
at org.python.pydev.ui.pythonpathconf.AbstractInterpreterEditor.updateTree(AbstractInterpreterEditor.java:722)
at org.python.pydev.ui.pythonpathconf.AbstractInterpreterEditor.doLoad(AbstractInterpreterEditor.java:991)
at org.eclipse.jface.preference.FieldEditor.load(org.eclipse.jface_3.2.2.M20061214-1200.jar.so)
at org.eclipse.jface.preference.FieldEditorPreferencePage.initialize(org.eclipse.jface_3.2.2.M20061214-1200.jar.so)
at org.eclipse.jface.preference.FieldEditorPreferencePage.createContents(org.eclipse.jface_3.2.2.M20061214-1200.jar.so)
at org.eclipse.jface.preference.PreferencePage.createControl(org.eclipse.jface_3.2.2.M20061214-1200.jar.so)
at org.eclipse.jface.preference.PreferenceDialog.createPageControl(org.eclipse.jface_3.2.2.M20061214-1200.jar.so)
at org.eclipse.jface.preference.PreferenceDialog$12.run(org.eclipse.jface_3.2.2.M20061214-1200.jar.so)
at org.eclipse.core.runtime.SafeRunner.run(org.eclipse.equinox.common_3.2.0.v20060603.jar.so)
at org.eclipse.core.runtime.Platform.run(org.eclipse.core.runtime_3.2.0.v20060603.jar.so)
at org.eclipse.ui.internal.JFaceUtil$1.run(org.eclipse.ui.workbench_3.2.2.M20070119-0800.jar.so)
at org.eclipse.jface.util.SafeRunnable.run(org.eclipse.jface_3.2.2.M20061214-1200.jar.so)
at org.eclipse.jface.preference.PreferenceDialog.showPage(org.eclipse.jface_3.2.2.M20061214-1200.jar.so)
at org.eclipse.ui.internal.dialogs.FilteredPreferenceDialog.showPage(org.eclipse.ui.workbench_3.2.2.M20070119-0800.jar.so)
at org.eclipse.jface.preference.PreferenceDialog$8.selectionChanged(org.eclipse.jface_3.2.2.M20061214-1200.jar.so)
at org.eclipse.jface.viewers.StructuredViewer$3.run(org.eclipse.jface_3.2.2.M20061214-1200.jar.so)
at org.eclipse.core.runtime.SafeRunner.run(org.eclipse.equinox.common_3.2.0.v20060603.jar.so)
at org.eclipse.core.runtime.Platform.run(org.eclipse.core.runtime_3.2.0.v20060603.jar.so)
at org.eclipse.ui.internal.JFaceUtil$1.run(org.eclipse.ui.workbench_3.2.2.M20070119-0800.jar.so)
at org.eclipse.jface.util.SafeRunnable.run(org.eclipse.jface_3.2.2.M20061214-1200.jar.so)
at org.eclipse.jface.viewers.StructuredViewer.firePostSelectionChanged(org.eclipse.jface_3.2.2.M20061214-1200.jar.so)
at org.eclipse.jface.viewers.StructuredViewer.handlePostSelect(org.eclipse.jface_3.2.2.M20061214-1200.jar.so)
at org.eclipse.jface.viewers.StructuredViewer$5.widgetSelected(org.eclipse.jface_3.2.2.M20061214-1200.jar.so)
at org.eclipse.jface.util.OpenStrategy.firePostSelectionEvent(org.eclipse.jface_3.2.2.M20061214-1200.jar.so)
at org.eclipse.jface.util.OpenStrategy.access$4(org.eclipse.jface_3.2.2.M20061214-1200.jar.so)
at org.eclipse.jface.util.OpenStrategy$1$2.run(org.eclipse.jface_3.2.2.M20061214-1200.jar.so)
at org.eclipse.swt.widgets.RunnableLock.run(org.eclipse.swt.gtk.linux.x86_3.2.2.v3236.jar.so)
at org.eclipse.swt.widgets.Synchronizer.runAsyncMessages(org.eclipse.swt.gtk.linux.x86_3.2.2.v3236.jar.so)
at org.eclipse.swt.widgets.Display.runAsyncMessages(org.eclipse.swt.gtk.linux.x86_3.2.2.v3236.jar.so)
at org.eclipse.swt.widgets.Display.readAndDispatch(org.eclipse.swt.gtk.linux.x86_3.2.2.v3236.jar.so)
at org.eclipse.jface.window.Window.runEventLoop(org.eclipse.jface_3.2.2.M20061214-1200.jar.so)
at org.eclipse.jface.window.Window.open(org.eclipse.jface_3.2.2.M20061214-1200.jar.so)
at org.eclipse.ui.internal.OpenPreferencesAction.run(org.eclipse.ui.workbench_3.2.2.M20070119-0800.jar.so)
at org.eclipse.jface.action.Action.runWithEvent(org.eclipse.jface_3.2.2.M20061214-1200.jar.so)
at org.eclipse.jface.action.ActionContributionItem.handleWidgetSelection(org.eclipse.jface_3.2.2.M20061214-1200.jar.so)
at org.eclipse.jface.action.ActionContributionItem.access$2(org.eclipse.jface_3.2.2.M20061214-1200.jar.so)
at org.eclipse.jface.action.ActionContributionItem$5.handleEvent(org.eclipse.jface_3.2.2.M20061214-1200.jar.so)
at org.eclipse.swt.widgets.EventTable.sendEvent(org.eclipse.swt.gtk.linux.x86_3.2.2.v3236.jar.so)
at org.eclipse.swt.widgets.Widget.sendEvent(org.eclipse.swt.gtk.linux.x86_3.2.2.v3236.jar.so)
at org.eclipse.swt.widgets.Display.runDeferredEvents(org.eclipse.swt.gtk.linux.x86_3.2.2.v3236.jar.so)
at org.eclipse.swt.widgets.Display.readAndDispatch(org.eclipse.swt.gtk.linux.x86_3.2.2.v3236.jar.so)
at org.eclipse.ui.internal.Workbench.runEventLoop(org.eclipse.ui.workbench_3.2.2.M20070119-0800.jar.so)
at org.eclipse.ui.internal.Workbench.runUI(org.eclipse.ui.workbench_3.2.2.M20070119-0800.jar.so)
at org.eclipse.ui.internal.Workbench.createAndRunWorkbench(org.eclipse.ui.workbench_3.2.2.M20070119-0800.jar.so)
at org.eclipse.ui.PlatformUI.createAndRunWorkbench(org.eclipse.ui.workbench_3.2.2.M20070119-0800.jar.so)
at org.eclipse.ui.internal.ide.IDEApplication.run(org.eclipse.ui.ide_3.2.1.M20060915-1030.jar.so)
at org.eclipse.core.internal.runtime.PlatformActivator$1.run(org.eclipse.core.runtime_3.2.0.v20060603.jar.so)
at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.runApplication(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.start(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
at org.eclipse.core.runtime.adaptor.EclipseStarter.run(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
at org.eclipse.core.runtime.adaptor.EclipseStarter.run(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
at java.lang.reflect.Method.invoke(libgcj.so.90)
at org.eclipse.core.launcher.Main.invokeFramework(Main.java:336)
at org.eclipse.core.launcher.Main.basicRun(Main.java:280)
at org.eclipse.core.launcher.Main.run(Main.java:977)
at org.eclipse.core.launcher.Main.main(Main.java:952)


```

Rather annoying, as I'm too stupid to know what it means, and I'd like to step up from IDLE a bit.

Any help is appreciated, thanks.

---

### Post by colau on 2009-06-12
You can use netbeans.
It supports many language.
[http://www.netbeans.org/features/python/]("http://www.netbeans.org/features/python/")

---

### Post by kpkeerthi on 2009-06-12
You seem to be using GCJ. Install Sun JDK 6 or Open JDK 6 and **set it the default JDK** for your PC. See [https://help.ubuntu.com/community/Java]("https://help.ubuntu.com/community/Java") for instructions.

Make sure it is active with the following command:
```
java -version
```

---

### Post by Asday on 2009-06-12
> **colau said:**
> You can use netbeans.
It supports many language.
[http://www.netbeans.org/features/python/]("http://www.netbeans.org/features/python/")

I wish to use Eclipse, otherwise I would have given up and used something else.

> You seem to be using GCJ. Install Sun JDK 6 or Open JDK 6 and set it the default JDK for your PC. See [https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java) for instructions.

Ok, I followed the instructions there, but it said I already had openjdk 6 installed, and after following all instructions, "java -version" output the same thing, and Eclipse still doesn't work.

I noticed this line upon startup, though:

```
testing /usr/lib/jvm/java-gcj...found

```

So is Eclipse specifically asking for GCJ?

---

### Post by Asday on 2009-06-14
SUPER-BUMP.

I tried using sun JDK too, and the same errors happen.  I also deleted my ~/.eclipse folder, and problems persist.

(Not sure if I mentioned, but I can't access Window->Preferences->PyDev->Interpreter-Python.  It says:  "The currently displayed page contains invalid values.")

---

### Post by Asday on 2009-06-30
[size="1"]uselessbump:d:d:d:d:d:d[/size]

(Oh wow, it changes allcaps to allsmall.  That's pretty clever.)

---

