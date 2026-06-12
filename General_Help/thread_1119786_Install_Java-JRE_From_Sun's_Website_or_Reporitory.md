---
title: "Install Java-JRE From Sun's Website or Reporitory?"
date: 2009-04-08
forum: General Help
---

### Post by umechanism on 2009-04-08
The program jLog is a Amateur Radio logging program that runs in a Java-JRE environment.  I have Java installed but the installation fails.  The jLog website [http://jlog.org/](http://jlog.org/) instructs me to download the Java Runtime Environment from Sun's website located here [http://java.sun.com/javase/downloads/index.jsp](http://java.sun.com/javase/downloads/index.jsp)

What is the difference between Sun's version of Java and the "sun-java6-jre" program found in the repository?  Which one should I install?

---

### Post by mikewhatever on 2009-04-08
What does 'the installation fails' mean? Do you get any error messages? If you do, please post the exact text.

---

### Post by umechanism on 2009-04-08
Well, the installation of the program may not have failed but when I launch the program it fails to launch and provides me with lots of error messages (see attached image of those error messages).

Now, the jLog program's website does instruct that Java JRE has to be installed and that its location must be part of the PATH so that jLog can find it when launched.  I may actually have two issues:
[LIST=1]
[*]Which version of JRE to install (from Sun's website or the repository).
[*]Setting the PATH so that jLog knows where JRE is located.
[/LIST]

Thank you for the help.

---

### Post by mikewhatever on 2009-04-08
I think version 6 is a good one to go with, also check the link below on how to configure java.
[https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)

---

### Post by umechanism on 2009-04-08
> **mikewhatever said:**
> I think version 6 is a good one to go with, also check the link below on how to configure java.
[https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)

Thanks but do you mean version six from the repository?

Also, I have already gone through Sun's installation steps for downloading and installing Java-JRE from their website.  Should I decide to use the Java in the repository, how do I uninstall the version I downloaded from Sun's website?  I initially downloaded and installed Sun's version from a folder I created in my home directory.

Thanks!

---

### Post by mikewhatever on 2009-04-08
I don't think it matters whether you install it from the repositories or Sun's website. The one from Sun tends to be newer, but I've never installed it in Ubuntu and have no idea how to rermove it.

---

### Post by umechanism on 2009-04-09
I decided to use the Java from the repository and it seems it is installed correctly.  However, this jLog program will not run.  Would it be too much of a bother to ask you to download jLog yourself and see if you can get it to run then relay your knowledge to me?

I'm sorry to ask but desperation and sleep deprivation tends to break me.

---

### Post by mikewhatever on 2009-04-09
I've got it installed and tried running, but get the same string under details. Not sure what's the deal.

---

### Post by txcrackers on 2009-04-09
You're missing a JAR (Java ARchive) file - specifically one that provides serial-port I/O. It's known as "rxtx" - check the installation instructions very carefully or ask them for help in getting it going. The JRE is working just fine - your installation is a little off.

---

### Post by mikewhatever on 2009-04-09
The instructions for that part are as follows:

>    4. The next steps are only necessary if you are going to connect a radio or keyer and you have not already installed these files when installing Java.
       
   5. Download 'RXTXcomm.jar' and install it in the 'lib/ext' folder of the Java VM (e.g. for RH9 with Sun's Java 1.6.0_04: '/usr/java/j2re1.6.0_04/lib/ext').
       
   6. If you are upgrading from V 3.x or V4 Beta 2 (i.e. from an older version of RXTX), please remove the file 'librxtxSerial-2.1-x.so' in the '/lib/386' folder (or equivalent).
       
   7. Please download 'librxtxSerial.so' and install it in the 'lib/i386' folder of the Java VM (e.g. for RH9 or FC4 with Sun's Java 1.6.0_04 it will be '/usr/java/j2re1.6.0_04/lib/ext'). If the 'lib/i386' folder is nonexistent, place it in 'bin' or another Java VM folder containing '.so' files.
       
   8. Important: Log in as root and add your jLog <user> to the group owning the '/var/lock' directory and to the group owning the serial port (e.g. /dev/ttyS0) to be used. This would typically (e.g. Red Hat 9) be users 'lock' and 'uucp' respectively. Try running jLog as root if you experience problems.
       
   9. To increase log capacity beyond 30000 entries per file, you must change the Java VM properties.
       
  10. Note that the default UTF-8 environment in  SuSE V 9+ must be changed to e.g. ISO-8859-1. See changing charset.



I'd didn't follow them through because it is stated that the steps are optional, and because I don't even have a serial port. Go figure.

---

### Post by umechanism on 2009-04-09
I'm going to download that serial port control file and give it a try but where the instructions say, **"Download 'RXTXcomm.jar' and install it in the 'lib/ext' folder of the Java VM (e.g. for RH9 with Sun's Java 1.6.0_04: '/usr/java/j2re1.6.0_04/lib/ext'). "**
Where would this file be placed in Ubuntu?  I'm not seeing a "lib/ext" location.

I really appreciate your help.

---

### Post by mikewhatever on 2009-04-10
It looks like with the current version, the path is as follows:
/usr/lib/jvm/java-6-sun-1.6.0.10/jre/lib/ext

---

### Post by umechanism on 2009-04-10
I got the program working last night.  I downloaded the Sun-Java-6 version from the repos then decided to NOT to allow the jLog program to select its version of Java.  I manually browsed to the same location you just posted (stopping at the /jvm directory) and the program seems to be working.  It does tell me that there seems to be a permission issue with some of the files I installed but I think I can work through those.  If not, I may be bugging you again.

Thank you for the help.

---

