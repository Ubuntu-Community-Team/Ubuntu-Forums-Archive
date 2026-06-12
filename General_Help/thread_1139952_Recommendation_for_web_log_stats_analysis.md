---
title: "Recommendation for web log stats analysis?"
date: 2009-04-27
forum: General Help
---

### Post by ArduinoFun on 2009-04-27
I am new to Ubuntu. I have installed 9.04 and I am in need of a program that I can run from my desktop, where i can download my web server log file and be able to view the reports.

When I was using Windows XP, I used a program called Web Log Expert lite
[http://www.weblogexpert.com/](http://www.weblogexpert.com/)

I would like to find something like this that I run on my laptop and just download my server log file.

Everything I find seems to want to be installed on the server which I dont need. I just need the ability to use my log file and have a graphical display of the reports.

Any help is appreciated. I installed AWStats on Ubuntu, thinking this would let me do what I want. But I cant even find where it is to know how to run it or if it will do what I want.

---

### Post by kanikilu on 2009-04-27
You can use **gnome-system-log** to manually view your log files. Or, as you have already done, install something like awstats. I haven't used it in a long time, so a tutorial would probably do a better job of explaining it:

[http://ubuntu-tutorials.com/2008/01/16/configuring-awstats-on-ubuntu-server/](http://ubuntu-tutorials.com/2008/01/16/configuring-awstats-on-ubuntu-server/)

---

### Post by mcook2 on 2010-06-27
I understand Splunk is well featured, supports log analysis using almost any type of log data, not necessarily on your server, comes in 32-bit and 64 bit versions for Linux as well as Windows, FreeBSD, AIX, HP-UX, OSX 10.5 and 10.6.

They have .deb, .rpm and .tgz available for download at their web site and they offer a "free perpetual license" as well as for-fee versions.

I'm going to try it myself 'cos on Ubuntu 10.4 the gnome-system-log application, at least when monitoring my main Apache2 log, drives up to 97% CPU on both processors on my AMD 3800+ X2 running [uname -a] Linux [hostname] 2.6.32-22-generic #36-Ubuntu SMP Thu Jun 3 22:02:19 UTC 2010 i686 GNU/Linux (Unbuntu i386 Desktop 10.4 "Lucid Lynx").

I haven't tried Awstats yet myself, but I am checking out the link provided above. 

You can also use a spreadsheet program like gnumeric or OpenOffice for some things.

---

