---
title: "Java Gtk error"
date: 2006-07-17
forum: Desktop Environments
---

### Post by reegz on 2006-07-17
Hi guys,

I upgraded my distro to 6.06 this weekend and am now having trouble running java swing apps.

I get the following error.

```

Exception in thread "main" java.awt.AWTError: Cannot load AWT toolkit: gnu.java.awt.peer.gtk.GtkToolkit
   at java.awt.Toolkit.getDefaultToolkit(libgcj.so.7)
   at java.awt.GraphicsEnvironment.getLocalGraphicsEnvironment(libgcj.so.7)
   at java.awt.Window.<init>(libgcj.so.7)
   at java.awt.Frame.<init>(libgcj.so.7)
   at java.awt.Frame.<init>(libgcj.so.7)
   at javax.swing.SwingUtilities$OwnerFrame.<init>(libgcj.so.7)
   at javax.swing.SwingUtilities.getOwnerFrame(libgcj.so.7)
   at javax.swing.JDialog.<init>(libgcj.so.7)
   at uk.co.kmatech.sms.ui.SetUpPanel.<init>(Unknown Source)
   at uk.co.kmatech.sms.ui.OpenSMSWizard.main(Unknown Source)
Caused by: java.lang.ClassNotFoundException: gnu.java.awt.peer.gtk.GtkToolkit
   at java.lang.Class.forName(libgcj.so.7)
   at java.lang.Class.forName(libgcj.so.7)
   at java

```

The lib being referred to exists

```

lrwxrwxrwx 1 root root       15 2006-07-14 23:39 /usr/lib/libgcj.so.7 -> libgcj.so.7.0.0
-rw-r--r-- 1 root root 21225540 2006-04-22 04:06 /usr/lib/libgcj.so.7.0.0

```

Im goind round in circles and have no idea how to resolve this. ](*,)  any help will be gladly welcome

---

### Post by reegz on 2006-07-17
Nevermind. I found the error. the version of java being used was the gij version and not the java from sun... 

problem solved.

---

