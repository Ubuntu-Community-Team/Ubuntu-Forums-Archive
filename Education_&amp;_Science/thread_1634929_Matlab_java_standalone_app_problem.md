---
title: "Matlab java standalone app problem"
date: 2010-12-01
forum: Education &amp; Science
---

### Post by Taros07 on 2010-12-01
I am trying to run some Java code in Eclipse which uses code that has been build by Matlab using the Matlab Builder JA.

However, when trying to run in Eclipse I get the following error:

Exception in thread "main" java.lang.UnsatisfiedLinkError: Failed to find the library libmwmclmcrrt.so.7.14, required by MATLAB Builder JA, on java.library.path.

```
Exception in thread "main" java.lang.UnsatisfiedLinkError: Failed to find the library libmwmclmcrrt.so.7.14, required by MATLAB Builder JA, on java.library.path.
 This library is typically installed along with MATLAB or the MCR, its absence may indicate an issue with that installation or the current path configuration.
The MCR version that this component is trying to use is: 7.14.

    at com.mathworks.toolbox.javabuilder.internal.MCRConfiguration$ProxyLibraryDir.get(MCRConfiguration.java:167)
    at com.mathworks.toolbox.javabuilder.internal.MCRConfiguration$ProxyLibraryDir.<clinit>(MCRConfiguration.java:173)
    at com.mathworks.toolbox.javabuilder.internal.MCRConfiguration.getProxyLibraryDir(MCRConfiguration.java:178)
    at com.mathworks.toolbox.javabuilder.internal.MCRConfiguration$MCRRoot.get(MCRConfiguration.java:77)
    at com.mathworks.toolbox.javabuilder.internal.MCRConfiguration$MCRRoot.<clinit>(MCRConfiguration.java:87)
    at com.mathworks.toolbox.javabuilder.internal.MCRConfiguration.getMCRRoot(MCRConfiguration.java:92)
    at com.mathworks.toolbox.javabuilder.internal.MCRConfiguration$ModuleDir.<clinit>(MCRConfiguration.java:66)
    at com.mathworks.toolbox.javabuilder.internal.MCRConfiguration.getModuleDir(MCRConfiguration.java:71)
    at com.mathworks.toolbox.javabuilder.internal.MWMCR.<clinit>(MWMCR.java:1553)

```I have been trying to implement to settings at [http://www.mathworks.com/help/toolbox/compiler/bqrw460-1.html](http://www.mathworks.com/help/toolbox/compiler/bqrw460-1.html), but these don't seem to work.

Does anybody have experience with getting this up and running?

Additional info:
Ubuntu 10.04 LTS x64
Matlab R2010b (no MCR installed - I tried and this doesn't help)
Eclipse Version: 3.5.2 from repositories

Thanks in advance!

---

### Post by Taros07 on 2010-12-01
The problem seems to lie in defining LD_LIBRARY_PATH (see mathworks'  link in first post).

However, then I run into issues described here: [https://edge.launchpad.net/ubuntu/+bug/366728](https://edge.launchpad.net/ubuntu/+bug/366728)

Still working on it, if anybody has suggestions....

---

### Post by Taros07 on 2010-12-01
Setting the variables in Eclipse itself fixes the problem for running the code from Eclipse (strange that Mathworks doesn't mention that). However, for standalone code, my question remains the same.

---

### Post by tkoWD on 2010-12-12
Same problem here..cannot seem to find the solution!

I exported the path correctly but it keeps on giving that exception...

```
Exception in thread "AWT-EventQueue-0" java.lang.UnsatisfiedLinkError: Failed to find the library libmwmclmcrrt.so.7.14, required by MATLAB Builder JA, on java.library.path.
```

---

### Post by koddistortion on 2011-02-08
I had the same problem (but on a Windows system) and fixed it. 
Several things to consider:
 - What version of MatLab do you use? 32bit or 64bit?
 - What version of Java do you use in order to interact with MatLab? 32bit or 64bit?

Getting your described error message only appeared to me, when I was using Windows 64bit, MatLab 64bit (compiled some MatLab scripts) and trying to use Java 32bit to access these.. 

Maybe this helps..

---

### Post by znutar on 2011-05-19
Hello I'm dealing with the same issue on Ubuntu 10.04 64-bits.


```
org.apache.jasper.JasperException: javax.servlet.ServletException: java.lang.UnsatisfiedLinkError: Failed to find the library libmwmclmcrrt.so.7.15, required by MATLAB Builder JA, on java.library.path.
 This library is typically installed along with MATLAB or the MCR, its absence may indicate an issue with that installation or the current path configuration.
The MCR version that this component is trying to use is: 7.15.
```


Using matlab 2011a with MCR 7.15


echo $LD_LIBRARY_PATH
/opt/MATLAB/v715/runtime/glnxa64:/opt/MATLAB/v715/bin/glnxa64:/opt/MATLAB/v715/sys/os/glnxa64:/opt/MATLAB/v715/sys/java/jre/glnxa64/jre/lib/amd64/native_threads:/opt/MATLAB/v715/sys/java/jre/glnxa64/jre/lib/amd64/server:/opt/MATLAB/v715/sys/java/jre/glnxa64/jre/lib/amd64/client:/opt/MATLAB/v715/sys/java/jre/glnxa64/jre/lib/amd64:/opt/MATLAB/v715/toolbox/javabuilder/jar/
root@dev:/# 

Please help !

---

### Post by cbanbury on 2011-07-25
Bump 

Same problem using matlab 2011a. Have tried 32/64 bit versions on lucid/maverick with no joy. 

Have set netbeans/eclipse to use sun-java-6 & same for MATLAB using 
setenv (from within MATLAB) - I think this is needed but still stuck

---

### Post by cbanbury on 2011-07-26
Adding them LD_LIBRARY_PATH directly in Eclipse worked. Thanks! 

I didn't know how to set this up in eclipse so see: 

[http://www.desy.de/~cholewa/eclipse/eclipseLdLibraryPath.html](http://www.desy.de/~cholewa/eclipse/eclipseLdLibraryPath.html)

---

