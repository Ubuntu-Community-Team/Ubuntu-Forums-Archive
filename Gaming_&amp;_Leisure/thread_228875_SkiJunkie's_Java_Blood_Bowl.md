---
title: "SkiJunkie's Java Blood Bowl"
date: 2006-08-03
forum: Gaming &amp; Leisure
---

### Post by Cpt_Fluffy on 2006-08-03
[See here for specific software that's leaving me stumped.]("http://javabbowl.no-ip.org/")

I'm trying to get this running on Ubuntu Dapper.  I'm totally new to the Linux experience, so treat me like a tard at all times, please ](*,) 

Right, I'm pretty sure my issue is with Java here.  I'm currently using the version of java that ships with Ubuntu - but have tried using the Sun packages from the repository.

```
sam@sam-desktop:~$ java -version
java version "1.4.2"
gij (GNU libgcj) version 4.1.0 (Ubuntu 4.1.0-1ubuntu8)

Copyright (C) 2006 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.
```

And the error I get (with or without the Sun packages) is

```
sam@sam-desktop:~/.Blood Bowl$ java -jar Bbowl.jar
Exception in thread "main" java.awt.AWTError: Cannot load AWT toolkit: gnu.java.awt.peer.gtk.GtkToolkit
   at java.awt.Toolkit.getDefaultToolkit(libgcj.so.7)
   at java.awt.Font.tk(libgcj.so.7)
   at java.awt.Font.getPeerFromToolkit(libgcj.so.7)
   at java.awt.Font.<init>(libgcj.so.7)
   at javax.swing.plaf.FontUIResource.<init>(libgcj.so.7)
   at javax.swing.plaf.metal.DefaultMetalTheme.<clinit>(libgcj.so.7)
   at java.lang.Class.initializeClass(libgcj.so.7)
   at javax.swing.plaf.metal.MetalLookAndFeel.createDefaultTheme(libgcj.so.7)
   at javax.swing.plaf.metal.MetalLookAndFeel.<init>(libgcj.so.7)
   at javax.swing.UIManager.<clinit>(libgcj.so.7)
   at java.lang.Class.initializeClass(libgcj.so.7)
   at bbowl.Bbowl.main(Unknown Source)
Caused by: java.lang.ClassNotFoundException: gnu.java.awt.peer.gtk.GtkToolkit
   at java.lang.Class.forName(libgcj.so.7)
   at java.lang.Class.forName(libgcj.so.7)
   at java.awt.Toolkit.getDefaultToolkit(libgcj.so.7)
   ...11 more
```

Now, if anyone can give me any (very simply worded) advice, I'd be greatful.

And if anyone can give me a painstakingly detailed step by step guide assuuming a fresh install of Ubuntu Dapper, I'd be over the moon.

Thanks in advance to any fellow Blood Bowlers.

:KS

---

### Post by Cpt_Fluffy on 2006-08-06
A single bump - then I'll leave it.

