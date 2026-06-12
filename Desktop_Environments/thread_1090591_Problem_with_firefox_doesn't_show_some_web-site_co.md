---
title: "Problem with firefox: doesn't show some web-site contents"
date: 2009-03-08
forum: Desktop Environments
---

### Post by munishvit on 2009-03-08
**[B]*[COLOR="Blue"]Check post #7 for solution[/COLOR]***[/B]
Hello friends,
On my Ubuntu 8.04, I am using Firefox 3.0.7. My browser doesn't show some of the website contents, but IE (in windows XP) doesn't create any such problem. 
As an example you may check the following site:
[http://www.kotaksecurities.com/news/EquityHome.htm](http://www.kotaksecurities.com/news/EquityHome.htm)
at right-hand site type SATYAMCOMP (or DLF, ICICIBANK or any other script name). Then at top of the page you will find link "STOCK CHART" (in caps and in blue). Now the coming page should display a graph (End of the day, or intraday), that is not visible under my browser.
Following packages are already installed:
> munish@lappy:~$ java -version
java version "1.6.0_0"
OpenJDK  Runtime Environment (build 1.6.0_0-b11)
OpenJDK Client VM (build 1.6.0_0-b11, mixed mode, sharing)
From Add/Remove...I installed:
Sun Java 6 Runtime
OpenJDK Java Runtime
Sun Java 6.0 Plugin
Icedtea Java Plugin
MonoDevelop

Any help will be highly appreciated, [COLOR="DarkGreen"]any least you can check with your browser and tell the status[/COLOR].

**Edit: You may check the following sites also**
[http://www.bseindia.com/price_finder/price_vol.asp?scripcd=532868&scripname=DLF%20LTD*](http://www.bseindia.com/price_finder/price_vol.asp?scripcd=532868&scripname=DLF%20LTD*)

---

### Post by lindsay7 on 2009-03-08
I saw lots of posts last night about the latest update of ff having problems, by the way the web site you listed will not open with Opera either.

---

### Post by Committed on 2009-03-08
Ok I just tried the link with both Firefox and Opera and it worked fine.  Tried my Scottrade account streaming qoutes as well and still works.  Do you have Java and javascript enabled in edit/preferences/content in firefox?

---

### Post by munishvit on 2009-03-08
> **Committed said:**
> Ok I just tried the link with both Firefox and Opera and it worked fine.  Tried my Scottrade account streaming qoutes as well and still works.  Do you have Java and javascript enabled in edit/preferences/content in firefox?

Ya both are enabled. Thanks for your efforts.
I guess, it could be because of some hardware issues. Following are the specifications: 
-----------------------------------------------------
Compaq Presario Compaq M2512AU (EV879PA)
Processor: AMD Mobile Sempron (1.8GHz)
RAM: 256+512 DDR1
Graphics: ATI Radeon Xpress 200M 
-----------------------------------------------------

---

### Post by munishvit on 2009-03-09
> **Committed said:**
> Ok I just tried the link with both Firefox and Opera and it worked fine.  Tried my Scottrade account streaming qoutes as well and still works.  Do you have Java and javascript enabled in edit/preferences/content in firefox?

Could you please tell me what softwares have you installed (related to browser)?

---

### Post by munishvit on 2009-03-10
I need you help guys...:o

---

### Post by Committed on 2009-03-10
Ok, I went through this as well, here's what I did. 


Before you begin, you need to ensure that your repositories are up to date by issuing the following:
**sudo apt-get update**



If you are developing Java applications, you will require Java Development Kit (JDK), on the other hand if you just require Java to run Java applications, then you need just Java Runtime Environment (JRE). For the former, the command is as follows:
sudo apt-get install sun-java6-jdk sun-java6-plugin

For JRE:
**sudo apt-get install sun-java6-jre sun-java6-plugin**

Once either one is done, run the sudo update-java-alternatives -s java-6-sun command and finally add the line &#8220;/usr/lib/jvm/java-6-sun&#8221; to the top of the /etc/jvm file (gksudo gedit /etc/jvm). Save and exit. To test your Java(TM) setup in the terminal type:-

java -version



If you get an output like below, then you are done!

java version &#8220;1.6.0&#8243; Java(TM) SE Runtime Environment (build 1.6.0-b105) Java HotSpot(TM) Client VM (build 1.6.0-b105, mixed mode, sharing)


Or for me brought me to:
Configuring sun-java6-jre

SUN MICRO SYSTEMS IS WILLING TO LICENCE THE HAVE PLATFORM STANDARD ADDITION DEVELOP KIT TO YOU ONLY UPON..........ACCEPTING TERMS..........

Tab to accept and hit enter to install.

---

### Post by bearslumber on 2009-03-10
Hi

I had the same problem. I found a solution by installing the sun-java-plugin for browsers. The JRE does not install the plugin for firefox.

I used synaptec package manager, but you can do the same using sudo aptget.

Check out the following link.

[http://ubuntuforums.org/showthread.php?t=1081819&highlight=sun+java+environment]("http://ubuntuforums.org/showthread.php?t=1081819&highlight=sun+java+environment").

Hope this resolves the problem.

Regards

Mr Bear

---

### Post by munishvit on 2009-03-11
> **bearslumber said:**
> Hi
I had the same problem. I found a solution by installing the sun-java-plugin for browsers. The JRE does not install the plugin for firefox.
I used synaptec package manager, but you can do the same using sudo aptget.
Mr Bear

buddy i hv already installed:
   Sun Java 6.0 Plugin
   Icedtea Java Plugin
even then its not working.

---

### Post by stardusk on 2009-03-11
Sorry to hijack this thread, but I am having the same problem. When I try to install sun-java6-plugin in the terminal I get this message:

Package sun-java6-plugin is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package sun-java6-plugin has no installation candidate

I already have all the java packages installed, and when I try to start a java applet in Firefox, it takes forever (i.e., it says "Applet Started", but never starts).

---

### Post by munishvit on 2009-03-12
> **Committed said:**
> Ok, I went through this as well, here's what I did. 


Before you begin, you need to ensure that your repositories are up to date by issuing the following:
**sudo apt-get update**


Thanks for your reply, I'll try these instructions and tell you.

---

### Post by munishvit on 2009-03-12
> **Committed said:**
> sudo apt-get install sun-java6-jre sun-java6-plugin

sudo update-java-alternatives -s java-6-sun

add the line “/usr/lib/jvm/java-6-sun” to the top of the /etc/jvm file (gksudo gedit /etc/jvm)

To test your Java(TM) setup in the terminal type:-
java -version
If you get an output like below, then you are done!
java version “1.6.0&#8243; Java(TM) SE Runtime Environment (build 1.6.0-b105) Java HotSpot(TM) Client VM (build 1.6.0-b105, mixed mode, sharing)


Thanks, its working :D:D:D

---

### Post by linusr on 2010-01-19
doesn't work for me, tried re-installing sun-java6-jre,sun-java6-pugin

java version "1.6.0_15"
Java(TM) SE Runtime Environment (build 1.6.0_15-b03)
Java HotSpot(TM) Server VM (build 14.1-b02, mixed mode)

any ideas?

---

