---
title: "Frostwire (&amp; Limewire) no longer launches"
date: 2008-12-17
forum: General Help
---

### Post by utherpendragonfly on 2008-12-17
I have used Frostwire before with no problem, but now it will not launch. I've uninstalled and reinstalled the deb package, and tried Limewire too, but nothing works. I think this has happened since upgrading to Intrepid.
Any ideas what I can try?

---

### Post by taurus on 2008-12-17
Try running it from a terminal to see what's wrong with it.

Applications -> Accessories -> Terminal
```
frostwire
```

---

### Post by utherpendragonfly on 2008-12-17
Thanks for the advice. I ran limewire in terminal (I got rid of frostwire) and got this:

davey@davey-desktop:~$ limewire
Starting LimeWire...
Java exec found in PATH. Verifying...
Suitable java version found [java = 1.6.0_0]
Configuring environment...
Loading LimeWire:
java.lang.UnsatisfiedLinkError: Can't load library: /usr/lib/jvm/java-6-openjdk/jre/lib/i386/xawt/libmawt.so
	at java.lang.ClassLoader.loadLibrary(ClassLoader.java:1666)
	at java.lang.Runtime.load0(Runtime.java:787)
	at java.lang.System.load(System.java:1022)
	at java.lang.ClassLoader$NativeLibrary.load(Native Method)
	at java.lang.ClassLoader.loadLibrary0(ClassLoader.java:1767)
	at java.lang.ClassLoader.loadLibrary(ClassLoader.java:1684)
	at java.lang.Runtime.loadLibrary0(Runtime.java:840)
	at java.lang.System.loadLibrary(System.java:1047)
	at sun.security.action.LoadLibraryAction.run(LoadLibraryAction.java:67)
	at sun.security.action.LoadLibraryAction.run(LoadLibraryAction.java:47)
	at java.security.AccessController.doPrivileged(Native Method)
	at java.awt.Toolkit.loadLibraries(Toolkit.java:1610)
	at java.awt.Toolkit.<clinit>(Toolkit.java:1632)
	at com.limegroup.gnutella.gui.Main.showInitialSplash(Main.java:62)
	at com.limegroup.gnutella.gui.Main.main(Main.java:40)

