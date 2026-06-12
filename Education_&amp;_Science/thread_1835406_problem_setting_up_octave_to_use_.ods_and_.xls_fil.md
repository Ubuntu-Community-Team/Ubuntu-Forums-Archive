---
title: "problem setting up octave to use .ods and .xls files through java"
date: 2011-08-29
forum: Education &amp; Science
---

### Post by malapradej on 2011-08-29
Hi,

I am relatively new to octave and linux and have been trying to set up octave to use commands like odsread or xlsread and others that will load and save spreadsheets into matrix variables. There is very little out there that gives a good step by step guide. The closest I got is summed up in my steps below although it is not 100% functional. I will appreciate if someone could help me over the last hurdle.

Download packages - io and java from [http://octave.sourceforge.net/packages.php](http://octave.sourceforge.net/packages.php)
type 'octave' in the terminal and in octave type the following: 

setenv("JAVA_HOME","/usr/lib/jvm/java-6-openjdk") - This should be the path to your jdk folder. 
s = javaObject('java.lang.String', 'Hello OctaveString') 

This should bring up the text 'Hello OctaveString'. Then you know its working. 

pkg install -verbose ~/Downloads/io-1.0.14.tar.gz - Assuming this is where you downloaded the io and java packages. 
pkg install -verbose ~/Downloads/java-1.2.8.tar.gz 
After typing 'pkg list' it should list the 2 packages 

I have added the following .jar files to a folder under my home folder called octave-  

jOpenDocument-1.2.jar, odfdom.jar,  odfdom-java-0.8.6.jar, xercesImpl.jar. I then added the following to  lines to a document called .octaverc under my home folder -  

  javaaddpath /home/malapradej/octave/jOpenDocument-1.2.jar 
  javaaddpath /home/malapradej/octave/odfdom-java-0.8.6.jar 
  javaaddpath /home/malapradej/octave/xercesImpl.jar 
  javaaddpath /home/malapradej/octave/odfdom.jar 

This should have added the class paths to octave on every startup. 

When I enter the following example of a file to read: 

 m = odsread('quizgrade.ods') 

I get the following error: 

 error: structure has no member `POI' 
>>>error: evaluating argument list element number 1 
error: called from: 
error:   /home/malapradej/octave/io-1.0.14/odsopen.m at line 328, column 3 
error:   /home/malapradej/octave/io-1.0.14/odsopen.m at line 148, column 19 
error:   /home/malapradej/octave/io-1.0.14/odsread.m at line 126, column 6

---

