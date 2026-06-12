---
title: "Specifying java to the main menu"
date: 2012-11-28
forum: Desktop Environments
---

### Post by stephaneeybert on 2012-11-28
Hello,

I have an application in the directory /home/stephane/programs/springsource/sts-3.1.0.RELEASE that requires java, in order to start up.

I can start the application fine from the command line:
```
stephane@stephane-ThinkPad-X61s:~> /home/stephane/programs/springsource/sts-3.1.0.RELEASE/STS

```

But when I try to start it from the main menu of Lubuntu 12.10 the application does not start and complains it cannot find any java. Here is the popup message it shows:
> A Java Runtime Environment (JRE) or Java Development Kit (JDK)
must be available in order to run STS. No Java virtual machine
was found after searching the following locations:
/home/stephane/programs/springsource/sts-3.1.0.RELEASE/jre/bin/java
java in your current PATH


Here is the menu entry in the .local/share/applications/sts.desktop file:
[Desktop Entry]
Type=Application
Name=STS
Comment=Spring Source Tools Suite
Icon=/home/stephane/programs/springsource/sts-3.1.0.RELEASE/configuration/org.eclipse.osgi/bundles/941/1/.cp/sts32.png
Exec=/home/stephane/programs/springsource/sts-3.1.0.RELEASE/STS
Terminal=false
Categories=Development;IDE;Java;

It used to work from the main manu but not anymore since I removed the java installed in the system. I want to use the java that is installed under my user home directory /home/stephane/programs/jdk1.6.0_37 and not any /usr/bin/java...

How can I tell the desktop environment to use my java ?

---

### Post by stephaneeybert on 2012-11-28
The java and other path informations were specified in a .bashrc file, but this file is read after the desktop environment is launched.

Instead I moved these java and other path informations into a .profile file which is read before the desktop environment is launched.

Now the application can be started from the main menu fine.

---