:-({|=

---

### Post by Burkey on 2006-08-07
If you open synaptic you can find the Sun Java interpreter.  Install that and remove the gij one and you should be good to go.

The top output shows you do not have the Sun one installed or it is not the default.

---

### Post by Cpt_Fluffy on 2006-08-07
Ah-ha.  Works a treat now.

That's awesome Burkey, thank you ever so much.

Now, a much less pressing follow-up question:

I'm using ```
java -jar Bbowl.jar
``` from Terminal in the Blood Bowl directory to launch it.

I want to add it to my Panel Menu.  I've tried using the same command but it comes out with a java error.  Is there something clever I can do?  Or should I just be happy with what I've got now 8)

---

### Post by patrick295767 on 2006-08-08
> **Cpt_Fluffy said:**
> [See here for specific software that's leaving me stumped.]("http://javabbowl.no-ip.org/")

I'm trying to get this running on Ubuntu Dapper.  I'm totally new to the Linux experience, so treat me like a tard at all times, please ](*,) 

Right, I'm pretty sure my issue is with Java here.  I'm currently using the version of java that ships with Ubuntu - but have tried using the Sun packages from the repository.

```
sam@sam-desktop:~$ java -version
java version "1.4.2"
gij (GNU libgcj) version 4.1.0 (Ubuntu 4.1.0-1ubuntu8)

Copyright (C) 2006 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.
```

And the error I get (with or without the Sun packages) is

```
sam@sam-desktop:~/.Blood Bowl$ java -jar Bbowl.jar
Exception in thread "main" java.awt.AWTError: Cannot load AWT toolkit: gnu.java.awt.peer.gtk.GtkToolkit
   at java.awt.Toolkit.getDefaultToolkit(libgcj.so.7)
   at java.awt.Font.tk(libgcj.so.7)
   at java.awt.Font.getPeerFromToolkit(libgcj.so.7)
   at java.awt.Font.<init>(libgcj.so.7)
   at javax.swing.plaf.FontUIResource.<init>(libgcj.so.7)
   at javax.swing.plaf.metal.DefaultMetalTheme.<clinit>(libgcj.so.7)
   at java.lang.Class.initializeClass(libgcj.so.7)
   at javax.swing.plaf.metal.MetalLookAndFeel.createDefaultTheme(libgcj.so.7)
   at javax.swing.plaf.metal.MetalLookAndFeel.<init>(libgcj.so.7)
   at javax.swing.UIManager.<clinit>(libgcj.so.7)
   at java.lang.Class.initializeClass(libgcj.so.7)
   at bbowl.Bbowl.main(Unknown Source)
Caused by: java.lang.ClassNotFoundException: gnu.java.awt.peer.gtk.GtkToolkit
   at java.lang.Class.forName(libgcj.so.7)
   at java.lang.Class.forName(libgcj.so.7)
   at java.awt.Toolkit.getDefaultToolkit(libgcj.so.7)
   ...11 more
```

Now, if anyone can give me any (very simply worded) advice, I'd be greatful.

And if anyone can give me a painstakingly detailed step by step guide assuuming a fresh install of Ubuntu Dapper, I'd be over the moon.

Thanks in advance to any fellow Blood Bowlers.

:KS

 Your post is cool !  I really like this game. I didnt know it was available for PC.  Cool 

Thx

---

### Post by andykrueger on 2006-12-02
I just started using this program and ran against the same problem when trying to add a menu item.  I think the first step is to create a script like this one:

```
#!/bin/bash
##
## Starts Blood Bowl from menu
 
java -jar Bbowl.jar
```

I named it Bbowl-start.  When I run this script (in the same location as Bbowl.jar) with ./Bbowl-start, it runs the program.  But when I try to set it up in the Menu Editor with a full path, nothing happens.  Or in terminal, I get this error:

```
andy@andy-desktop:~$ /home/andy/Bbowl8_6/Bbowl-start
Unable to access jarfile Bbowl.jar
```

It's obviously running the script but hitting a snag.  Tried to run it with sudo, etc, but no luck.  I can't think of any good reason why the script should run from its own directory, but not when using a full path.  I assume it's because of Java somehow, but that's the extent of my knowledge!  I'd be grateful if someone could figure out the next step.

---

### Post by gyerekember on 2008-03-10
How about
```
#!/bin/bash
##
## Starts Blood Bowl from menu

cd  /home/andy/Bbowl8_6/
java -jar Bbowl.jar
```
?

---

### Post by hark130 on 2010-01-10
I'm having some problems with Skijunkie's Java Blood Bowl as well.  

[B]
First[/B], my details:

I'm using 9.10 Karmic Koala on a Compaq Presario C700
hark@Comhaq:~$ java -version
java version "1.6.0_0"
OpenJDK Runtime Environment (IcedTea6 1.6.1) (6b16-1.6.1-3ubuntu1)
OpenJDK Client VM (build 14.0-b16, mixed mode, sharing)

[B]
Second[/B], the problem:

The problem doesn't occur until I actually begin a match.  When I receive a CAS, I get prompted if I want to use my apothecary (which is normal).  If I choose yes, everything works fine.  If I choose no, the client locks up.  The player doesn't head to the CAS box, the chat window won't exchange messages, and my opponent can't continue.  I don't have this problem if I play the game locally.  This only occurs when I play a game online.


**Third**, what I've done to troubleshoot:


[LIST=1]
[*]I've run the client through sudo (sudo java -jar BBowl.jar)
[*]I've tried it substituted as root (su root then java -jar BBowl.jar)
[*]I've tried it substituted as root in a login shell (su - root then java -jar BBowl.jar)
[*]I've tried it in another workspace (just in case a window was hidden)
[*]I've verified both root and my user "hark" have write access
[*]I set the window to always be on top (just in case I was missing something)
[/LIST]

I'm out of ideas and could really use some help.

---

