---
title: "Java problem"
date: 2005-11-02
forum: Desktop Environments
---

### Post by VladTheImpaler on 2005-11-02
I am a n00b with a java problem.  I have installed Ubuntu and the Automatix additions.

I often listen to the internet stream here: [http://www.fmnewschannel975.com/kfncstream.htm](http://www.fmnewschannel975.com/kfncstream.htm)

When I try to do this on the new linux PC, the normal stream controls are absent and are replaced by a box with a red X in the upper left corner.  Even I know this is a problem.

When I right click the box, I get a java console with the following info:


Java Plug-in 1.5.0_05
Using JRE version 1.5.0_05 Java HotSpot(TM) Client VM
User home directory = /home/jay


----------------------------------------------------
c:   clear console window
f:   finalize objects on finalization queue
g:   garbage collect
h:   display this help message
l:   dump classloader list
m:   print memory usage
o:   trigger logging
p:   reload proxy configuration
q:   hide console
r:   reload policy configuration
s:   dump system and deployment properties
t:   dump thread list
v:   dump thread stack
x:   clear classloader cache
0-5: set trace level to <n>
----------------------------------------------------

load: class WMPNS.WMP not found.
java.lang.ClassNotFoundException: WMPNS.WMP
	at sun.applet.AppletClassLoader.findClass(Unknown Source)
	at java.lang.ClassLoader.loadClass(Unknown Source)
	at sun.applet.AppletClassLoader.loadClass(Unknown Source)
	at java.lang.ClassLoader.loadClass(Unknown Source)
	at sun.applet.AppletClassLoader.loadCode(Unknown Source)
	at sun.applet.AppletPanel.createApplet(Unknown Source)
	at sun.plugin.AppletViewer.createApplet(Unknown Source)
	at sun.applet.AppletPanel.runLoader(Unknown Source)
	at sun.applet.AppletPanel.run(Unknown Source)
	at java.lang.Thread.run(Unknown Source)
Caused by: java.io.IOException: open HTTP connection failed.
	at sun.applet.AppletClassLoader.getBytes(Unknown Source)
	at sun.applet.AppletClassLoader.access$100(Unknown Source)
	at sun.applet.AppletClassLoader$1.run(Unknown Source)
	at java.security.AccessController.doPrivileged(Native Method)
	... 10 more
Exception in thread "Thread-5" java.lang.NullPointerException
	at sun.plugin.util.GrayBoxPainter.showLoadingError(Unknown Source)
	at sun.plugin.AppletViewer.showAppletException(Unknown Source)
	at sun.applet.AppletPanel.runLoader(Unknown Source)
	at sun.applet.AppletPanel.run(Unknown Source)
	at java.lang.Thread.run(Unknown Source)
java.lang.NullPointerException
	at sun.plugin.util.GrayBoxPainter.showLoadingError(Unknown Source)
	at sun.plugin.AppletViewer.showAppletStatus(Unknown Source)
	at sun.applet.AppletPanel.run(Unknown Source)
	at java.lang.Thread.run(Unknown Source)
Exception in thread "thread applet-WMPNS.WMP" java.lang.NullPointerException
	at sun.plugin.util.GrayBoxPainter.showLoadingError(Unknown Source)
	at sun.plugin.AppletViewer.showAppletException(Unknown Source)
	at sun.applet.AppletPanel.run(Unknown Source)
	at java.lang.Thread.run(Unknown Source)
/usr/share/themes/Human/gtk-2.0/gtkrc:7: Failed to parse property value " GTK_SHADOW_NONE " for `GtkMenuItem::shadow-type'
/usr/share/themes/Human/gtk-2.0/gtkrc:58: Engine "clearlooks" is unsupported, ignoring
/usr/share/themes/Human/gtk-2.0/gtkrc:7: Failed to parse property value " GTK_SHADOW_NONE " for `GtkMenuItem::shadow-type'
/usr/share/themes/Human/gtk-2.0/gtkrc:58: Engine "clearlooks" is unsupported, ignoring

What have I done wrong and how should I fix this?  Thanks in advance for your help.

Vlad

---

### Post by jvictor on 2005-11-03
> load: class WMPNS.WMP not found.
java.lang.ClassNotFoundException: WMPNS.WMP

Caused by: java.io.IOException: open HTTP connection failed.



The VM is not able to find the class , maybe coz the server dint allow to connect , usuallly radio sites run on some non public port , so maybe ur applet maybe the route of the problems

---

### Post by ngms27 on 2005-11-03
I think its using a Microsoft Codec so you need W32Codecs installed.

JonnyT

---

### Post by VladTheImpaler on 2005-11-03
Jonny, w32 codecs are installed.

I did some googling and came up with this regarding a similar error:

[http://www.smeter.net/forums/post-643.html](http://www.smeter.net/forums/post-643.html)

> The problem is not that a Java module written by Microsoft will not run under Sun Java. The problem is that Microsoft doesn’t supply any Java module whatsoever to decode its better quality media streams. Microsoft media streams are decoded by compiled code that was written in C++ under Windows. Java error messages display because your web browser is trying to run Java code that doesn’t exist. Microsoft stopped providing Java plug-in code for other web browsers when Apple announced its Safari web browser. That was the “straw that broke the camel’s back,” so to speak. If Apple hadn’t released Safari Microsoft likely still would be supporting other browsers. If Microsoft was your company would you write code to make competitive browsers able to play the same high-quality media streams that can be played in Internet Explorer under Windows?


And this:

[http://support.microsoft.com/default.aspx?scid=kb;en-us;817855](http://support.microsoft.com/default.aspx?scid=kb;en-us;817855)

> FIX: Java Runtime Does Not Initialize the Windows Media Player 9 OCX Control in Netscape Navigator

Article ID	:	817855
Last Review	:	August 4, 2004
Revision	:	1.2

SYMPTOMS
If you use a version of Netscape Navigator that has an embedded <APPLET> tag for the Windows Media Player 9 Series OCX control, the Java Runtime may not initialize the control. You receive the following error message:
General Failure

java.lang.NoClassDefFoundError: sun/awt/DrawingSurface
     at WMPNS.WMP.getHWND(WMP.java)
     at WMPNS.WMP.start(WMP.java)
     at sun.applet.AppletPanel.run(Unknown Source)
     at java.lang.Thread.run(Unknown Source)
java.lang.NoClassDefFoundError: sun/awt/DrawingSurface
     at WMPNS.WMP.getHWND(WMP.java)
     at WMPNS.WMP.start(WMP.java)
     at sun.applet.AppletPanel.run(Unknown Source)
     at java.lang.Thread.run(Unknown Source)

CAUSE
This problem occurs because the Windows Media Player 9 Series OCX control uses methods that are no longer supported by Netscape.
RESOLUTION
The following file is available for download from the Microsoft Download Center:
DownloadDownload the WindowsMedia9-KB817885-x86-ENU.exe package now. ([http://download.microsoft.com/download/e/e/1/ee1fbd59-a2a3-4d69-8f28-3a6e34fd8216/windowsmedia9-kb817885-x86-enu.exe](http://download.microsoft.com/download/e/e/1/ee1fbd59-a2a3-4d69-8f28-3a6e34fd8216/windowsmedia9-kb817885-x86-enu.exe))
For additional information about how to download Microsoft Support files, click the following article number to view the article in the Microsoft Knowledge Base:

Is it possible to install this Microsoft patch?  Is it advisable?

---

