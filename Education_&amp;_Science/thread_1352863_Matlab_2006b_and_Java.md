---
title: "Matlab 2006b and Java"
date: 2009-12-12
forum: Education &amp; Science
---

### Post by cpgos on 2009-12-12
Does anybody know the Java requirements of Matlab.

I have installed Matlab 2006b on an ASUS netbook, running Ubuntu 9.10, without generating any error messages but when I run Matlab all I get, after the usual splash screen showing the version number, is a blank grey box that does not allow for any user interaction. 

It seems that this problem is something to do with Java, however when I try to update several Java dependencies are not available. Could somebody briefly outline which are the essential Java packages for Matlab?

Best regards,
cpgos

---

### Post by nateperson on 2009-12-13
I don't really know, but are you running open Java that comes standard with Ubuntu or the most current sun version?  Cause that most likely will cause issues.

Follow this [https://help.ubuntu.com/community/Java]("https://help.ubuntu.com/community/Java") to install and configure Java and I'd suggest to make sure you also install the JDK.  

I installed 2009b the other day and 10 or so different toolkits and have had no issues with it or any of them, but I also had the Sun 6 JDK installed and working before Matlab, but other than that I didn't really have anything special going on.

---

### Post by cpgos on 2009-12-15
Thank you for your response, which has led to Matlab now being operational.

It seems to me that you are right and that the current Sun version of Java is required. Initially, the standard open version was installed; however when I changed to the Sun version the full Matlab desktop now opens.

The commands that I executed in a terminal window and my understanding of them are as follows:

sudo update-java-alternatives -l [This displays the current java default.]

sudo update-java-alternatives -s java-6-sun [This updates to sun java 6.]

export MATLAB_JAVA=/usr/lib/jvm/java-6-sun-1.6.0.16/jre && [This is to do with creating a variable called MATLAB_JAVA???]

/usr/local/matlab73/etc/lmstart [This starts the license manager.]

/usr/local/matlab73/bin/matlab -desktop [This starts Matlab.]

Best regards,
cpgos

---

### Post by nateperson on 2009-12-16
> export MATLAB_JAVA=/usr/lib/jvm/java-6-sun-1.6.0.16/jre && [This is to do with creating a variable called MATLAB_JAVA???]

Correct, it creates an environmental variable, but it only works for your current session.  So unless your going to want to run multiple versions of java with matlab, I'd suggest you place it in your .bashrc file in your home directory that way it will automatically create itself at the start of each session.

---

### Post by cpgos on 2009-12-28
Thank you for your response and my apologies for not responding before now.

I have added the "EXPORT_MATLAB..." command to the start of the matlab launch file directly after the first line "#!/bin/sh". The matlab launch file being /usr/local/matlab73/bin/matlab. Also this suggestion was found in the thread called "Matlab R2006b on Ubuntu 7.10".

In addition, to avoid having to enter the full path to the license manager and the matlab launcher each time I have created symbolic links to both in /usr/local/bin.

The commands used to create the symbolic links to the license manager and the matlab launcher respectively follow below :

sudo ln -s /usr/local/matlab73/etc/lmstart
sudo ln -s /usr/local/matlab73/bin/matlab

A directory listing of /usr/local/bin now shows two cyan coloured files, lmstart and matlab.

Best regards,
cpgos

---

