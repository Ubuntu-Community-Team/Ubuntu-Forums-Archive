---
title: "Java problem"
date: 2010-12-04
forum: Desktop Environments
---

### Post by Shabban on 2010-12-04
Hi I am doing an online registration that requires Fingerprinting but each time i want to load the page, it will says No Scanners connected. am using digitalpersona 4500. my java console shows this result

Java Plug-in 1.6.0_22
Using JRE version 1.6.0_22-b04 Java HotSpot(TM) Client VM
User home directory = C:\Users\Latifat

----------------------------------------------------
c:   clear console window
f:   finalize objects on finalization queue
g:   garbage collect
h:   display this help message
l:   dump classloader list
m:   print memory usage
o:   trigger logging
q:   hide console
r:   reload policy configuration
s:   dump system and deployment properties
t:   dump thread list
v:   dump thread stack
x:   clear classloader cache
0-5: set trace level to <n>
----------------------------------------------------

Applet Initialized
32Bit Machine Detected
java.lang.UnsatisfiedLinkError: no NLicensing in java.library.path
    at java.lang.ClassLoader.loadLibrary(Unknown Source)
    at java.lang.Runtime.loadLibrary0(Unknown Source)
    at java.lang.System.loadLibrary(Unknown Source)
    at com.neurotechnology.Library.NativeManager.loadDefault(NativeManager.java:15)
    at com.neurotechnology.Library.NetInstall.checkLoadDefault(NetInstall.java:33)
    at VeriFingerWebClient.VeriFingerWebClient.init(VeriFingerWebClient.java:129)
    at sun.plugin2.applet.Plugin2Manager$AppletExecutionRunnable.run(Unknown Source)
    at java.lang.Thread.run(Unknown Source)
default library not found
Loading - NCore.dll
C:\Users\Latifat\.neurotec\VeriFinger\NCore.dll
Loading - NLicensing.dll
C:\Users\Latifat\.neurotec\VeriFinger\NLicensing.dll
Loading - NImages.dll
C:\Users\Latifat\.neurotec\VeriFinger\NImages.dll
Loading - FPScannerMan.dll
C:\Users\Latifat\.neurotec\VeriFinger\FPScannerMan.dll
Loading - NTemplate.dll
C:\Users\Latifat\.neurotec\VeriFinger\NTemplate.dll
Loading - NFExtractor.dll
C:\Users\Latifat\.neurotec\VeriFinger\NFExtractor.dll
Loading - NMatcher.dll
C:\Users\Latifat\.neurotec\VeriFinger\NMatcher.dll
Loading - NCluster.dll
C:\Users\Latifat\.neurotec\VeriFinger\NCluster.dll
Loading - NeurotecJavaNative.dll
C:\Users\Latifat\.neurotec\VeriFinger\NeurotecJavaNative.dll
java.lang.Exception: Input/output error has occurred.
    at com.neurotechnology.NLicensing.NLicensing.nlicenseObtain(Native Method)
    at com.neurotechnology.NLicensing.NLicensing.licenseObtain(NLicensing.java:8)
    at VeriFingerWebClient.VeriFingerWebClient.init(VeriFingerWebClient.java:160)
    at sun.plugin2.applet.Plugin2Manager$AppletExecutionRunnable.run(Unknown Source)
    at java.lang.Thread.run(Unknown Source)
Loaded image: [http://www.jamb.org.ng/Unifiedtme/lthumb.gif](http://www.jamb.org.ng/Unifiedtme/lthumb.gif)
Loaded image: [http://www.jamb.org.ng/Unifiedtme/rthumb.gif](http://www.jamb.org.ng/Unifiedtme/rthumb.gif)
false
Obtaining license
Releasing license
No scanners conected
Releasing license

---

### Post by asmoore82 on 2010-12-04
Are you using [Microsoft Windows]("http://www.microsoft.com/windows/")??

This is a support forum for [Ubuntu]("http://www.ubuntu.com/") [Linux]("http://en.wikipedia.org/wiki/Linux").

We are a helpful lot, so you might still get a viable answer...

---

