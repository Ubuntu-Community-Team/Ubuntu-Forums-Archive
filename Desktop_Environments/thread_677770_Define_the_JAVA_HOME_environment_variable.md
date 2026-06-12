---
title: "Define the JAVA_HOME environment variable"
date: 2008-01-25
forum: Desktop Environments
---

### Post by tchayya on 2008-01-25
Hi,
when i enter the command ./startup.sh (for intalio server) i receive the following message 
Neither the JAVA_HOME nor the JRE_HOME environment variable is defined
At least one of these environment variable is needed to run this program
could you please help me how to define it?
Regards :confused:

---

### Post by kpkeerthi on 2008-01-25
1. Make sure you have JRE/JDK installed
```
java -version
``` should print the version

2. Get the path to JDK/JRE install folder. For instance, if you have jdk1.5 installed, it would be /usr/lib/jvm/java-1.5.0-sun.

3. At the command prompt, type 
```
export JAVA_HOME=/usr/lib/jvm/java-1.5.0-sun
```

4. Now try running ./startup.sh.

If it works, add the export command to .bashrc file in your HOME folder to export JAVA_HOME everytime you open a terminal (bash).

---

### Post by tchayya on 2008-01-25
Thank you it's helpfull & it's running
:popcorn:

---

### Post by TomDaBomb2u on 2008-04-17
> **kpkeerthi said:**
> 1. Make sure you have JRE/JDK installed
```
java -version
``` should print the version

2. Get the path to JDK/JRE install folder. For instance, if you have jdk1.5 installed, it would be /usr/lib/jvm/java-1.5.0-sun.

3. At the command prompt, type 
```
export JAVA_HOME=/usr/lib/jvm/java-1.5.0-sun
```

4. Now try running ./startup.sh.

If it works, add the export command to .bashrc file in your HOME folder to export JAVA_HOME everytime you open a terminal (bash).

Hello, I've tried this same procedure in Hardy, and it works while the terminal window is open, but when close the terminal then reopen, echo $JAVA_HOME returns a blank line. It appears that my environment variable is not being saved. 

Any suggestions?

-Thomas

---

### Post by andrewc6l on 2008-04-17
Have you added the export line to your ~/.bashrc (assuming you're using bash)? If so, it should be set when you open a new Terminal. (It won't be set in any existing terminal sessions, only when you open a new one.)

The fact that you don't see it when you open a new terminal makes me suspect something's wrong with ~/.bashrc - maybe a typo?

---

