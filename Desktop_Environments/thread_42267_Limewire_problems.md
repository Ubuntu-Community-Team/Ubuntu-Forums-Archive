---
title: "Limewire problems"
date: 2005-06-16
forum: Desktop Environments
---

### Post by haaglin on 2005-06-16
I have some problems with limewire, when i try to run it i get this error:
A friend of mine has the same problem. anyone having this problem too? 
Reinstalling does not help. 
> 
Starting LimeWire...
Java exec found in PATH. Verifying...
Suitable java version found [java = 1.5.0_02]
Configuring environment...
Loading LimeWire:
java.lang.UnsatisfiedLinkError: initNative
        at org.jdesktop.jdic.tray.internal.impl.GnomeSystemTrayService.initNative(Native Method)
        at org.jdesktop.jdic.tray.internal.impl.GnomeSystemTrayService.<clinit>(Unknown Source)
        at org.jdesktop.jdic.tray.internal.impl.ServiceManagerStub.getService(Unknown Source)
        at org.jdesktop.jdic.tray.internal.ServiceManager.getService(Unknown Source)
        at org.jdesktop.jdic.tray.SystemTray.<clinit>(Unknown Source)
        at com.limegroup.gnutella.gui.notify.LinuxNotifyUser.<init>(LinuxNotifyUser.java:24)
        at com.limegroup.gnutella.gui.notify.NotifyUserProxy.<init>(NotifyUserProxy.java:49)
        at com.limegroup.gnutella.gui.notify.NotifyUserProxy.<clinit>(NotifyUserProxy.java:15)
        at com.limegroup.gnutella.gui.Initializer.initialize(Initializer.java:242)
        at com.limegroup.gnutella.gui.GUILoader.load(GUILoader.java:44)
        at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
        at sun.reflect.NativeMethodAccessorImpl.invoke(Unknown Source)
        at sun.reflect.DelegatingMethodAccessorImpl.invoke(Unknown Source)
        at java.lang.reflect.Method.invoke(Unknown Source)
        at com.limegroup.gnutella.gui.Main.main(Main.java:31)

******************************************************************
Something went wrong with LimeWire.
Maybe you're using the wrong version of Java?
(LimeWire is tested against and works best with with Sun's JRE, Java 1.4+)
The version of Java in your PATH is:
java version "1.5.0_02"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_02-b09)
Java HotSpot(TM) Client VM (build 1.5.0_02-b09, mixed mode)



---

### Post by SGC on 2005-06-16
How did you install it?

If you used ubuntuguide methode , then try this for alternate installtion methode:
[http://ubuntuforums.org/showpost.php?p=189682&postcount=5](http://ubuntuforums.org/showpost.php?p=189682&postcount=5)

---

### Post by haaglin on 2005-06-17
that is how i installed it.

---

### Post by bored2k on 2005-06-17
[QUOTE=haaglin]that is how i installed it.[/QUOTE]
 No no no dont convert rpm's !.
[http://ubuntuguide.org/#jre](http://ubuntuguide.org/#jre)
[http://ubuntuguide.org/#limewire](http://ubuntuguide.org/#limewire)

---

### Post by haaglin on 2005-06-17
Thanks. tried that, but still the same problem  :?

---

### Post by hammett111 on 2005-06-19
Use the AMD64 blacklist backports Java, your Limewire will not work with the 32bit libs java.

---

### Post by haaglin on 2005-06-19
where can i get that?

---

### Post by hammett111 on 2005-06-20
Hope this helps
 
 Where to get this: (right click + save link as..)
 [ftp://ftp.tux.org/pub/java/JDK-1.4.2/amd64/01/j2re-1.4.2-01-linux-amd64.bin](ftp://ftp.tux.org/pub/java/JDK-1.4.2/amd64/01/j2re-1.4.2-01-linux-amd64.bin)
 
 What to do with it?
 
 1. Make shell script executable,
 Right click on the file and change properties to executable
 
 2. Run the script,
 -> ./j2re-1.4.2-01-linux-amd64.bin
 -> Answer "yes" to the question
 
 3. When script execution has been completed, following directory should have been created:
 
 for example i ran the script in ~/home/quentin, and now in quentin is direcotory called j2re1.4.2
 
Now make a directory called /usr/local/java

 4. Now you can move the j2re1.4.2-directory to /usr/local/java (sudo mv j2re1.4.2 /usr/local/java).

5.  Open a terminal in the LimeWire folder and type sh runLime.sh

and WALLAH it goes

---

### Post by haaglin on 2005-06-20
ok. thanks, and this works with a non a64 computer?

---

