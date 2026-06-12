---
title: "MATLAB 2011a Student installation issues on 11.04"
date: 2011-05-26
forum: Education &amp; Science
---

### Post by ada-m on 2011-05-26
I'm hoping someone can help me out. I've had a lot of trouble with installation.  A few weeks ago I was trying to do it without JRE and had few issues.  

Yesterday I tried again using JRE, and the download_agent file provided by MATLAB.  When I click on the graphical link the installer opens up like normal and I quickly get an Invalid XML Format that states "There was an error while connecting to the server. Consult the FAQ on the MathWorks Web site for more information."

I was unable to find any info on the site and as I am not all that experienced with Linux, trying to pick all of this stuff up on the fly, I am completely lost.  If anybody can help me out or at least point me in the right direction I would really appreciate it.

Thank you,
Adam

---

### Post by ada-m on 2011-05-27
I'm assuming its a JRE issue because when I run the JRE check on Oracle's site (FF and Chrome), it states that its not found.  When I right click on the installer I have the option to run JRE 6. 

Real confused. =|

---

### Post by ada-m on 2011-05-28
Solution:
[http://ubuntuforums.org/showthread.php?t=1769418](http://ubuntuforums.org/showthread.php?t=1769418)

---

### Post by devangel77b on 2011-09-26
The links in the other Ubuntu forum page are broken.  What are the steps necessary to fix JRE and allow Matlab 2011a to run in Ubuntu 11.04?  I think I run into the same problem as the original poster - Matlab installs but in trying to run it fails to find the correct Java.  I installed Sun JRE 6 from the ppa but still can't get Matlab to find it.  

Going to switch to python.

---

### Post by ada-m on 2012-02-07
Sorry for the dead link.  Its probably to late for the human above but I hope this helps someone in the future:

Method 1

Install openjdk using the following command from your terminal

sudo apt-get install openjdk-7-jre

Install Java for browser – firefox/chrome..

For running applets in your web browsers such as Mozilla Firefox or Google Chrome, you need to install icedtea plugin. Execute the following command from your terminal

sudo apt-get install icedtea6-plugin

Method 2

Install Oracle JRE Using PPA

Open the terminal and run the following commands

sudo add-apt-repository ppa:ferramroberto/java
sudo apt-get update
sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts

--- via ubuntugeek.com

---

### Post by kayeswahid on 2012-02-12
Is it possible to have an APC UPS management tool or with Network Ups Tool (NUT) to connect to a server through cables or USB and notify other computer on the network and shut down their devices? What are the possible issues when performing this setup?

For additional help you can see here <a href="http://www.techyv.com/questions/matlab-installation-error-ubuntu-1104">                                                                                               [Matlab installation error on Ubuntu 11.04]("http://www.techyv.com/questions/matlab-installation-error-ubuntu-1104")
</a>

---

