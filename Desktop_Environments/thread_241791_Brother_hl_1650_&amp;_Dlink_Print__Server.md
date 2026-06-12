---
title: "Brother hl 1650 &amp; Dlink Print  Server"
date: 2006-08-22
forum: Desktop Environments
---

### Post by turath on 2006-08-22
Greets Guys


Ok Well my setup is simple.

I set up an ubuntu box inside my network.

It was not aproblem because we are all just networked not really 
an internal domain.

I have been tryign to print to this dlinks erver that connects the office to 
the brother hl 1650.

Now as with windows I just pointed to the printer installed the driver and it was working.

Unfortunately with Ubuntu I have been having no such luck.

I installed Samba and have cups working


the ip to the dlink is static set at 172.16.1.253

I can see it in the network servers but I cannot print to it.

Do I need to do somethig special...because I don't need perms to print.


Can someone point me in the right direction.

-

---

### Post by llamakc on 2006-08-22
Here's what I always do on Ubuntu, right or wrong.

cd /usr/share/doc/cupsys && zcat README.Debian

```

 - Administration over the web interface is disabled by default since it
   requires the CUPS daemon to be able to read /etc/shadow.  If you want to
   enable web administration with shadow passwords (authentication type
   'basic'), put the user cupsys into group shadow by

       adduser cupsys shadow

   as root.

```

The snip above is near the bottom of the readme.

Next:

Restart cups: /etc/init.d/cupsys restart

and next:

sudo ln -s  ../backend-available/snmp /usr/lib/cups/backend/snmp
 
Now, when you browse to localhost:631 in FireFox you should see your printer autodetected.

---

