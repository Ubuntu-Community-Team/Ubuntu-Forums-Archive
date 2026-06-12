---
title: "Help getting Java configured (installed, but where is it???)"
date: 2011-11-17
forum: Desktop Environments
---

### Post by Moozillaaa on 2011-11-17
ed. 3:
Java does not show in Tools/Add-ons/Plugins.
Help?

=====================

ed. 2:
Is Java a pop-up, that must be allowed for x website???

===========================

ed 1.:
Ok - installed from front end prompts, and back end prompts, restarted browser, restarted machine, and still no Java operation.

Anybody got any ideas here?

=================================

Title says it all; it's installed

chuck-04d0@chuck-04d0-laptop:~$ java -version
java version "1.5.0"
gij (GNU libgcj) version 4.4.3

Copyright (C) 2007 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.
chuck-04d0@chuck-04d0-laptop:~$ 

but I can't find it, to configure, or even 'enable' it in FF browser. 10.04, 3.6.22 FF

Help? Tools/Add-ons does not show it.

---

### Post by Moozillaaa on 2011-11-17
Ok - installed from front end prompts, and back end prompts, successfully (supposedly) restarted browser, restarted machine, and still no Java operation.

Anybody got any ideas here?

---

### Post by QDR06VV9 on 2011-11-18
Taken From here
[http://java.dzone.com/articles/sun-java-6-ubuntu-1004-1010](http://java.dzone.com/articles/sun-java-6-ubuntu-1004-1010)


Ubuntu 10.10
To install Sun's Java 6 JDK on Ubuntu 10.10, add the Sun Java6 Community PPA and install:

add-apt-repository ppa:sun-java-community-team/sun-java6
apt-get update
apt-get install sun-java6-jdk
update-java-alternatives -s java-6-sun

Ubuntu 10.04
To make Sun's Java 6 JDK available on Ubuntu 10.04 add the new repository like so:

add-apt-repository "deb [http://archive.canonical.com/](http://archive.canonical.com/) lucid partner"
aptitude update
aptitude install sun-java6-jdk
update-java-alternatives -s java-6-sun

From [http://christiansons.net/mike/blog/2010/07/sun-java-6-on-ubuntu-10-04-10-10-and-later/](http://christiansons.net/mike/blog/2010/07/sun-java-6-on-ubuntu-10-04-10-10-and-later/)


Or You could just enable the Canonicel Repos witch  is the smart way
and simply install "sun-java6-jdk"

---

### Post by Moozillaaa on 2011-11-18
Thanks... I'll post results shortly here

(watch for meltdown smoke - I'm near critical mass with this)

---

### Post by Moozillaaa on 2011-11-18
chuck-04d0@chuck-04d0-laptop:~$ exec sudo -s

[sudo] password for chuck-04d0: 

root@chuck-04d0-laptop:~# update-java-alternatives -s java-6-sun

update-alternatives: error: no alternatives for xulrunner-1.9-javaplugin.so.
update-alternatives: error: alternative /usr/lib/jvm/java-6-sun/jre/lib/amd64/libnpjp2.so for mozilla-javaplugin.so not registered, not setting.
update-alternatives: [COLOR=Red]**error: no alternatives for xulrunner-1.9-javaplugin.so.**[/COLOR]

root@chuck-04d0-laptop:~# 


[COLOR=Red]Mean anything?[/COLOR]

[COLOR=Red]**Googling now...**[/COLOR]

---

### Post by beaver29 on 2012-02-22
This won't be in time to help Moozillaaa but for the benefit of anyone else who may read this thread in the future:

I've always had problems installing Sun Java under Ubuntu.  The installation works fine but Firefox doesn't find the plugin.  (I don't know why Ubuntu software center and synaptic package manager don't take care of that detail...)

I have always had to manually tell Firefox where to find the Java plugin in the "libnpjp2.so" file. Instructions for doing this are in these threads:

[http://ubuntuforums.org/showthread.php?t=1905492](http://ubuntuforums.org/showthread.php?t=1905492)

[http://ubuntuforums.org/showthread.php?t=1896122](http://ubuntuforums.org/showthread.php?t=1896122)

[http://ubuntuforums.org/showthread.php?t=1899035](http://ubuntuforums.org/showthread.php?t=1899035)

hope this helps!

---

### Post by Moozillaaa on 2012-02-26
Yes, it might still help; I never got Java completely configured for my one specific task. I'll check it over.

---

