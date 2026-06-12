---
title: "Jdownloader install failed attempt"
date: 2009-04-25
forum: General Help
---

### Post by kerryandjane on 2009-04-25
Hey guys, the first tricky thing i tried in the new Jaunty is to install Jdownloader (to download megaupload files)
i was following 
[http://blackonsole.blogspot.com/2009/03/install-jdownloader-on-linux-ubuntu-810.html]("http://blackonsole.blogspot.com/2009/03/install-jdownloader-on-linux-ubuntu-810.html")

the error is
E: python-wxgtk2.8: subprocess post-installation script returned error exit status 1
E: wxbanker: dependency problems - leaving unconfigured


i only did the first step which crashed my computer

Can someone help?

---

### Post by Find on 2009-05-19
Do you have Java installed?

If not, install Java first.  You can go to System > Administration > Update Manager. Java 6 is already there.

Then follow the instructions given here
[http://pagesofinterest.net/blog/2009/05/installing-jdownloader-in-ubuntu/](http://pagesofinterest.net/blog/2009/05/installing-jdownloader-in-ubuntu/)

It will work.

BTW, i think at first you should 
sudo dpkg --configure -a

---

