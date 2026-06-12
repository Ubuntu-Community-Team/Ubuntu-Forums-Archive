---
title: "hosting a printer"
date: 2006-01-25
forum: Desktop Environments
---

### Post by fast orange on 2006-01-25
simple question, but only complicated answers were found in other posts.  I've got 2 ubuntu computers, and one printer.  I use DHCP, so ip adress configuration is not an option for printing.

How do I use localhost:631 to share my printers (my printer doesnt install in the ubuntu menus, only this).  I think i'm typing a bad device URI, cause I'm getting the message that it can't connect.  Is security an issue? do I need to supply passwords or activate the printer to be shared?

PS. If your in need of making the canon IP1500 work in linux.  Localhost:631 is necessary for the driver someone provided here in the forums.

---

### Post by Shadyman on 2006-01-25
You could always Samba share it, then link it by Samba on your other computer. That's the only way I can think of right now, i'm sure there's a *nix way of doing it. :KS

---

### Post by soulestream on 2006-01-25
> I use DHCP, so ip adress configuration is not an option for printing.

no, No, NO

I have seen this a few times today on posts. Just because you use DHCP, doesnt mean you cant have a static address.  
1. Most home routers support static DHCP. This means you can specify what IP address each PC gets, even though it is using DHCP.(or just use static addresses)

2. DHCP server should(this is kinda flaky sometimes), update your system so the it knows what address/hostname each machine has. So you can then just say the printserver is on PC-bob, instead of 192.168.12.4. Option 1 works much better.  

To enable the cups webmin 

[http://ubuntu.wordpress.com/2005/10/13/enabling-cupsys-web-admin-interface/](http://ubuntu.wordpress.com/2005/10/13/enabling-cupsys-web-admin-interface/)

To set up IPP

[http://www.gentoo.org/doc/en/printing-howto.xml](http://www.gentoo.org/doc/en/printing-howto.xml)   <-- start at *Configuration. 

soule

---

