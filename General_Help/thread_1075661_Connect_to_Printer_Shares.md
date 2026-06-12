---
title: "Connect to Printer Shares"
date: 2009-02-20
forum: General Help
---

### Post by MaindotC on 2009-02-20
I'd like some help figuring out how to connect to networked printers on my campus network.  For example, if I'm using a Vista machine that is not on the campus domain, I can type in the menu \\printer:
[IMG]http://img258.imageshack.us/img258/2883/screenshotvistarunningsqs6.png[/IMG]

 enter my credentials in the formate of "DOMAIN\username" and "password" and then display a list of shared computers on our campus:

[IMG]http://img12.imageshack.us/img12/9923/screenshot1cg6.png[/IMG]

In Ubuntu, I typically print the printer's IP address from the printer configuration, then use System -> Administration -> Printing, create a new LDP printer, enter the IP address, and then it automatically finds the proper printer driver and I have to name it.  Is there any way I can just connect to the printer share and view them as I do in Vista?  Thanks!

---

### Post by MaindotC on 2009-02-23
bump

---

### Post by HermanAB on 2009-02-23
You need to run a scan with "smbclient -L", or try "linneighborhood":
[http://www.bnro.de/~schmidjo/](http://www.bnro.de/~schmidjo/)

If you know which machines to check, you can try "lpstat".  Here are some more ideas: [http://aeronetworks.ca/print-howto.html](http://aeronetworks.ca/print-howto.html)

Cheers,

Herman

---

### Post by MaindotC on 2009-02-23
Thanks, Herman!  I viewed the links you posted and they look like something that will help me.  I'll view them in more detail after I fail this Java test I'm about to take.  I couldn't get smbclient -L to work - the man page specifies to use this option to list shares but I must be missing something :(

---

### Post by MaindotC on 2009-03-06
The -L option doesn't work for me - just lists all available options for smbclient.  I opened nautilus and typed:
```

smb://printer.morrisville.edu

```
and after I authenticated I see some shares on this machine but it's like a listing of C$ and PRINT$ and not the list of printers that shows in windows.  I tried navigating into those shares listed with smb and I was denied access.

---

### Post by jrperpetu on 2009-03-08
sir,

i'm neophyte in linux. i need some help in sharing epson stylus c43sx from 2 system (acer veriton 5600g) units with the same ubuntu 8.10 desktop OS.

my system is configured to use dhcp rather than static ip.

what do i do to make this possible?

please help!

---

