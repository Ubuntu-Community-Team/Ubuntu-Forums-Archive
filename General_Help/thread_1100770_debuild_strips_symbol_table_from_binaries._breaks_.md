---
title: "debuild strips symbol table from binaries. breaks jmap"
date: 2009-03-19
forum: General Help
---

### Post by gmoore777 on 2009-03-19
FYI:

So, at work, we take perfectly good downloads, for example,
Java SDK 1.5.0 update 15 and debianize it so that the local
development groups only gets the Java from our local repository.
It allows us to tweak/customize the package.

debuild will strip all the binaries.
Normally this is desired, but not for Java, specifically
the `jmap` tool. (possibly others.)

You will want to comment out the call to `dh_strip` in 
debian/rules file, otherwise you may see errors like this:

$ jmap -heap 19466

Attaching to process ID 19466, please wait...
sun.jvm.hotspot.debugger.NoSuchSymbolException: Could not find symbol "gHotSpotVMTypeEntryTypeNameOffset" 
in any of the known library names (libjvm.so, libjvm_g.so, gamma_g)
*********** at sun.jvm.hotspot.HotSpotTypeDataBase.lookupInProcess(HotSpotTypeDataBase.java:400)
*********** at sun.jvm.hotspot.HotSpotTypeDataBase.getLongValueFromProcess(HotSpotTypeDataBase.java:381)
*********** at sun.jvm.hotspot.HotSpotTypeDataBase.readVMTypes(HotSpotTypeDataBase.java:86)
*********** at sun.jvm.hotspot.HotSpotTypeDataBase.<init>(HotSpotTypeDataBase.java:68)
*********** at sun.jvm.hotspot.bugspot.BugSpotAgent.setupVM(BugSpotAgent.java:550)
*********** at sun.jvm.hotspot.bugspot.BugSpotAgent.go(BugSpotAgent.java:476)
*********** at sun.jvm.hotspot.bugspot.BugSpotAgent.attach(BugSpotAgent.java:314)
*********** at sun.jvm.hotspot.tools.Tool.start(Tool.java:146)
*********** at sun.jvm.hotspot.tools.JMap.main(JMap.java:126)
Debugger attached successfully.
jmap requires a java VM process/core!
$

[Note: the libjvm.so file in update  1.5.0 update15 which holds the symbol of  gHotSpotVMTypeEntryTypeNameOffset
was stripped of its symbol table by debian process dh_strip. jmap evidently depends on this symbol table.
]

---

### Post by realflash on 2009-05-08
Thanks very much - saved me a lot of time.

The quick resolution is to use a JRE installed by hand, not from a system debian package.

---

