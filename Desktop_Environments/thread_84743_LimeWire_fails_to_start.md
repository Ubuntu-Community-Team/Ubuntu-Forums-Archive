---
title: "LimeWire fails to start"
date: 2005-10-31
forum: Desktop Environments
---

### Post by Brian McConnell on 2005-10-31
Hi,
LimeWire won't start for me!

Here's the terminal output:
```
brian@ubuntu:~$ /usr/bin/runLime.sh
Starting LimeWire...
Java exec found in PATH. Verifying...
Suitable java version found [java = 1.4.2]
Configuring environment...
Loading LimeWire:
java.lang.ExceptionInInitializerError
        at com.limegroup.gnutella.gui.Main.showInitialSplash(Main.java:67)
        at com.limegroup.gnutella.gui.Main.main(Main.java:39)
Caused by: java.lang.NullPointerException
        at java.lang.ClassLoader.loadLibrary0(ClassLoader.java:2171)
        at java.lang.ClassLoader.loadLibrary(ClassLoader.java:2006)
        at java.lang.Runtime.loadLibrary0(Runtime.java:824)
        at java.lang.System.loadLibrary(System.java:908)
        at sun.security.action.LoadLibraryAction.run(LoadLibraryAction.java:76)
        at java.security.AccessController.doPrivileged1(Native Method)
        at java.security.AccessController.doPrivileged(AccessController.java:287)
        at java.awt.Toolkit.loadLibraries(Toolkit.java:1488)
        at java.awt.Toolkit.<clinit>(Toolkit.java:1511)
        ... 2 more

******************************************************************
Something went wrong with LimeWire.
Maybe you're using the wrong version of Java?
(LimeWire is tested against and works best with with Sun's JRE, Java 1.4+)
The version of Java in your PATH is:
java version "1.4.2"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.4.2)
Classic VM (build 1.4.2, J2RE 1.4.2 IBM build cxppc32142-20050609 (JIT enabled: jitc))

brian@ubuntu:~$
```

here's the terminal output for checking my java version:
```
brian@ubuntu:~$ java -version
java version "1.4.2"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.4.2)
Classic VM (build 1.4.2, J2RE 1.4.2 IBM build cxppc32142-20050609 (JIT enabled: jitc))
brian@ubuntu:~$
```

Any suggestions? Installation of both java and Limwire seemed to have gone fine without a hitch. So, I'm a bit stumped. Any help would be greatly appreciated.
Thanks,
Brian

ps - I am sorry to cross-post, it's just that my original post in the ppc section got little response so I hoped posting here would possibly get some ideas and I think this may not be ppc specific. I had originally posted this thread at [http://ubuntuforums.org/showthread.php?t=80783]("http://ubuntuforums.org/showthread.php?t=80783")

---

### Post by jmcnaught on 2005-11-01
hi,

i don't know if this is much help, but i've had trouble running LimeWire on java 1.4 on x86.  unfortunately, i don't think java 1.5 is available for linux powerpc.

have you checked the limewire website?

personally, i don't use limewire because i find it slow and it consumes a lot of ram.  and it takes forever to index my collection.  thankfully there are other options in ubuntu for connecting to gnutella (the network that limewire uses).

gtk-gnutella is the easiest to get up and running, but the interface is very cluttered hard to navigate.  there is also giftd which is a daemon (server) that runs in the background and connects to gnutella, fasttrack (kazaa) and maybe other networks at the same time.  you need a giftd client to use it.  Giftoxic and giftui are GTK clients that look pretty nice, and Apollon is available for KDE.

I tried getting giftui and giftoxic to work in hoary... there's a configuration script that you need to run that has a lot of questions.  i ran that script dozens of times and spent hours researching online... hopefully you fair better.

Also: MLDonkey.  It can download from eMule/eDonkey2k, Gnutella, Soulseek, DCC, Overnet and Bittorrent.  Like giftd, it's a client server model.  I've never tried it in Ubuntu.

Finally: mutella.  I have not tried it, but apparently it has an ncurses (text only, use in a terminal window) interface or you can control it through your web browser (probably by going to [http://localhost:9304](http://localhost:9304) or some other number).

If you want to browse the descriptions of these and other programs, search for gnutella in synaptic.

---

### Post by zekolas on 2005-11-01
Limewire is running great for me however I have the JRE 1.5 installed, so you might want to try and download and install the latest JRE from sun's web site

---

### Post by mips on 2005-11-01
Download and install Automatix. Use it to install your Java & Limewire.

This is how i installed all my apps and have no problems except for SkypeOut not wanting to make a call after the first one.

---

### Post by tseliot on 2005-11-01
Type "sudo update-alternatives --config java" and select the java version that matches yours.

It worked for me.

---

### Post by Brian McConnell on 2005-11-24
Problem solved by updating to java 1.5. still using ibm's java.
this is on ppc.

---

