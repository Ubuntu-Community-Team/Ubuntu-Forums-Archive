---
title: "Help. Can't see samba printer from Windows."
date: 2005-12-21
forum: Desktop Environments
---

### Post by KermitJr on 2005-12-21
I'm using Kubuntu.

I've needled through all of the control settings.  Tried to force user, etc.

Could someone please give me a step by step on sharing a printer from samba to windows xp.

For the record, I've searched the forums, the wiki won't connect, and I'm getting really frustrated.

Thanks,
KermitJr.

---

### Post by HermanAB on 2005-12-21
Can't give you a simple step by step.  However, have a look at this guide:
[http://www.aerospacesoftware.com/samba-debug-howto.html](http://www.aerospacesoftware.com/samba-debug-howto.html)

The first trick is to ensure that you can see the printer using smbclient by connecting to the server, preferably from another Linux machine, or from the server itself.

The second trick is to ensure that the Windows firewall is open and will allow the printing service through.  You can test that by using telnet.  The common ports are 515, 631 and 9100.  Therefore, if your Windoze firewall is open, you should get a response from the server when doing:
c:\> telnet serveraddress 631

The final trick is to remember that CUPS make all printers appear to be Postscript printers.  Therefore, configure the printer in Windows as an Apple Laser Writer II and it should work, no matter what kind of printer it really is.

'Hope that helps!

Herman
[http://www.aerospacesoftware.com/linuxhowtos.html](http://www.aerospacesoftware.com/linuxhowtos.html)

---

