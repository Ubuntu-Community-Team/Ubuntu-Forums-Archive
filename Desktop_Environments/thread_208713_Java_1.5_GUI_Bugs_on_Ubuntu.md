---
title: "Java 1.5 GUI Bugs on Ubuntu"
date: 2006-07-04
forum: Desktop Environments
---

### Post by alexgutteridge on 2006-07-04
Hi,

I have a Java application which runs fine under OS X (Java version 1.5 Update 6). I have installed and selected the Sun Java package so that the Ubuntu Java is also version 1.5 Update 6, but the application has strange gui bugs running under Ubuntu 6.06.

GUI elements like buttons, sliders etc.. dissappear when the application window is resized and only reappear (if at all) when the mouse is passed over them. This makes working with the application extremely frustrating, but I can't work out what the problem is. The author insists that it runs fine for him on Java 1.5 and given that it runs fine on OS X I have no reason to doubt him.

Has anyone seen this before on Ubuntu, or have any ideas on any Java settings I can play with? My Java knowledge is fairly slim, so I'm at the end of my tether. :(

---

### Post by kpkeerthi on 2006-07-04
Can you post what is the result of executing
```
java -version
``` from the terminal window/ We can proceed from there.

---

### Post by alexgutteridge on 2006-07-04
[QUOTE=kpkeerthi]Can you post what is the result of executing
```
java -version
``` from the terminal window/ We can proceed from there.[/QUOTE]

On Ubuntu:

```
java version "1.5.0_06"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_06-b05)
Java HotSpot(TM) Client VM (build 1.5.0_06-b05, mixed mode, sharing)
```

Under OS X I get:

```
java version "1.5.0_06"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_06-112)
Java HotSpot(TM) Client VM (build 1.5.0_06-64, mixed mode, sharing)
```

So a different build (obviously I guess) but identical otherwise I assume.

---

### Post by kpkeerthi on 2006-07-04
Thats sounds OK to me. I have had problems running swing-based Java apps with the native GTK look and feel. And the symptoms were exactly the same as yours (GUI elements like buttons, sliders etc.. dissappear when the application window is resized and only reappear (if at all) when the mouse is passed over them). But when I switched the Look and Feel to 'Metal' (the standard Java look and feel), it runs just fine. Do you have access to source code so that you can change the look and feel and recompile the code? Just to be sure, can you post a screenshot of the app you are running?

---

### Post by kpkeerthi on 2006-07-04
Try 
```

java -Dswing.defaultlaf=javax.swing.plaf.metal.MetalLookAndFeel YouAppClassFileName

``` from command line and see if it solves the problem.

---

### Post by alexgutteridge on 2006-07-04
Your diagnosis looks to be getting somewhere near the problem. On a hunch I just tried running the app under a KDE session (rather than Gnome), and it runs perfectly. As I said before, my Java knowledge is close to zero, but it looks like there is some bug in the whole Java / GTK / Gnome setup. Whether it's an Ubuntu issue or not I don't know. Thanks for your help anyway.

---

