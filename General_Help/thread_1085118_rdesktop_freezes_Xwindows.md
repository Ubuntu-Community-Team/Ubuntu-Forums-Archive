---
title: "rdesktop freezes Xwindows"
date: 2009-03-02
forum: General Help
---

### Post by CamG on 2009-03-02
rdesktop is causing my entire desktop to freeze. No keyboard or mouse. I must press the reset button on my box to recover.

I can get a connection and navigate a windows desktop. The freeze only happens when a dialog box pops up within the remote windows session.

This only happens when connecting to Windows Server 2003. It never happens when connecting to Windows Server 2008.

After I reboot my machine and attempt to reconnect to the session on the windows server, it freezes my desktop again.

This started happening after I upgraded from ubuntu 8.04 to 8.10.

This problem is local to my machine as others in my office can use rdesktop without problems.

I am using ubuntu 8.10 32 bit.

---

### Post by jorgeag on 2009-03-03
I have the same problem with Intrepid 8.10 and rdesktop 1.6.0 ...

I reverted back to 1.4.1 that i downloaded from 
[http://linuxappfinder.com/package/rdesktop](http://linuxappfinder.com/package/rdesktop)

I am using version 1.4.1-1.1ubuntu0.6.06.1 on intrepid...

It's really a pain if you try to use Linux on production environments and are always getting this sort of problems...

Hope this helps....

PS: Be sure to dismiss the update of rdesktop each time otherwise you'll get version 1.6.0 again in no time.

---

### Post by pceriotti on 2009-04-09
I had the same problem on xubuntu 8.10 using rdesktop 1.6.0. In my case the client was connecting to Windows 2000 servers and It froze when the user performed certain actions in particular.

The solution I found was downgrading to rdesktop 1.5.0.

---

