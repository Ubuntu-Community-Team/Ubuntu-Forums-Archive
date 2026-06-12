---
title: "Azureus Would Not Open"
date: 2007-10-24
forum: Desktop Environments
---

### Post by Kdar on 2007-10-24
I can't open Azureus (I used to able before, but not now)

When I type "sh /usr/bin/azureus", I get this:

> DEBUG::Tue Oct 23 23:12:48 GMT-04:00 2007:: org.gudy.azureus2.core3.security.impl.SESecurityManagerImpl::initialise::140:
  No SSL provider available
    SESecurityManager::initialise::52,ConfigurationChecker::setSystemProperties::145,ConfigurationManager::initialise::138,ConfigurationManager::getInstance::71,LoggerImpl::init::90,Logger::<clinit>::48,Class::initializeClass::-1,StartServer::<init>::70,Main::<init>::56,Main::main::162
DEBUG::Tue Oct 23 23:12:48 GMT-04:00 2007:: org.gudy.azureus2.core3.security.impl.SESecurityManagerImpl::initialise::140:
  No SSL provider available
    SESecurityManager::initialise::52,CryptoManagerImpl::<init>::73,CryptoManagerImpl::getSingleton::60,CryptoManagerFactory::getSingleton::33,AzureusCoreImpl::<init>::155,AzureusCoreImpl::create::92,AzureusCoreFactory::create::46,Main::<init>::143,Main::main::162
Aborted (core dumped)


What can I do?
some other program had this "Aborted (core dumped)"

---

### Post by Prospero2006 on 2007-10-24
I would suggest downloading the newest version from

[http://azureus.sourceforge.net/download.php](http://azureus.sourceforge.net/download.php)

See if one of those won't run for you.
Azureus has given me the run-around as well, but I always
seem to get it working.

PLS SEED!


Pros

---

### Post by Kdar on 2007-10-24
I always seed :)

---

I was able to install Azureus 3, using those instructions. (just changed the name of tar in one line of code)
[http://ubuntu1501.blogspot.com/2007/05/installing-newest-azurues-in-ubuntu-704.html](http://ubuntu1501.blogspot.com/2007/05/installing-newest-azurues-in-ubuntu-704.html)

But I have few more questions. How do I change icon for all .torrent files?

---

### Post by tassoman on 2007-10-24
Use deluge as bittorent client

---

### Post by DexBex on 2007-10-25
I am also having problem with Azureus now.It terminates with this error message....
**********************************
 An unexpected error has been detected by Java Runtime Environment:
#
#  Internal Error (53484152454432554E54494D450E435050020F), pid=9103, tid=3084852112
#
# Java VM: Java HotSpot(TM) Client VM (1.6.0-b105 mixed mode, sharing)
# An error report file with more information is saved as hs_err_pid9103.log
#
# If you would like to submit a bug report, please visit:
#   [http://java.sun.com/webapps/bugreport/crash.jsp](http://java.sun.com/webapps/bugreport/crash.jsp)
#
Aborted (core dumped)
*************************************

Is there any problem wiht JAVA VM...???

---

### Post by por100pre1 on 2007-10-25
Don't waste your time with Azureus. Use [Deluge]("http://deluge-torrent.org/downloads-ubuntu"), if using Gutsy do this:

```
sudo aptitude install deluge-torrent
```

---

### Post by DexBex on 2007-10-25
i am using Feisty...is this availabe with genome.....?

---

### Post by zachtib on 2007-10-25
> **DexBex said:**
> i am using Feisty...is this availabe with genome.....?

[http://deluge-torrent.org/downloads-ubuntu](http://deluge-torrent.org/downloads-ubuntu)

---

