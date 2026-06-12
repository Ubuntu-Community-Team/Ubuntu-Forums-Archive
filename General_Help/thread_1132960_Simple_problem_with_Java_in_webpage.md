---
title: "Simple problem with Java in webpage"
date: 2009-04-22
forum: General Help
---

### Post by frenchn00b on 2009-04-22
Hello,

I try to embed the jar file into my webpage:

with this code:
```
<OBJECT classid="clsid:8AD9C840-044E-11D1-B3E9-00805F499D93"
width=512 height=632 align=baseline
codebase=http://java.sun.com/products/plugin/autodl/jinstall-1_3_1-windows-i586.cab#Version=1,1,1,0>
<PARAM name='codebase' value='.'>
<PARAM name='archive' value='SomeJavaApp.jar'>
<PARAM name='code' value='SomeJavaApp.class'>
<PARAM name='type' value='application/x-java-applet;jpi-version=1.3.1'>
<COMMENT> <EMBED type='application/x-java-applet;version=1.3.1'
width='512' height='632' align='baseline' code='SomeJavaApp.class' archive='myjarapplication.jar'
codebase='.' pluginspage='http://java.sun.com'>
<NOEMBED>No Java 2 Support Found</NOEMBED>
</EMBED>
</COMMENT>
</OBJECT>
```


```
Java Plug-in 1.5.0_01
Verwendung der JRE-Version 1.5.0_01 Java HotSpot(TM) Client VM
Home-Verzeichnis des Benutzers = C:\Dokumente und Einstellungen\frenchn00b


----------------------------------------------------
c:   Konsolenfenster schließen
f:   Objekte in Finalisierungswarteschlange finalisieren
g:   Speicherbereinigung
h:   Diese Hilfemeldung anzeigen
l:   ClassLoader-Liste ausgeben
m:   Speicherbelegung anzeigen
o:   Protokollierung auslösen
p:   Proxy-Konfiguration neu laden
q:   Konsole ausblenden
r:   Richtlinien-Konfiguration neu laden
s:   System- und Bereitstellungseigenschaften ausgeben
t:   Threadliste ausgeben
v:   Thread-Stack ausgeben
x:   ClassLoader-Cache löschen
0-5: Trace-Stufe auf <n> setzen
----------------------------------------------------

Cookie-Service nicht verfügbar - Cache zum Ermitteln von "Cookie" verwenden
Cookie-Service nicht verfügbar - Cache zum Ermitteln von "Cookie" verwenden
APPLET-Marke ohne CODE-Parameter
java.lang.NullPointerException: name
APPLET-Marke ohne CODE-Parameter
	at sun.applet.AppletClassLoader.getResourceAsStream(Unknown Source)
	at sun.applet.AppletPanel$6.run(Unknown Source)
	at java.security.AccessController.doPrivileged(Native Method)
	at sun.applet.AppletPanel.createApplet(Unknown Source)
	at sun.plugin.AppletViewer.createApplet(Unknown Source)
	at sun.applet.AppletPanel.runLoader(Unknown Source)
	at sun.applet.AppletPanel.run(Unknown Source)
	at java.lang.Thread.run(Unknown Source)
java.lang.NullPointerException: name
	at sun.applet.AppletClassLoader.getResourceAsStream(Unknown Source)
	at sun.applet.AppletPanel$6.run(Unknown Source)
	at java.security.AccessController.doPrivileged(Native Method)
	at sun.applet.AppletPanel.createApplet(Unknown Source)
	at sun.plugin.AppletViewer.createApplet(Unknown Source)
	at sun.applet.AppletPanel.runLoader(Unknown Source)
	at sun.applet.AppletPanel.run(Unknown Source)
	at java.lang.Thread.run(Unknown Source)
Laden: Klasse SomeJavaApp.class nicht gefunden
java.lang.ClassNotFoundException: SomeJavaApp.class
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
Laden: Klasse SomeJavaApp.class nicht gefunden
java.lang.ClassNotFoundException: SomeJavaApp.class
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

```

But I get those errors.

What could it be? 
Best regards

---

