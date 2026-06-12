---
title: "Xerox Workcentere Pro Driver won't install."
date: 2006-04-07
forum: Desktop Environments
---

### Post by lucas.clemente on 2006-04-07
THe driver is here: 
[http://www.support.xerox.com/go/getfile.asp?Xlang=en_US&XCntry=USA&objid=49941&EULA=1&prodID=WCPC2128_WCPC2636_WCPC3545&Family=WorkCentre%20Pro&ripId=&langs=English%20(US)&plats=Linux&Xtype=download#suppplat](http://www.support.xerox.com/go/getfile.asp?Xlang=en_US&XCntry=USA&objid=49941&EULA=1&prodID=WCPC2128_WCPC2636_WCPC3545&Family=WorkCentre%20Pro&ripId=&langs=English%20(US)&plats=Linux&Xtype=download#suppplat)

I get wierd error messages when I run sudo ./setup

lclemente@ubuntu-Lucas:~/Desktop/Linuxi386XpxxInstall$ sudo ./setup
................ERROR: No such file or directory
lclemente@ubuntu-Lucas:~/Desktop/Linuxi386XpxxInstall$ 

I need this stupid printer driver to install.

---

### Post by kingmonkey on 2006-04-07
is setup executable?

---

### Post by lucas.clemente on 2006-04-07
I can only assume it is. How do I check?

---

### Post by black hole sun on 2006-04-07
It is indeed a binary setup file.

This is what I get when  I try to run it:

.sh: /usr/Xerox/xpxx/xpqadmin: No such file or directory
sh: /usr/Xerox/xpxx/xpqadmin: No such file or directory

Apparently you need some xerox program installed prior to installing this driver.

---