******************************************************************
Something went wrong with LimeWire.
Maybe you're using the wrong version of Java?
(LimeWire is tested against and works best with with Sun's JRE, Java 1.5+)
The version of Java in your PATH is:
java version "1.6.0_0"
IcedTea6 1.3.1 (6b12-0ubuntu6) Runtime Environment (build 1.6.0_0-b12)
OpenJDK Client VM (build 1.6.0_0-b12, mixed mode, sharing)

I'm a little confused by what the problem might be, if I have a suitable version of Java. I also have Sun Java Control Panel installed, if that helps.

---

### Post by shane8002 on 2008-12-17
Make sure you have java installed.

---

### Post by taurus on 2008-12-17
Frostwire doesn't like the OpenJDK version.  It wants the Sun version.

```
sudo apt-get update
sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-plugin
```
When you get to the java licensing screen, press the Tab key to highlight the <OK> and then Return to accept it.  Once it's done, check to make sure you are using Sun.

```
java -version
frostwire
```

---

### Post by utherpendragonfly on 2008-12-18
I tried the above and got this:

davey@davey-desktop:~$ sudo apt-get update
[sudo] password for davey: 
Hit [http://ubuntu.mirror.frontiernet.net](http://ubuntu.mirror.frontiernet.net) intrepid Release.gpg
Ign [http://ubuntu.mirror.frontiernet.net](http://ubuntu.mirror.frontiernet.net) intrepid/main Translation-en_US       
Ign [http://ubuntu.mirror.frontiernet.net](http://ubuntu.mirror.frontiernet.net) intrepid/restricted Translation-en_US 
Ign [http://ubuntu.mirror.frontiernet.net](http://ubuntu.mirror.frontiernet.net) intrepid/multiverse Translation-en_US 
Ign [http://ubuntu.mirror.frontiernet.net](http://ubuntu.mirror.frontiernet.net) intrepid/universe Translation-en_US   
Get:1 [http://ubuntu.mirror.frontiernet.net](http://ubuntu.mirror.frontiernet.net) intrepid-updates Release.gpg [189B] 
Ign [http://ubuntu.mirror.frontiernet.net](http://ubuntu.mirror.frontiernet.net) intrepid-updates/main Translation-en_US
Ign [http://ubuntu.mirror.frontiernet.net](http://ubuntu.mirror.frontiernet.net) intrepid-updates/restricted Translation-en_US
Ign [http://ubuntu.mirror.frontiernet.net](http://ubuntu.mirror.frontiernet.net) intrepid-updates/multiverse Translation-en_US
Ign [http://ubuntu.mirror.frontiernet.net](http://ubuntu.mirror.frontiernet.net) intrepid-updates/universe Translation-en_US
Get:2 [http://ubuntu.mirror.frontiernet.net](http://ubuntu.mirror.frontiernet.net) intrepid-security Release.gpg [189B]
Ign [http://ubuntu.mirror.frontiernet.net](http://ubuntu.mirror.frontiernet.net) intrepid-security/main Translation-en_US
Ign [http://ubuntu.mirror.frontiernet.net](http://ubuntu.mirror.frontiernet.net) intrepid-security/restricted Translation-en_US
Ign [http://ubuntu.mirror.frontiernet.net](http://ubuntu.mirror.frontiernet.net) intrepid-security/multiverse Translation-en_US
Ign [http://ubuntu.mirror.frontiernet.net](http://ubuntu.mirror.frontiernet.net) intrepid-security/universe Translation-en_US
Hit [http://ubuntu.mirror.frontiernet.net](http://ubuntu.mirror.frontiernet.net) intrepid-backports Release.gpg        
Ign [http://ubuntu.mirror.frontiernet.net](http://ubuntu.mirror.frontiernet.net) intrepid-backports/restricted Translation-en_US
Ign [http://ubuntu.mirror.frontiernet.net](http://ubuntu.mirror.frontiernet.net) intrepid-backports/main Translation-en_US
Ign [http://ubuntu.mirror.frontiernet.net](http://ubuntu.mirror.frontiernet.net) intrepid-backports/multiverse Translation-en_US
Ign [http://ubuntu.mirror.frontiernet.net](http://ubuntu.mirror.frontiernet.net) intrepid-backports/universe Translation-en_US
Hit [http://ubuntu.mirror.frontiernet.net](http://ubuntu.mirror.frontiernet.net) intrepid Release                      
Get:3 [http://ubuntu.mirror.frontiernet.net](http://ubuntu.mirror.frontiernet.net) intrepid-updates Release [51.2kB]   
Ign [http://linux.getdropbox.com](http://linux.getdropbox.com) intrepid Release.gpg                           
Ign [http://linux.getdropbox.com](http://linux.getdropbox.com) intrepid/main Translation-en_US                
Get:4 [http://archive.canonical.com](http://archive.canonical.com) intrepid Release.gpg [189B]                 
Get:5 [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid Release.gpg [189B]                
Ign [http://linux.getdropbox.com](http://linux.getdropbox.com) intrepid Release                               
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release.gpg                                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Translation-en_US                      
Get:6 [http://ubuntu.mirror.frontiernet.net](http://ubuntu.mirror.frontiernet.net) intrepid-security Release [44.0kB]  
Ign [http://linux.getdropbox.com](http://linux.getdropbox.com) intrepid/main Packages                         
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release.gpg                              
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Translation-en_US                   
Hit [http://linux.getdropbox.com](http://linux.getdropbox.com) intrepid/main Packages                         
Hit [http://ubuntu.mirror.frontiernet.net](http://ubuntu.mirror.frontiernet.net) intrepid-backports Release            
Hit [http://ubuntu.mirror.frontiernet.net](http://ubuntu.mirror.frontiernet.net) intrepid/main Packages                
Hit [http://ubuntu.mirror.frontiernet.net](http://ubuntu.mirror.frontiernet.net) intrepid/restricted Packages          
Hit [http://ubuntu.mirror.frontiernet.net](http://ubuntu.mirror.frontiernet.net) intrepid/multiverse Packages          
Hit [http://ubuntu.mirror.frontiernet.net](http://ubuntu.mirror.frontiernet.net) intrepid/main Sources                 
Hit [http://ubuntu.mirror.frontiernet.net](http://ubuntu.mirror.frontiernet.net) intrepid/restricted Sources           
Hit [http://ubuntu.mirror.frontiernet.net](http://ubuntu.mirror.frontiernet.net) intrepid/universe Packages            
Get:7 [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release [27.6kB]                          
Hit [http://ubuntu.mirror.frontiernet.net](http://ubuntu.mirror.frontiernet.net) intrepid/universe Sources             
Get:8 [http://ubuntu.mirror.frontiernet.net](http://ubuntu.mirror.frontiernet.net) intrepid-updates/main Packages [256kB]
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid/free Translation-en_US              
Get:9 [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release [27.6kB]                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Packages                               
Ign [http://archive.canonical.com](http://archive.canonical.com) intrepid/partner Translation-en_US            
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid/non-free Translation-en_US       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Packages                          
Get:10 [http://archive.canonical.com](http://archive.canonical.com) intrepid Release [7007B]                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Packages                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Packages                            
Get:11 [http://ubuntu.mirror.frontiernet.net](http://ubuntu.mirror.frontiernet.net) intrepid-updates/restricted Packages [3861B]
Get:12 [http://ubuntu.mirror.frontiernet.net](http://ubuntu.mirror.frontiernet.net) intrepid-updates/multiverse Packages [1923B]
Get:13 [http://ubuntu.mirror.frontiernet.net](http://ubuntu.mirror.frontiernet.net) intrepid-updates/main Sources [80.1kB]
Get:14 [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid Release [11.7kB]                 
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid Release                             
Get:15 [http://ubuntu.mirror.frontiernet.net](http://ubuntu.mirror.frontiernet.net) intrepid-updates/restricted Sources [1169B]
Get:16 [http://ubuntu.mirror.frontiernet.net](http://ubuntu.mirror.frontiernet.net) intrepid-updates/universe Packages [31.5kB]
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid/free Packages                       
Get:17 [http://ubuntu.mirror.frontiernet.net](http://ubuntu.mirror.frontiernet.net) intrepid-updates/universe Sources [6412B]
Get:18 [http://ubuntu.mirror.frontiernet.net](http://ubuntu.mirror.frontiernet.net) intrepid-security/main Packages [38.2kB]
Get:19 [http://archive.canonical.com](http://archive.canonical.com) intrepid/partner Packages [906B]           
Get:20 [http://ubuntu.mirror.frontiernet.net](http://ubuntu.mirror.frontiernet.net) intrepid-security/restricted Packages [1785B]
Get:21 [http://ubuntu.mirror.frontiernet.net](http://ubuntu.mirror.frontiernet.net) intrepid-security/multiverse Packages [14B]
Get:22 [http://ubuntu.mirror.frontiernet.net](http://ubuntu.mirror.frontiernet.net) intrepid-security/main Sources [12.7kB]
Get:23 [http://ubuntu.mirror.frontiernet.net](http://ubuntu.mirror.frontiernet.net) intrepid-security/restricted Sources [571B]
Get:24 [http://ubuntu.mirror.frontiernet.net](http://ubuntu.mirror.frontiernet.net) intrepid-security/universe Packages [16.4kB]
Get:25 [http://ubuntu.mirror.frontiernet.net](http://ubuntu.mirror.frontiernet.net) intrepid-security/universe Sources [2429B]
Hit [http://ubuntu.mirror.frontiernet.net](http://ubuntu.mirror.frontiernet.net) intrepid-backports/restricted Packages
Hit [http://ubuntu.mirror.frontiernet.net](http://ubuntu.mirror.frontiernet.net) intrepid-backports/main Packages
Hit [http://ubuntu.mirror.frontiernet.net](http://ubuntu.mirror.frontiernet.net) intrepid-backports/multiverse Packages
Hit [http://ubuntu.mirror.frontiernet.net](http://ubuntu.mirror.frontiernet.net) intrepid-backports/universe Packages
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid/non-free Packages
Fetched 557kB in 2s (246kB/s)                      
Reading package lists... Done
W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
W: You may want to run apt-get update to correct these problems
davey@davey-desktop:~$ sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-pluginReading package lists... Done
Building dependency tree       
Reading state information... Done
sun-java6-bin is already the newest version.
sun-java6-bin set to manually installed.
sun-java6-jre is already the newest version.
sun-java6-jre set to manually installed.
sun-java6-plugin is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 11 not upgraded.

It seems like I need an older version of java for Limewire to work? And this part baffles me:
 
W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783

---

### Post by taurus on 2008-12-18
What is the output of this command?

```
sudo update-alternatives --config java
```

---

### Post by utherpendragonfly on 2008-12-18
davey@davey-desktop:~$ sudo update-alternatives --config java
[sudo] password for davey: 

There are 3 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
*+        1    /usr/lib/jvm/java-6-openjdk/jre/bin/java
          2    /usr/lib/jvm/java-6-cacao/jre/bin/java
          3    /usr/lib/jvm/java-6-sun/jre/bin/java

Press enter to keep the default[*], or type selection number: 3
Using '/usr/lib/jvm/java-6-sun/jre/bin/java' to provide 'java'.

It worked! I was just able to launch Limewire. Thank you!

---

