---
title: "Open Office &amp; Frostwire Stopped Working, Need to downgrade Java."
date: 2008-12-17
forum: General Help
---

### Post by xrecar on 2008-12-17
Hello everyone, hope you're having a nice time.
I wonder If I'm the only one with this problem and I don't really know where to post, so any information is greatly appreciated.

Today I came up to open a document (.docx) on OpenOffice's Word processor, however after putting up a dialog about document recovery it never launched. Ok, I pass on that because it wasn't a very important thing. Next thing is that frostwire has stopped working too, so I'm guessing that since OO is from sun it uses java in some point and that's why as well frostwire is not working. I'm not a 100% sure so please correct me if I'm wrong.

also this is the output that came from frostwire (Notice the last message):

```
Starting FrostWire...          
Java exec found in PATH. Verifying...
Suitable java version found [java = 1.6.0_0]
Configuring environment...                  
Loading FrostWire:                          
CLASSPATH SET TO: :./log4j.jar:./clink.jar:./ProgressTabs.jar:./looks.jar:./httpcore-niossl-4.0-alpha7.jar:./themes.jar:./jaudiotagger.jar:./commons-logging.jar:./jl.jar:./jflac.jar:./mp3spi.jar:./httpcore-nio-4.0-beta2.jar:./foxtrot.jar:./jcraft.jar:./onion-common.jar:./daap.jar:./commons-codec-1.3.jar:./forms.jar:./jorbis.jar:./httpclient-4.0-alpha3.jar:./onion-fec.jar:./junit.jar:./jdic.jar:./tritonus.jar:./httpcore-4.0-beta2.jar:./gettext-commons.jar:./vorbisspi.jar:./guice-1.0.jar:./lw-all.jar:./messages.jar:./icu4j.jar:./jmdns.jar:./FrostWire.jar:./jdic_stub.jar:./aopalliance.jar:./jogg.jar:./jython.jar
java.lang.UnsatisfiedLinkError: Can't load library: /usr/lib/jvm/java-6-cacao/jre/lib/amd64/xawt/libmawt.so
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
        at com.limegroup.gnutella.gui.Main.showInitialSplash(Unknown Source)
        at com.limegroup.gnutella.gui.Main.main(Unknown Source)


******************************************************************
Something went wrong with FrostWire.
Maybe you're using the wrong version of Java?
(FrostWire is tested against and works best with with Sun's JRE, Java 1.4+)
The version of Java in your PATH is:
java version "1.6.0_0"
IcedTea6 1.3.1 (6b12-0ubuntu5) Runtime Environment (build 1.6.0_0-b12)
CACAO (build 0.99.3+hg, compiled mode)
```

So.. should I remove java and go back to 1.4 or something?

**PS: **I have been searching the forums and I've found a topic that addresses the OOo3 issue, I wilt try it. However that's only for OOo3 and I need the solution for frostwire. 


**UPDATE 1:**
Removing the openoffice.org-kde package works quite well.
Now all I Need is Frostwire and wait till they fix that package (openoffice.org-kde)

**UPDATE 2:** Frostwire does not work on Gnome nor KDE, just switched to verify.

**UPDATE 3:** Solved the frostwire issue by installing the ubuntu restricted extras pack

---

### Post by jamesstansell on 2008-12-17
For frostwire try

```

$ sudo aptitude install sun-java6-jre
$ sudo update-java-alternatives java-6-sun

```

Because you appear to be running in 64-bit mode you should probably also visit the 64-bit forum.  In particular there is a sticky thread about java that may interest you.

---

### Post by xrecar on 2008-12-17
Thanks. Even though I solved it by installing the ubuntu restricted extras, the problem IS java as you're suggesting =D

So Many, Many Thanks :)

---

