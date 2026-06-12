---
title: "Friggin SWT broke Azureus"
date: 2006-03-17
forum: Desktop Environments
---

### Post by Blairboy on 2006-03-17
I updated azureus and SWT (because it made me) and now when I run it, i get this crap.  Any ideas?

azureus
Exception in thread "main" java.lang.UnsatisfiedLinkError: no swt-pi-gtk-3139 in java.library.path
        at java.lang.ClassLoader.loadLibrary(Unknown Source)
        at java.lang.Runtime.loadLibrary0(Unknown Source)
        at java.lang.System.loadLibrary(Unknown Source)
        at org.eclipse.swt.internal.Library.loadLibrary(Library.java:123)
        at org.eclipse.swt.internal.gtk.OS.<clinit>(OS.java:19)
        at org.eclipse.swt.internal.Converter.wcsToMbcs(Converter.java:63)
        at org.eclipse.swt.internal.Converter.wcsToMbcs(Converter.java:54)
        at org.eclipse.swt.widgets.Display.<clinit>(Display.java:122)
        at org.gudy.azureus2.ui.swt.mainwindow.SWTThread.<init>(SWTThread.java:75)
        at org.gudy.azureus2.ui.swt.mainwindow.SWTThread.createInstance(SWTThread.java:58)
        at org.gudy.azureus2.ui.swt.mainwindow.Initializer.<init>(Initializer.java:108)
        at org.gudy.azureus2.ui.swt.Main.<init>(Main.java:147)
        at org.gudy.azureus2.ui.swt.Main.main(Main.java:162)

---

### Post by Blairboy on 2006-03-17
In case anyone has had the same problem with SWT updates in Azureus, here's a mini HowTo:

Go to your home/user/.azureus directory.  Copy all the libswt* files over the ones in your /usr/lib folder.  Azureus runs like a charm after that.

---

### Post by raven65az on 2006-08-08
> **Blairboy said:**
> In case anyone has had the same problem with SWT updates in Azureus, here's a mini HowTo:

Go to your home/user/.azureus directory.  Copy all the libswt* files over the ones in your /usr/lib folder.  Azureus runs like a charm after that.

Umm, what if those files do not exist in the home/user/.azureus directory?
I installed...encountered the same shell output....reinstalled..same issue, took your advice, and couldnt find the files you mention.
Scott (Raven)

---

### Post by raven65az on 2006-08-08
Did an alternate installation that worked perfectly...thanks;)

---

### Post by droogy on 2006-08-19
> **Blairboy said:**
> In case anyone has had the same problem with SWT updates in Azureus, here's a mini HowTo:

Go to your home/user/.azureus directory.  Copy all the libswt* files over the ones in your /usr/lib folder.  Azureus runs like a charm after that.

when I go into Azureus it download the swt3.2 for linux to my desktop and trying to update at which point it says the update was probably unsucessful (it doesn't have the rights to install/update, I imagine).

However I am able to go back into azureus and it works.. is there anyway I can' update to swt 3.2 otherwise?  is it on a repository somewhere?

---

