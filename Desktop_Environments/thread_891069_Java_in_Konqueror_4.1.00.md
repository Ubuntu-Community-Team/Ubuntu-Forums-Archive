---
title: "Java in Konqueror 4.1.00?"
date: 2008-08-15
forum: Desktop Environments
---

### Post by russofris on 2008-08-15
Good afternoon,

I am having a bit of a difficult time getting java applets to open in Konqueror 4.1.0  (within the intrepid alpha3 amd64 release).  The result being that I never progress past the "applet loading" dialog.

I had a peek at [http://www.konqueror.org/javahowto/](http://www.konqueror.org/javahowto/) .  This provides simple instructions on getting java to work in konqueror.  Simply go to settings, java settings, and point to your preferred JVM.  Looking at my box, I have a couple to choose from.

frusso@H2SO4:/$ find . -name java                                             
./usr/lib/jvm/java-1.5.0-sun-1.5.0.16/bin/java                                
./usr/lib/jvm/java-1.5.0-sun-1.5.0.16/jre/bin/java                            
./usr/lib/jvm/java-6-openjdk/bin/java                                         
./usr/lib/jvm/java-6-openjdk/jre/bin/java                                     
./usr/lib/jvm/java-6-sun-1.6.0.07/bin/java                                    
./usr/lib/jvm/java-6-sun-1.6.0.07/jre/bin/java                                

all of them seem to work (tested with java -version).  the system JVM is currently java-6-openjdk.

So I go into konqueror, and examine the default path.  It is set to "java".  This results in no applets being shown.  I change this to /usr/lib/jvm/java-6-openjdk/jre/bin/java .  This seems to improve the situation.  I now have empty boxes with "applet loading" in them.  I try each of the 3 JVMs available to me with the same results (applet loading forever).

To test, I am trying the following two pages.
[http://www.java.com/en/download/help/testvm.xml](http://www.java.com/en/download/help/testvm.xml)
[http://www.javatester.org/index.htm](http://www.javatester.org/index.htm)
Both load successfully under Firefox.

I searched the launchpad bug DB, but was unable to find any relevant looking bugs.

[https://launchpad.net/+search?field.text=konqueror+java](https://launchpad.net/+search?field.text=konqueror+java)

Has anyone else tried to get Java working in Konqueror under Intreped?  What were your results?  If someone else can confirm on amd64, I will take the time to file a defect.

Thank you for your time,
Frank Russo

---

