---
title: "Java Lockups"
date: 2005-06-12
forum: Desktop Environments
---

### Post by dasunst3r on 2005-06-12
Whenever I try to launch NetBeans or Azureus, the JVM would eat the 239 MB or so of memory and will not show the GUI for any program I'm using.  I'm using Hoary with a Dell Inspiron 6000.  Has anybody faced the same problem?  Thanks!

---

### Post by haaglin on 2005-07-22
i have the same problem, none of my java apps is working, and java in firefox is realy slow, i just get the spinning logo, and after a while, it finaly loads. but none of my java apps is loading. Java is also making firefox hang sometimes. i have tried to completely remove java and all the java apps, and reinstalling. but it still doesn't work. Has anyone had this problem and got it fixed? or do i realy have to reinstall ubuntu?

---

### Post by Tichondrius on 2005-08-17
[QUOTE=haaglin]i have the same problem, none of my java apps is working, and java in firefox is realy slow, i just get the spinning logo, and after a while, it finaly loads. but none of my java apps is loading. Java is also making firefox hang sometimes. i have tried to completely remove java and all the java apps, and reinstalling. but it still doesn't work. Has anyone had this problem and got it fixed? or do i realy have to reinstall ubuntu?[/QUOTE]
 Yes I have the EXACT same problem - java is horrendously slow in firefox.  I installed the java package from the extra repositories  mentioned by ubuntuguide.org.   So I think maybe it's a bad version of java and will try to find another source for this package.

---

### Post by Tichondrius on 2005-08-18
[QUOTE=Tichondrius]Yes I have the EXACT same problem - java is horrendously slow in firefox.  I installed the java package from the extra repositories  mentioned by ubuntuguide.org.   So I think maybe it's a bad version of java and will try to find another source for this package.[/QUOTE]
 I found the problem - you need to create a link from the /etc/alternatives to the java plaugin. Use the command below, which works for the java SDK - you may need to modify the path to use j2re1.5-sun if you installed the java runtime environment instead of the full sdk :

$ sudo ln -sf /usr/lib/j2sdk1.5-sun/jre/plugin/i386/ns7/libjavaplugin_oji.so /etc/alternatives/firefox-javaplugin.so

---

