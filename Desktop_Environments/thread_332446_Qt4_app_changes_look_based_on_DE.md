---
title: "Qt4 app changes look based on DE?"
date: 2007-01-06
forum: Desktop Environments
---

### Post by Jessehk on 2007-01-06
I copied a simple tutorial program demonstrating Qt4, and compiled it.

When run under Gnome, it has the appearance of a gtk+ app, whereas under KDE, it looks like a typical Qt app.

Is this some sort of fantastic new feature, or am I getting excited over nothing?

---

### Post by IYY on 2007-01-07
I checked the Wikipedia article for QT, and here's what it has to say:

> **Complete abstraction of the GUI**

Qt uses its own paint engine and controls. This makes the work of porting to other platforms easier because very few classes in Qt depended really on the target platform. Qt used to emulate the native look of its intended platforms, which occasionally led to slight discrepancies where that emulation wasn't perfect. This, however, no longer applies because the latest versions of Qt use the native styles API of the different platforms to draw the Qt controls. This approach is similar to that of the Swing toolkit in Java

---

