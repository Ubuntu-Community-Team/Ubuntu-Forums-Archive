---
title: "Default XML parser for Java"
date: 2006-07-31
forum: Desktop Environments
---

### Post by Sak on 2006-07-31
Hey all,

I'm encountering a strange response from a Java program that I'm trying to run.  I'm running a default Ubuntu 6.06 install, the only extra installs are stuff like Xgl, Compiz, and some items from Easyubuntu - such as Flash plugin etc.  

The program I'm trying to run is here:

[http://nmedit.sourceforge.net](http://nmedit.sourceforge.net)

Now I have no idea what's going wrong here, but one of the developers for the project tells me that the XML parser that Java is using by default is having trouble with the program.  Here's the output that I get when I try to run the program...

```

sak@demian:~/wip/nmedit/sak/nomad-0.2$ java -jar nomad-0.2.jar
Exception in thread "main" java.awt.AWTError: Cannot load AWT toolkit: gnu.java.awt.peer.gtk.GtkToolkit
   at java.awt.Toolkit.getDefaultToolkit(libgcj.so.7)
   at net.sf.nmedit.nomad.core.application.splash.SplashScreen.imageFromURL(Unknown Source)
   at net.sf.nmedit.nomad.core.application.splash.SplashScreen.advance(Unknown Source)
   at net.sf.nmedit.nomad.core.application.Application.create(Unknown Source)
   at net.sf.nmedit.nomad.core.nomad.Nomad.main(Unknown Source)
Caused by: java.lang.ClassNotFoundException: gnu.java.awt.peer.gtk.GtkToolkit
   at java.lang.Class.forName(libgcj.so.7)
   at java.lang.Class.forName(libgcj.so.7)
   at java.awt.Toolkit.getDefaultToolkit(libgcj.so.7)
   ...4 more

```

Anyone have any suggestions they can offer that might help out?  Is this a problem with Ubuntu's default installation of Java somewhere?

---

### Post by JKoder on 2006-08-01
Hy it seems that you dont have some libraries like gnu.java.awt
Try installing sun java 1.5.x jre (from synaptic) that may help you.

But you need a XML parser ?

---

### Post by Sak on 2006-08-01
Thanks for having a look at my problem JKoder.  I have to apologize though.  I just looked back through the email correspondence I had with the developer and discovered that the error output I was getting before was related to the XML parser.  Comparing my old error messages to these is something I should have done before I posted here.  For reference, here's the previous error I was getting before reinstalling Ubuntu:

```

sak@demian:~/wip/nomad/sak/nomad$ java -jar nomad.jar
Exception in thread "main"
net.sf.nmedit.nomad.core.application.ApplicationInstantiationException:
java.util.InvalidPropertiesFormatException: Error in parsing XML.
   at net.sf.nmedit.nomad.core.application.Application.create(Unknown
Source)
   at net.sf.nmedit.nomad.core.nomad.Nomad.main(Unknown Source)
Caused by: java.util.InvalidPropertiesFormatException: Error in parsing
XML.
   at java.util.Properties.loadFromXML(libgcj.so.7)
   at
net.sf.nmedit.nomad.core.application.Application.putPropertiesFromXML(Unknown Source)
   at
net.sf.nmedit.nomad.core.application.Application.putPropertiesFromXML(Unknown Source)
   at net.sf.nmedit.nomad.core.application.Application.create(Unknown
Source)
   ...1 more
Caused by: org.xml.sax.SAXParseException: Illegal processing instruction
target (found "xml")
   at gnu.xml.aelfred2.SAXDriver.fatal(libgcj.so.7)
   at gnu.xml.aelfred2.XmlParser.error(libgcj.so.7)
   at gnu.xml.aelfred2.XmlParser.parsePI(libgcj.so.7)
   at gnu.xml.aelfred2.XmlParser.parseMarkupdecl(libgcj.so.7)
   at gnu.xml.aelfred2.XmlParser.parseDoctypedecl(libgcj.so.7)
   at gnu.xml.aelfred2.XmlParser.parseProlog(libgcj.so.7)
   at gnu.xml.aelfred2.XmlParser.parseDocument(libgcj.so.7)
   at gnu.xml.aelfred2.XmlParser.doParse(libgcj.so.7)
   at gnu.xml.aelfred2.SAXDriver.parse(libgcj.so.7)
   at gnu.xml.aelfred2.XmlReader.parse(libgcj.so.7)
   at java.util.Properties.loadFromXML(libgcj.so.7)
   ...4 more

```

Thanks for catching that.  Sorry about the mixup.

I just reinstalled Dapper over the weekend, wanting to get a fresh and clean installation to start over with.  My first install of Ubuntu was something of a trial run, and I had installed and played with just about everything that looked somewhat interesting - which I thought may have messed up a few things.  So the error that I'm recieving in the original post is what I'm getting now on my new system.  

Anyway, according to Synaptic, I have the packages you suggested already installed.

---

### Post by Sak on 2006-08-02
Just for the sake of completion, I've discovered a solution to this problem.

In my previous post I mentioned that I had installed Sun Java 1.5.0, but for whatever reason it wasn't being used, and the default Java system was instead.

I tracked down where the binary for Sun Java is installed.  On my Dapper install, 'java' is a symlink to '/etc/alternatives/java'  Which is in turn another link to one of the two different versions of Java installed in '/usr/lib/jvm/'

Instead of messing around with the system symlinks, I just made an alias in my .bashrc file like this:

```

alias sjava='/usr/lib/jvm/java-1.5.0-sun/bin/java'

```

Now I can launch the Sun 1.5 Java binary with the 'sjava' command and leave the default 'java' command as it is established by the system.  I thought this might be safer in case there are other applications that rely on the other version of Java.

Anyway, I thought I'd let you all know the details in case someone else writes in with a similar problem.

---

