---
title: "Cant get java plugin to work in firefox"
date: 2010-03-24
forum: Desktop Environments
---

### Post by zooounds on 2010-03-24
I have tried everything according to the instructions.

My packages:

```

$ dpkg -l | grep java6
ii  sun-java6-bin                              6-15-1                                                     Sun Java(TM) Runtime Environment (JRE) 6 (architecture depend
ii  sun-java6-fonts                            6-15-1                                                     Lucida TrueType fonts (from the Sun JRE)
ii  sun-java6-jre                              6-15-1                                                     Sun Java(TM) Runtime Environment (JRE) 6 (architecture indepe
ii  sun-java6-plugin                           6-15-1                                                     The Java(TM) Plug-in, Java SE 6

```

Firefox says:

```

Java(TM) Plug-in 1.6.0_15-b03

    Filnamn: libjavaplugin_oji.so
    Java(TM) Plug-in 1.6.0_15

MIME-typ 	Beskrivning 	Filändelse 	Aktiverad
application/x-java-vm 	Java™ Plug-in 		Ja
application/x-java-applet 	Java™ Plug-in Applet 		Ja
application/x-java-applet;version=1.1 	Java™ Plug-in 		Ja
application/x-java-applet;version=1.1.1 	Java™ Plug-in 		Ja
application/x-java-applet;version=1.1.2 	Java™ Plug-in 		Ja
application/x-java-applet;version=1.1.3 	Java™ Plug-in 		Ja
application/x-java-applet;version=1.2 	Java™ Plug-in 		Ja
application/x-java-applet;version=1.2.1 	Java™ Plug-in 		Ja
application/x-java-applet;version=1.2.2 	Java™ Plug-in 		Ja
application/x-java-applet;version=1.3 	Java™ Plug-in 		Ja
application/x-java-applet;version=1.3.1 	Java™ Plug-in 		Ja
application/x-java-applet;version=1.4 	Java™ Plug-in 		Ja
application/x-java-applet;version=1.4.1 	Java™ Plug-in 		Ja
application/x-java-applet;version=1.4.2 	Java™ Plug-in 		Ja
application/x-java-applet;version=1.5 	Java™ Plug-in 		Ja
application/x-java-applet;version=1.6 	Java™ Plug-in 		Ja
application/x-java-applet;jpi-version=1.6.0_15 	Java™ Plug-in 		Ja
application/x-java-bean 	Java™ Plug-in JavaBeans 		Ja
application/x-java-bean;version=1.1 	Java™ Plug-in 		Ja
application/x-java-bean;version=1.1.1 	Java™ Plug-in 		Ja
application/x-java-bean;version=1.1.2 	Java™ Plug-in 		Ja
application/x-java-bean;version=1.1.3 	Java™ Plug-in 		Ja
application/x-java-bean;version=1.2 	Java™ Plug-in 		Ja
application/x-java-bean;version=1.2.1 	Java™ Plug-in 		Ja
application/x-java-bean;version=1.2.2 	Java™ Plug-in 		Ja
application/x-java-bean;version=1.3 	Java™ Plug-in 		Ja
application/x-java-bean;version=1.3.1 	Java™ Plug-in 		Ja
application/x-java-bean;version=1.4 	Java™ Plug-in 		Ja
application/x-java-bean;version=1.4.1 	Java™ Plug-in 		Ja
application/x-java-bean;version=1.4.2 	Java™ Plug-in 		Ja
application/x-java-bean;version=1.5 	Java™ Plug-in 		Ja
application/x-java-bean;version=1.6 	Java™ Plug-in 		Ja
application/x-java-bean;jpi-version=1.6.0_15 	Java™ Plug-in

```

("Ja" means "Yes")

But java.com:s test page can't detect my java.

---

