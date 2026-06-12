---
title: "Firefox java plugin problems"
date: 2009-06-12
forum: General Help
---

### Post by japher on 2009-06-12
I'm having problems viewing an applet in Firefox. I've read many posts on this forum that seem to have got me a little closer to my goal, but I'm still stuck with the "Start: applet not initialized" error when trying to access the applet.

I'm running 32-bit Firefox, with the Sun java plugin on Ubuntu 9.04. To get to this point I have run the following commands:
```

sudo apt-get install sun-java6-plugin
sudo update-alternatives --config java (selected the option to make sun jre my default)
sudo ln -s /usr/lib/jvm/java-6-sun-1.6.0.13/jre/plugin/i386/ns7/libjavaplugin_oji.so /home/joe/.mozilla/plugins/libjavaplugin_oji.so

```Now, when I visit [http://www.javatester.org/version.html](http://www.javatester.org/version.html) I get the java version shown as:
[FONT=Courier New][SIZE=2]Java Version 1.6.0_0 from Sun Microsystems Inc.[/SIZE][/FONT]

The signed applet here: [https://auth1.forsakringskassan.se/necs/bidlogon.jsp](https://auth1.forsakringskassan.se/necs/bidlogon.jsp) also seems to work (I get the java securty message pop-up, and when I accept this, the applet launches).

However I'm *still* unable to view the applet I need to use. Still getting the "Start: applet not initialized" error. I ran firefox from the console and checked the ouput after attempting to view the applet. This was the result:
```

net.sourceforge.jnlp.LaunchException: Fatal: Initialization Error: Could not initialize applet.
    at net.sourceforge.jnlp.Launcher.createApplet(Launcher.java:472)
    at net.sourceforge.jnlp.Launcher.getApplet(Launcher.java:418)
    at net.sourceforge.jnlp.Launcher$TgThread.run(Launcher.java:597)
Caused by: java.lang.NullPointerException
    at net.sourceforge.jnlp.Launcher.createApplet(Launcher.java:458)
    ... 2 more
Caused by: 
java.lang.NullPointerException
    at net.sourceforge.jnlp.Launcher.createApplet(Launcher.java:458)
    at net.sourceforge.jnlp.Launcher.getApplet(Launcher.java:418)
    at net.sourceforge.jnlp.Launcher$TgThread.run(Launcher.java:597)
java.lang.NullPointerException
    at net.sourceforge.jnlp.NetxPanel.runLoader(NetxPanel.java:102)
    at sun.applet.AppletPanel.run(AppletPanel.java:380)
    at java.lang.Thread.run(Thread.java:636)
java.lang.NullPointerException
    at sun.applet.AppletPanel.run(AppletPanel.java:430)
    at java.lang.Thread.run(Thread.java:636)

```Using this info, I was able to dig up this link via google:
[https://bugzilla.redhat.com/show_bug.cgi?id=477351](https://bugzilla.redhat.com/show_bug.cgi?id=477351)

That redhat bug shows someone with apparently exactly the same problem (some signed applets work, some don't). However I'm not sure what my next step should be to try and resolve this.

Can anyone help?

---

### Post by synapsys on 2009-06-12
Isn't there a package called firefox-java-plugin or something along those lines? If there is try installing that.....

---

### Post by japher on 2009-06-12
synapsys: No such package I'm afraid :D

I've finally got this solved though. I had tried to disable the Iced Tea plugin but obviously it was still interfering somehow. I removed both iced tea packages to fix my problems once and for all.

So, the complete list of commands I ran to get the sun java plugin working completely and correctly was:

```
sudo apt-get install sun-java6-plugin
sudo update-alternatives --config java (selected the option to make sun jre my default)
sudo ln -s /usr/lib/jvm/java-6-sun-1.6.0.13/jre/plugin/i386/ns7/libjavaplugin_oji.so /home/joe/.mozilla/plugins/libjavaplugin_oji.so
sudo apt-get remove icedtea-6-jre-cacao
sudo apt-get remove icedtea6-plugin
```

Not sure if the creation of the symlink is required or not, but it didn't hurt ;)

---

### Post by C. M .Hughes on 2009-06-28
japher, thank you so much for posting this. This has solved my Java issues which have had me grumpy all day.

In case you (or anyone else searching the forums) is interested, the IcedTea plugin was having difficulties with the Mathematical software Geogebra. 

After following these commands, it all works sweetly. 

Thanks again.

---

### Post by jdelgado on 2009-12-04
also solved my problem, thanks!

---

### Post by sdaau on 2010-06-09
Thanks - this worked for me in Lucid: 
```

$ sudo apt-get install sun-java6-plugin

$ sudo update-alternatives --config java 
There are 2 choices for the alternative java (providing /usr/bin/java).

  Selection    Path                                      Priority   Status
------------------------------------------------------------
* 0            /usr/lib/jvm/java-6-openjdk/jre/bin/java   1061      auto mode
  1            /usr/lib/jvm/java-6-openjdk/jre/bin/java   1061      manual mode
  2            /usr/lib/jvm/java-6-sun/jre/bin/java       63        manual mode

Press enter to keep the current choice[*], or type selection number: 2
update-alternatives: using /usr/lib/jvm/java-6-sun/jre/bin/java to provide /usr/bin/java (java) in manual mode.

$ sudo update-alternatives --config mozilla-javaplugin.so 
There are 2 choices for the alternative mozilla-javaplugin.so (providing /usr/lib/mozilla/plugins/libjavaplugin.so).

  Selection    Path                                                       Priority   Status
------------------------------------------------------------
* 0            /usr/lib/jvm/java-6-openjdk/jre/lib/i386/IcedTeaPlugin.so   1061      auto mode
  1            /usr/lib/jvm/java-6-openjdk/jre/lib/i386/IcedTeaPlugin.so   1061      manual mode
  2            /usr/lib/jvm/java-6-sun/jre/lib/i386/libnpjp2.so            63        manual mode

Press enter to keep the current choice[*], or type selection number: 2
update-alternatives: using /usr/lib/jvm/java-6-sun/jre/lib/i386/libnpjp2.so to provide /usr/lib/mozilla/plugins/libjavaplugin.so (mozilla-javaplugin.so) in manual mode.

```

Cheers!

---

### Post by craigster0 on 2010-06-19
I have a solution to the general problem of java not working in Firefox 3.6 that worked for me for Firefox 3.6.3 on Ubuntu Linux 10.04 (Lucid Lynx) 32 bit kernel.  For other flavors of Ubuntu or Linux you may or may not find some of the steps relevant.

The basic problem is that there's no compatible version of Java in the Firefox plugins directory.  Since Firefox 3.6 uses a new version of the Java Plugin API we need a compatible version of the Java library (see [http://www.java.com/en/download/faq/firefox_newplugin.xml](http://www.java.com/en/download/faq/firefox_newplugin.xml) for a description of the new Java API problem).

As near as I can tell, OpenJDK, which is preferred "Open Source" version of Java favored by Ubuntu developers, doesn't have the required interfaces, so Sun Java is required.  See the discussion of this issue as well as the solution proposed by kmb42vt (which is reproduced here) on this page: [http://www.zdnet.co.uk/blogs/jamies-random-musings-10006480/ubuntu-1004-lucid-lynx-and-java-10015534/](http://www.zdnet.co.uk/blogs/jamies-random-musings-10006480/ubuntu-1004-lucid-lynx-and-java-10015534/)

To fix this, perform the following steps:

1) go to System --> Administration --> Software Sources, and select the "Other Software" tab.  Drop down and check "http://archive.canonical.com/ubuntu lucid partner" and then click "Close".  Then click "reload" to accept the offer to reload the software sources.

2) go to System --> Administration --> Synaptic Package Manager, and enter "sun-java6" in the quick search box.  Drop down to sun-java6-plugin and mark it for installation.  It will drag in a batch of other software pacakges for a total of 103 Mbyte of software to install.  Click "Apply" to download the software.

That's it!  It was *not* necessary to symlink the java library into the Firefox plugins directory or run update-java-alternatives or update-alternatives.  After I installed the packages, Firefox 3.6.3 automatically picked up the right library, without even requiring me to restart Firefox.  I verified this by opening 'about: plugins' and my favorite app requiring java, Map of the Market.  I was also able to install and setup WebEx (which I needed).

You can try Map of the Market at: [http://www.smartmoney.com/map-of-the-market/?afl=yahoo](http://www.smartmoney.com/map-of-the-market/?afl=yahoo) or run a simple Java Tester at: [http://javatester.org/version.html](http://javatester.org/version.html)

Further info: I checked, and libjava* is not symlinked anywhere under /usr/lib/firefox* (which includes {firefox,firefox-3.6.3,firefox-addons).  It appears that Firefox auto-detected that a valid verison of java was available and picked it up.  (Note that the version of firefox I'm running is from a Ubuntu package, not straight from Mozilla, so it may have additional stuff added.)

(Note:  you can download and install Java directly from Sun from this page: [http://www.java.com/en/download/linux_manual.jsp?locale=en&host=www.java.com:80](http://www.java.com/en/download/linux_manual.jsp?locale=en&host=www.java.com:80) and then follow the manual installation instructions on this page: [http://java.sun.com/javase/6/webnotes/install/jre/manual-plugin-install-linux.html](http://java.sun.com/javase/6/webnotes/install/jre/manual-plugin-install-linux.html) If you do that, you probably want to use the package manager to remove OpenJDK and icedtea6-plugin first.  I haven't tried this approach since I prefer to use the package manager to keep track of software.) 

More info on my config:

Linux temp 2.6.32-21-generic #32-Ubuntu SMP Fri Apr 16 08:10:02 UTC 2010 i686 GNU/Linux
Mozilla Firefox for Ubuntu canonical - 1.0
Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.2.3) Gecko/20100423 Ubuntu/10.04 (lucid) Firefox/3.6.3

---

### Post by taz35 on 2010-09-06
In my case Java Plugin seems to be working on some sites but like a distinct Java applet wasn't popping up.
The browser stuck unless I went over what is suggested here.

> 
talha@cnl-4:/usr/java$ sudo apt-get install sun-java6-plugin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
sun-java6-plugin is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
talha@cnl-4:/usr/java$ sudo update-alternatives --config java
There are 2 choices for the alternative java (providing /usr/bin/java).

  Selection    Path                                      Priority   Status
------------------------------------------------------------
* 0            /usr/lib/jvm/java-6-openjdk/jre/bin/java   1061      auto mode
  1            /usr/lib/jvm/java-6-openjdk/jre/bin/java   1061      manual mode
  2            /usr/lib/jvm/java-6-sun/jre/bin/java       63        manual mode

Press enter to keep the current choice[*], or type selection number: 2
update-alternatives: using /usr/lib/jvm/java-6-sun/jre/bin/java to provide /usr/bin/java (java) in manual mode.
talha@cnl-4:/usr/java$ sudo apt-get remove icedtea-6-jre-cacao
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  icedtea-6-jre-cacao
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 877kB disk space will be freed.
Do you want to continue [Y/n]? 
(Reading database ... 304083 files and directories currently installed.)
Removing icedtea-6-jre-cacao ...
talha@cnl-4:/usr/java$ sudo apt-get remove icedtea6-plugin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  icedtea6-plugin
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 274kB disk space will be freed.
Do you want to continue [Y/n]? 
(Reading database ... 304075 files and directories currently installed.)
Removing icedtea6-plugin ...
talha@cnl-4:/usr/java$ 


---

### Post by xander98989 on 2010-09-23
Although many Java applets worked without problems, Geogebra applets were not working until I did this fix. Thank you!

---

### Post by Ron O on 2010-09-30
You guys are A number 1. 

I've been trying to get Java working for Oanda's currency trading platform for two years now without success. I kept getting "applet not initialized". Oanda tech support wanted the output from the Java terminal, and with Iced Tea there wasn't any. The thing that was perplexing was that many other Java applets were working fine, but not this one. Following your instructions, all works great.

I hated to replace open source software with proprietary Sun software, though. I hope they fix this incompatibility, but how will I know if they do?

---

### Post by SzSpain on 2010-10-12
> **japher said:**
> synapsys: No such package I'm afraid :D

I've finally got this solved though. I had tried to disable the Iced Tea plugin but obviously it was still interfering somehow. I removed both iced tea packages to fix my problems once and for all.

So, the complete list of commands I ran to get the sun java plugin working completely and correctly was:

```
sudo apt-get install sun-java6-plugin
sudo update-alternatives --config java (selected the option to make sun jre my default)
sudo ln -s /usr/lib/jvm/java-6-sun-1.6.0.13/jre/plugin/i386/ns7/libjavaplugin_oji.so /home/joe/.mozilla/plugins/libjavaplugin_oji.so
sudo apt-get remove icedtea-6-jre-cacao
sudo apt-get remove icedtea6-plugin
```

Not sure if the creation of the symlink is required or not, but it didn't hurt ;)


Hi Japher: I could hug you and kiss your feet!!! You solved my problem which cost me MANY hours ....next time I shall look in this forum from the very start!!
 Thanks again so much, now I got Geogebra running under Firefox.:):popcorn:

---

### Post by egidijus on 2010-10-29
I hate problems with java/icedtea on ubuntu. On karmic java applets  worked somehow with icedtea plugin. On lucid (10.04.1) all worked perfectly just out of the box (after installing ubuntu-restricted-extras). maverik - whatever I was doing - without success -- either icedtea or sun-java does't work correctly for me. Problem is, that applets in firefox does not close after game was finished and stay running all the time until I close firefox (or any other browser such as google chrome/chromium).
Look at [www.chess.lt]("http://www.chess.lt") click 'Play' and try to close applet... :(
Currently I use Java Version 1.6.0_22 from Sun Microsystems Inc.
Firefox 3.6.11

Any help would be appreciated.

Thanks

---

### Post by egidijus on 2010-11-01
Tired of solving the problem on 10.10, I've turned back to ubuntu 10.04 and with latest updates the problem persist now even with lucid :(. I think it happen when latest Ubuntu updates came.
I think it's ridiculous to use windows OS only for playing java games because ubuntu can't properly handle it.

any suggestions so far?...

---

### Post by gandaran on 2010-11-01
> **egidijus said:**
> Tired of solving the problem on 10.10, I've turned back to ubuntu 10.04 and with latest updates the problem persist now even with lucid :(. I think it happen when latest Ubuntu updates came.
I think it's ridiculous to use windows OS only for playing java games because ubuntu can't properly handle it.

any suggestions so far?...
you are doing something wrong in installing java!
sun-java works very well in linux just like in windows!
all you have to do is install sun-java6-plugin! (from the archive.canonical partner repository)
remove all openjdk-java and icedtea packages!
and don't make any java system links (unless you are installing java from sun-java website), it mite mess up you system!

---

### Post by egidijus on 2010-11-02
> **gandaran said:**
> you are doing something wrong in installing java!
sun-java works very well in linux just like in windows!
all you have to do is install sun-java6-plugin! (from the archive.canonical partner repository)
remove all openjdk-java and icedtea packages!
and don't make any java system links (unless you are installing java from sun-java website), it mite mess up you system!
 
Yes gandaran, I did everything you've suggested, maybe 10 times... I agree - sun-java6-plugin (from sun site or partner repos) works very well, but applets cannot be closed after game was completed. :(
Please look at [http://www.chess.lt/cgi_bin/default.asp?Lang=E](http://www.chess.lt/cgi_bin/default.asp?Lang=E)[]("http://www.chess.lt/") and click <play!> link and try close the applet...

---

### Post by egidijus on 2010-11-06
Any solution please! :( I can't believe there isn't any... or should I better report a problem to launchpad?

---

### Post by egidijus on 2010-11-20
So no suggestions as I understand, no any idea what to do... indeed its very sad to realise that I should use WinOS for playing chess. ](*,)

---

### Post by jbeiter on 2013-01-30
anyone have a version of this fix for ubuntu 12.10? Tried to retrace the steps but it doesn't work. Can't seem to find any versions of java that fit this bill.

---

### Post by oldos2er on 2013-01-30
Old thread closed, please start a new thread.

---

