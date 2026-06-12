---
title: "Cocoon installation"
date: 2005-12-15
forum: General Help
---

### Post by ohzopants on 2005-12-15
I was recently forced into a hard drive format by harddrive problems and decided to switch from Ubuntu to Kubuntu.  So far so good though there were a few hitches with networking.

I have set up azureus to work properly and to pick up torrents automatically from a directory.  I have also enabled the statistics so that I can monitor my torrrents remotely (side note: along with an ftp server this setup  is a dream come true).  My apache installation works fine, but to parse the xml azureus stats I need to install cocoon, and that's where the problem is.

I can't get it to build.  I have a proper version of java installed but running the build.sh script yields:

Unable to locate tools.jar. Expected to find it in /usr/lib/j2re1.5-sun/lib/tools.jar
Buildfile: build.xml

init-tasks:
Compiling 5 source files to /media/Data/FirefoxDLs/cocoon-2.1.8/tools/anttasks

BUILD FAILED
/media/Data/FirefoxDLs/cocoon-2.1.8/tools/targets/init-build.xml:144: Unable to find a javac compiler;
com.sun.tools.javac.Main is not on the classpath.
Perhaps JAVA_HOME does not point to the JDK

Total time: 2 seconds

JAVA_HOME is currently set as: /usr/lib/j2re1.5-sun/  This is where my java actually is so I figure this should work.

Can anyone help me get cocoon to work? I don't care about it in general (don't even really know what it does), I just want to see my azureus stats.

Thanks,
Graham

---

### Post by mlomker on 2005-12-15
[QUOTE=ohzopants]
Unable to locate tools.jar. Expected to find it in /usr/lib/j2re1.5-sun/lib/tools.jar
Buildfile: build.xml
[/QUOTE]

I have j2re1.5 installed and that file isn't there.  It suspect that you need the SDK version, which includes more files (j2re is just runtime).

---

### Post by ohzopants on 2005-12-15
Thanks, that seems prety obvious in retrosprect.  Now I'm off to figure out I to tell Apache it's there.

---

