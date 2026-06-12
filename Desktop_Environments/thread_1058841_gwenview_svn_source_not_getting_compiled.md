---
title: "gwenview svn source not getting compiled"
date: 2009-02-03
forum: Desktop Environments
---

### Post by jhahoneyk on 2009-02-03
I have checked out the latest svn source for gwenview, following instructions at [http://gwenview.sourceforge.net/svn](http://gwenview.sourceforge.net/svn) . When I try to make it, after many checks, it gives the following error-

```
checking for Qt... configure: error: Qt (>= Qt 3.2) (headers and libraries) not found. Please check your installation!
For more details about this problem, look at the end of config.log.

```

But I have Qt4 libraries and headers installed and so I am able to compile and run my own small qt apps (I'm learning qt) by using qmake and make.
After some googling, I found on the forums to install libqt3-headers libqt3-compat-headers qt3-dev-tools libqt3-mt-dev . Doing so removed the error, but not my Qt apps won't compile. make is unable to find the header files (like QApplication, etc). So I uninstalled the Qt3 headers and libraries, and reinstalled the Qt4 headers and libraries. So, now the situation reverted back, I can compile my Qt apps, but gwenview configure gives the same error.

I conclude that the ./configure is unable to find the Qt 4 headers and libraries. But being a newbie, I don't know how to fix this, so please help.

---

