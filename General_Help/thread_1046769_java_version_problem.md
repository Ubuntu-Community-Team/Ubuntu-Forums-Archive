---
title: "java version problem"
date: 2009-01-21
forum: General Help
---

### Post by Fugazi66 on 2009-01-21
I go to a website that has problems with java 1.6.0_10 so I need to upgrade to 1.6.0_11

I followed the directions on this ( [http://jmtdstoc.blogspot.com/2008/12/ubuntu-810-sun-java-16011-and-firefox.html](http://jmtdstoc.blogspot.com/2008/12/ubuntu-810-sun-java-16011-and-firefox.html) ) site. It looks like I got it all right...

when I type java -version I get..

java version "1.6.0_11"
Java(TM) SE Runtime Environment (build 1.6.0_11-b03)
Java HotSpot(TM) Server VM (build 11.0-b16, mixed mode)

But when I test my java version at ( [http://javatester.org/version.html](http://javatester.org/version.html) ), it says I'm still on _10

I have the libjavaplugin_oji.so linked to the /usr/bin/firefox-3.0.5/plugins directory.

I can't figure out what I'm missing.

Thanks in advance

---

### Post by ajmorris on 2009-01-22
hi there,
that is telling us what JRE version your os is using. However, i can only assume that your firefox is not using that version, as when you checked it on the internet, it returned the older version. What version is being specified in about:plugins  ?

Also, did you uninstall the jre version from the ubuntu repos before you installed the new version?



AJ

---

