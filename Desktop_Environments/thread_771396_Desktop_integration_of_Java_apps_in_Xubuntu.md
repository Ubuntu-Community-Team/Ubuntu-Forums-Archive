---
title: "Desktop integration of Java apps in Xubuntu"
date: 2008-04-27
forum: Desktop Environments
---

### Post by jdarias on 2008-04-27
I've switched from Gnome to xfce and so far the adaptation has been nice despite some missing things.
The main one is the lack of desktop integration of Java apps and Xubuntu. They do not use the native theme. Instead they use a Java look.
This didn't happen in Ubuntu. Is it possible to make this happen in Xubutu?

Edit: forgot to mention: this happens with FreeMind and the Java Panel so far. Got to try Azureus. This is Xubuntu 8.04

---

### Post by jdarias on 2008-04-28
bump

---

### Post by revertex on 2008-04-29
look here 

[http://ubuntuforums.org/showthread.php?t=383394](http://ubuntuforums.org/showthread.php?t=383394)

[http://java.sun.com/docs/books/tutorial/uiswing/lookandfeel/plaf.html#steps](http://java.sun.com/docs/books/tutorial/uiswing/lookandfeel/plaf.html#steps)

---

### Post by jdarias on 2008-04-30
I looked both pages, followed the advice of the thread but it didn't work. The other one (from java) was more like developer relevant stuff.

---

### Post by revertex on 2008-05-05
from the java page:

> **  Specifying the Look and Feel: Command Line  **

   You can specify the L&F at the command line by using the -D flag to set the swing.defaultlaf property.  For example:  ```
java -Dswing.defaultlaf=com.sun.java.swing.plaf.gtk.GTKLookAndFeel MyApp
```

---

### Post by janfsd on 2008-05-06
I got a similar problem, it might be related. I am using Gnome though, but when running a java application with root, i get the metal theme. It works normally for normal user, it loads the gtk theme, but I don't know why this happens. In Gutsy it didn't.

You could try this in the terminal:
```
export _JAVA_OPTIONS="-Dswing.defaultlaf=com.sun.java.swing.plaf.gtk.GTKLookAndFeel"
```
and after run freemind and see, and check the terminal messages, maybe you can see some message related to your problem. I am still looking for a solution to my problem.

Another option could be creating, or editing the swing.properties file. It should be here: /usr/lib/jvm/java-6-sun/jre/lib
if you are using java6:
```
# Swing properties
swing.defaultlaf=com.sun.java.swing.plaf.gtk.GTKLookAndFeel

```

---

### Post by revertex on 2008-05-06
I give up, none of these options works for me.

---

### Post by janfsd on 2008-05-06
And for the second option, you have to check wich java you are using:
```
sudo update-alternatives --list java
```
Change to java-6-sun if necessary.

Anyway the metal theme is not that bad. :D

---

### Post by janfsd on 2008-05-06
Sorry for double post. Delete this if possible.

---

