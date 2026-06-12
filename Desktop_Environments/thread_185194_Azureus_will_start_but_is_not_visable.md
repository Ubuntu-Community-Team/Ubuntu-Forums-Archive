---
title: "Azureus will start but is not visable"
date: 2006-05-31
forum: Desktop Environments
---

### Post by clarke.rainey on 2006-05-31
Without doing any updates, my azureus appears to have seriously messed itself up... my X restarted for some reason today and when I tried to open Azureus up again I got a little popup saying that it did not tidily shutdown, but the popup will not go away and after the splash screen for Azureus, the program will not show itself, it just sits in the background hidden... I just tried uninstalling and reinstalling and I have the official Sun 1.5 SDK... if anyone has any ideas that would be wonderful...

---

### Post by santiagozky on 2006-05-31
I have the same problem, azureus starts fine, but if I minimize it, it will disappear but keep runing. the log doesnt show anything interesting

---

### Post by Gustavo on 2006-06-01
Take a look and see if it helps:

[https://wiki.ubuntu.com/RestrictedFormats?highlight=%28restricted%29#head-6acdf8655644645c067fb9e965a66be38681b7fb](https://wiki.ubuntu.com/RestrictedFormats?highlight=%28restricted%29#head-6acdf8655644645c067fb9e965a66be38681b7fb)

---

### Post by Travisty on 2006-06-01
I found that Azureus has been hosed since one of the beta upgrades a while back. The Java changed and hasn't worked since. The only work around that I have found was to instal the Linux version of Java. This fixed all of my problems except for Azureus. I figured it was a small price to pay to have Java working. I too would love to find an answer to this problem. As I am now using the linux official BT client and really miss Azureus.

---

### Post by bjc on 2006-06-02
[QUOTE=clarke.rainey]Without doing any updates, my azureus appears to have seriously messed itself up... my X restarted for some reason today and when I tried to open Azureus up again I got a little popup saying that it did not tidily shutdown, but the popup will not go away and after the splash screen for Azureus, the program will not show itself, it just sits in the background hidden... I just tried uninstalling and reinstalling and I have the official Sun 1.5 SDK... if anyone has any ideas that would be wonderful...[/QUOTE]

Yeah, there are a couple of problems with the Azureus package. You can fix most of them by installing Sun's Java instead. Try something like this:
```

sudo apt-get install sun-java5-jre
sudo update-alternatives --config java

```
Then select the ' /usr/lib/jvm/java-1.5.0-sun/jre/bin/java' option (probably number 3). This only remaining problem seems to be the zombie error popup about the untidy shutdown, which you can solve by either upgrading Azureus manually, or waiting for the Ubuntu package to be synced with upstream.

---

### Post by vulpes76 on 2006-06-03
I was having the exact same problem, i'd installed the sun jre 1.5 and was getting pretty frustrated with no gui and the message down the bottom right. used the second like above to make sun java default and it seems to be working perfectly now.

---

### Post by JGKC9AYC on 2006-06-03
I installed Azureus through the "Add/Remove" programs.  I thought I already had Java installed.
When Azureus started, it asked what language & I selected it.  It then asked me to choose between beginner, intermediate & expert.  I chose beginner & clicked next.  It then disappeared.  I tried twice more & it did the same thing so I uninstalled it.
Ideas?  Suggestions?
Thanks.

---

### Post by bjc on 2006-06-03
I'd install it again with Sun's Java, as explained above. If that still doesn't work, download [http://prdownloads.sourceforge.net/azureus/Azureus2.4.0.2.jar?download](http://prdownloads.sourceforge.net/azureus/Azureus2.4.0.2.jar?download) and copy it to */usr/share/java/Azureus2.jar*. (If you haven't used Azureus before, consider deleting you profile directory as well (*~/.azureus*).

---

### Post by Ocxic on 2006-06-03
I have found that the tray icon for azurues doesn't apper, but ther is a small 1 pixel spot where you could click to get axureus up. when you open azureus watch the tray closely if you see something move it's there just search for it, or open azureus again and the main windows will apper.

---

### Post by ariel on 2006-06-03
Unfortunately the official Ubuntu 6.06 release shipped with a flawed azureus. Getting it to work again is now that difficult.

First you need to install Sun's Java 1.5. At the end, you can verify the installation doing 

       java -version 

Then you will need the latest azureus cvs:

[http://azureus.sourceforge.net/index_CVS.php](http://azureus.sourceforge.net/index_CVS.php)

because the official version has problems in dapper/sun java (you can't close the little notification windows).

You can unpack the tar in /opt/azureus, then replace the /usr/bin/azureus script with a link pointing to /opt/azureus/azureus.

This did the trick for me. Hope this helps.

---

### Post by zukakog on 2006-06-03
[QUOTE=bjc]Yeah, there are a couple of problems with the Azureus package. You can fix most of them by installing Sun's Java instead. Try something like this:
```

sudo apt-get install sun-java5-jre
sudo update-alternatives --config java

```
Then select the ' /usr/lib/jvm/java-1.5.0-sun/jre/bin/java' option (probably number 3). This only remaining problem seems to be the zombie error popup about the untidy shutdown, which you can solve by either upgrading Azureus manually, or waiting for the Ubuntu package to be synced with upstream.[/QUOTE]

I did this, but it didn't help with the pop-up messages, or the icon missing from the system tray.

I also downloaded the new Azureus2.jar from their main site.  It works great ***except*** for this wierd box in the bottom corner.
[IMG]http://kogenterprises.com/public/a.jpg[/IMG]
It stays on top of everything.  Any ideas?

---

### Post by JGKC9AYC on 2006-06-04
[QUOTE=ariel]Unfortunately the official Ubuntu 6.06 release shipped with a flawed azureus. Getting it to work again is now that difficult.

First you need to install Sun's Java 1.5. At the end, you can verify the installation doing 

       java -version 

Then you will need the latest azureus cvs:

[http://azureus.sourceforge.net/index_CVS.php](http://azureus.sourceforge.net/index_CVS.php)

because the official version has problems in dapper/sun java (you can't close the little notification windows).

You can unpack the tar in /opt/azureus, then replace the /usr/bin/azureus script with a link pointing to /opt/azureus/azureus.

This did the trick for me. Hope this helps.[/QUOTE]

Ok...I downloaded that file from the link you provided, created an "/opt/azureus" directory & extracted the file into it, however, there's no "azureus" in the /opt/azureus folder.  This is what I got with the "ls" command:

Azureus2403-B36.jar  build  com  dist  edu  META-INF  org

I'm also not sure of what you mean by "replacing the /usr/bin/azureus script with a link pointing to /opt/azureus/azureus."  Could you elaborate, please?
Thanks!

---

### Post by ariel on 2006-06-08
[quote=JGKC9AYC]Ok...I downloaded that file from the link you provided, created an "/opt/azureus" directory & extracted the file into it, however, there's no "azureus" in the /opt/azureus folder.  This is what I got with the "ls" command:

Azureus2403-B36.jar  build  com  dist  edu  META-INF  org

I'm also not sure of what you mean by "replacing the /usr/bin/azureus script with a link pointing to /opt/azureus/azureus."  Could you elaborate, please?
Thanks![/quote] 
As of late I'm using an easier method. Just rename the .jar you downloaded to "Azureus2.jar", then  

    cd /usr/share/java
    sudo mv Azureus2.jar Azureus2.jar.original

Then move the jar you downloaded to /usr/share/java, effectively replacing the original one. In case you want to roll back, just use the backup created in the "mv" step.

This one is easier than replacing the original script and you don't risk losing any functionality provided by that script.

---

