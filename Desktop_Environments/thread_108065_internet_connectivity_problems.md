---
title: "internet connectivity problems"
date: 2005-12-24
forum: Desktop Environments
---

### Post by arvsr1988 on 2005-12-24
Hello all,

I have an ADSL connection.  I did what this site ([http://ca.huji.ac.il/services/internet/connect/adsl/pppoe_linux.shtml](http://ca.huji.ac.il/services/internet/connect/adsl/pppoe_linux.shtml)) told me to do (it was to actually download a program that helped setup pppoe).  My internet then worked and i let ubuntu do auto updates.  After that i rebooted the system and ever since i rebooted the system, my internet doesn't work anymore.  In the connection icon (in the taskbar, top right) there is a red cicle with a white dash and when i click it i get this error: SIOCGIFFLAGS.  So i right click that icon and change the thing to "lo" or "eth0".  then i reconnect back to the internet and it connects but when i open firefox and type [www.google.com](www.google.com) or whatever, it keeps looking and doesnt load the page. can anybody help me?

---

### Post by arvsr1988 on 2005-12-26
hey can someone please help me out??

---

### Post by imrumpf on 2005-12-30
not sure if this helps but it worked for me...

1) Terminal ---> sudo pppoeconf
2) insert all of the proper information.
3) verify everything works.
4) System --> Preferences --> Sessions --> Startup programs --> 

5)add:
pon dsl-provider 


Hope that helps, let me know if it did.

---

