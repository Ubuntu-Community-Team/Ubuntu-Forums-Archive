---
title: "difference between /etc/init.d/tomcat6 start and $CATALINA_HOME/bin/startup.sh"
date: 2009-05-21
forum: General Help
---

### Post by michaelrepucci on 2009-05-21
Hi fellow Ubuntu'ers,

I'm pretty new to Ubuntu (9.04) and Tomcat (6 via Synaptic Package Manager), and I've come across an interesting little bug that I don't understand. I was wondering if anyone out there may have seen this issue, or have insight as to why it is occurring.

When I installed Tomcat, the package installed various startup/shutdown scripts into /etc/tomcat6 and /etc/init.d/tomcat6. Running these scripts spawns 3 processes (see [http://ubuntuforums.org/showthread.php?t=1165023](http://ubuntuforums.org/showthread.php?t=1165023)), and Tomcat runs fine, including the manager and example apps. However, a custom app provided by my colleague fails.

This app runs fine on multiple other systems, and will run fine on my system as well if I use $CATALINA_HOME/bin/startup.sh to start Tomcat instead. So what is the difference between the package startup scripts, and those under $CATALINA_HOME/bin? Any why do the package maintainers (presumably) believe their scripts to be a preferred way to run Tomcat (i.e., what am I losing by using $CATALINA_HOME/bin/startup.sh)?

I'm not so concerned about making my custom app work, since this is just a local install for development purposes. I'm more curious to understand the difference between the various startup/shutdown scripts as they related to Ubuntu packages and Tomcat operation and functionality. But just in case you were curious, the error I get with my custom app when running using the /etc/init.d/tomcat6 script says something about a parsing error in {my app}/WEB-INF/web.xml.

Thanks in advance for any insight!

:) Michael

---

