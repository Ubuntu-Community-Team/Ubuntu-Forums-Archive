---
title: "Tomcat and log4j: output defaults to syslog?"
date: 2009-02-16
forum: General Help
---

### Post by elmccarthy on 2009-02-16
Hi there,

I'm running Ubuntu server 8.04, with the latest apache-tomcat packages (version 5.5.25-5ubuntu).  The application I want to deploy uses log4j for logging.  I've added log4j-1.2.jar to /usr/share/tomcat5.5/common/lib and the logging facilities are working, except that all of the output from the root logger is going to syslog instead of the usual tomcat log file (which only contains messages about server startup and shutdown).

The output continues going to syslog even if I create my own log4j.properties in /usr/share/tomcat5.5/common/classes and try to explicitly send the output to a file somewhere.

It seems very much like there's _another_ log4j configuration file somewhere that's taking precedence, but I can't find one anywhere.  Has anyone seen this problem?  Has anyone solved this problem?  Can anyone else suggest other things for me to try?

Thanks,

Luke

---

### Post by elmccarthy on 2009-02-16
It turns out that /etc/init.d/tomcat5.5 runs tomcat using jsvc instead of the usual startup script that comes with the apache-tomcat distribution.  In /etc/init.d/tomcat5.5, stdout and stderr are explicitly redirected to the syslog.

As to why my log4j.properties wasn't changing things: apparently there was a log4j.properties hidden in the application I was trying to deploy and it was overriding the server-wide one.  While I was playing around trying to figure this out, I noticed that the webapp-specific log4j.properties file is used even when it lacks all the necessary information.  I.e.: webapp-specific log4j.properties does not inherit from server-wide log4j.properties.  I just assumed it would.

---

