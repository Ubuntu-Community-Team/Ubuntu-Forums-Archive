---
title: "Netlogo and java"
date: 2006-01-12
forum: General Help
---

### Post by phidippus on 2006-01-12
I'm trying to run Netlogo, but I get some errors. I installed JRE from SUN, but it did not fix the problem.

$ java -jar NetLogo.jar
Exception in thread "main" java.awt.AWTError: Cannot load AWT toolkit: gnu.java.awt.peer.gtk.GtkToolkit
   at ._ZN4java4lang11VMThrowable16fillInStackTraceEPNS0_9ThrowableE (/usr/lib/libgcj.so.6.0.0)
   at ._ZN4java4lang9Throwable16fillInStackTraceEv (/usr/lib/libgcj.so.6.0.0)
   at ._ZN4java4lang9ThrowableC1EPNS0_6StringE (/usr/lib/libgcj.so.6.0.0)
   at ._ZN4java4lang5ErrorC1EPNS0_6StringE (/usr/lib/libgcj.so.6.0.0)
   at ._ZN4java3awt8AWTErrorC1EPNS_4lang6StringE (/usr/lib/libgcj.so.6.0.0)
   at ._ZN4java3awt7Toolkit17getDefaultToolkitEv (/usr/lib/libgcj.so.6.0.0)
   at ._ZN4java3awt19GraphicsEnvironment27getLocalGraphicsEnvironmentEv (/usr/lib/libgcj.so.6.0.0)
   at ._ZN4java3awt6WindowC1EPS1_PNS0_21GraphicsConfigurationE (/usr/lib/libgcj.so.6.0.0)
   at ._ZN4java3awt6WindowC1EPNS0_5FrameE (/usr/lib/libgcj.so.6.0.0)
   at ._ZN5javax5swing7JWindowC1Ev (/usr/lib/libgcj.so.6.0.0)
   at org.nlogo.app.Splash.beginSplash() (Unknown Source)
   at ._ZN16_Jv_InterpMethod9run_classEP7ffi_cifPvP7ffi_rawS2_ (/usr/lib/libgcj.so.6.0.0)
   at org.nlogo.app.App.main(java.lang.String[]) (Unknown Source)
   at ._ZN16_Jv_InterpMethod9run_classEP7ffi_cifPvP7ffi_rawS2_ (/usr/lib/libgcj.so.6.0.0)
   at ._ZN3gnu4java4lang10MainThread9call_mainEv (/usr/lib/libgcj.so.6.0.0)
   at ._ZN3gnu4java4lang10MainThread3runEv (/usr/lib/libgcj.so.6.0.0)
   at ._Z13_Jv_ThreadRunPN4java4lang6ThreadE (/usr/lib/libgcj.so.6.0.0)
   at ._Z11_Jv_RunMainP14_Jv_VMInitArgsPN4java4lang5ClassEPKciPS6_b (/usr/lib/libgcj.so.6.0.0)
   at .main (/usr/lib/libgij.so.6.0.0)
   at .__libc_start_main (/lib/tls/i686/cmov/libc-2.3.5.so)
Caused by: java.lang.ClassNotFoundException: gnu.java.awt.peer.gtk.GtkToolkit not found in gnu.gcj.runtime.SystemClassLoader{urls=[file:NetLogo.jar,file:./], parent=gnu.gcj.runtime.ExtensionClassLoader{urls=[], parent=null}}
   at ._ZN4java4lang11VMThrowable16fillInStackTraceEPNS0_9ThrowableE (/usr/lib/libgcj.so.6.0.0)
   at ._ZN4java4lang9Throwable16fillInStackTraceEv (/usr/lib/libgcj.so.6.0.0)
   at ._ZN4java4lang9ThrowableC1EPNS0_6StringE (/usr/lib/libgcj.so.6.0.0)
   at ._ZN4java4lang9ThrowableC1EPNS0_6StringEPS1_ (/usr/lib/libgcj.so.6.0.0)
   at ._ZN4java4lang9ExceptionC1EPNS0_6StringEPNS0_9ThrowableE (/usr/lib/libgcj.so.6.0.0)
   at ._ZN4java4lang22ClassNotFoundExceptionC1EPNS0_6StringEPNS0_9ThrowableE (/usr/lib/libgcj.so.6.0.0)
   at ._ZN4java4lang22ClassNotFoundExceptionC1EPNS0_6StringE (/usr/lib/libgcj.so.6.0.0)
   at ._ZN4java3net14URLClassLoader9findClassEPNS_4lang6StringE (/usr/lib/libgcj.so.6.0.0)
   at ._ZN4java4lang11ClassLoader9loadClassEPNS0_6StringEb (/usr/lib/libgcj.so.6.0.0)
   at ._ZN4java4lang11ClassLoader9loadClassEPNS0_6StringE (/usr/lib/libgcj.so.6.0.0)
   at ._Z13_Jv_FindClassP13_Jv_Utf8ConstPN4java4lang11ClassLoaderE (/usr/lib/libgcj.so.6.0.0)
   at ._ZN4java4lang5Class7forNameEPNS0_6StringEbPNS0_11ClassLoaderE (/usr/lib/libgcj.so.6.0.0)
   at ._ZN4java4lang5Class7forNameEPNS0_6StringE (/usr/lib/libgcj.so.6.0.0)
   ...15 more

---

### Post by Sepht on 2006-01-12
it's because your install isn't using JRE.. it's using gcj runtime.... change the symlink (I think it's in /usr/bin )

---

### Post by phidippus on 2006-01-12
Installing J2SE from SUN and using SUN's java fixed it.

---

### Post by limako on 2006-02-15
Any suggestions for someone using powerpc (ubuntu breezy badger)?  I'm getting the same error, but Sun doesn't provide a runtime for that architecture.

---

### Post by habalo on 2008-01-16
hi 

does any one know how to count the number of turtles when I load the image?

The following lines are examples of my code.

to import-image

ca
let file user-file
if file = false [ stop ]
;; imports image into patches
import-pcolors file
;; generates a white border around the image to avoid wrapping
;; converts the square grid to an hex grid
makes-initial-box

;; transfers the image to the turtles. Rounds the color values to be integers.
ask turtles 
  [
   set color round ([pcolor] of patch-here)
   set heading color   
  ]
  

;; erases the patches (sets their color back to black),
;; except the border patches, which will remain white

ask patches [if border? != true
               [
                set pcolor black
               ]
            ]

end

---

