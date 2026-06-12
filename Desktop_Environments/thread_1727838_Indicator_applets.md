---
title: "Indicator applets"
date: 2011-04-13
forum: Desktop Environments
---

### Post by vicke4 on 2011-04-13
I'm new to Linux and Ubuntu 10.10.i googled for adding more indicator applets.i followed the steps they gave.but not working.please tell me how to add more indicator applet in Ubuntu 10.10?

---

### Post by ankspo71 on 2011-04-13
Hi,
Indicator applets are very new to Ubuntu (and linux in general). These are what are going to be used to replace the traditional way of accessing application icons from the notification area. Unfortunately, it will take a while before more indicator applets become available, because the developers of the applications will need some time to make them. 

I do know where to find some though and that is over at the omgubuntu site. Here are the search results of Indicator Applet at omgubuntu:
[http://www.omgubuntu.co.uk/?s=indicator+applet](http://www.omgubuntu.co.uk/?s=indicator+applet)
Scroll through each page and you will find indicator applets for weather, RSS feeds, email, system monitoring, battery status, twitter, and more.

The OMG! Ubuntu! Guide to the best indicator applets around:
[http://www.omgubuntu.co.uk/2011/01/the-omg-guide-to-must-have-indicator-applets/](http://www.omgubuntu.co.uk/2011/01/the-omg-guide-to-must-have-indicator-applets/)

How to add more apps to the Ubuntu Messaging Menu
[http://www.omgubuntu.co.uk/2010/10/how-to-add-more-apps-to-the-ubuntu-messaging-menu/](http://www.omgubuntu.co.uk/2010/10/how-to-add-more-apps-to-the-ubuntu-messaging-menu/)

happy hunting :) PS: they also go by the name of app-indicators too.

---

### Post by vicke4 on 2011-04-13
hey i downloaded a indicator applet named ejjecter0.4.2.tar.bz2 from launchpad.please tell me how to install it?

---

### Post by ankspo71 on 2011-04-13
Hi,
The one you downloaded needs to be compiled and installed manually because it is a source code package. You can do this if you like, and the instructions are in the file named "install" inside the the package, but there is also a PPA repository available that contains a newer version of ejecter (currently version 0.4.4) for Ubuntu 10.10 and 10.04. 

The PPA Repository installation method:
[http://www.omgubuntu.co.uk/2011/01/ejector-tray-app-adds-indicator-applet-support/](http://www.omgubuntu.co.uk/2011/01/ejector-tray-app-adds-indicator-applet-support/)

The instructions are fairly easy. All you would need to do open your terminal and enter the two commands they gave, one line at a time.
   
```
sudo add-apt-repository ppa:fredp/ppa
sudo apt-get update && sudo apt-get install ejecter
```

The next time you restart or Log into Ubuntu, the ejector icon should automatically start.

By the way, PPA's (Personal Package Archives) are additional repositories that you can add to your "Software Sources" to install additional software on Ubuntu. 

Some of the PPA repositories contain experimental or beta software though, and they are not usually maintained by the Ubuntu developers themselves, so it's not always the best option.

Hope this helps.

---

### Post by vicke4 on 2011-04-13
really it's not working.please tell me a different way.

---

