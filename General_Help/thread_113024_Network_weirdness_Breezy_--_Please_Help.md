---
title: "Network weirdness Breezy -- Please Help"
date: 2006-01-05
forum: General Help
---

### Post by mikecrowe on 2006-01-05
Hi folks,

I am having some network weirdness I need some advise on:

Hardware:  Dell Latitude D600 with Intel PRO/Wireless 2200BG.

Using Breezy, but with the 2.6.15-10-i686 kernel from Dapper.  Network continually locked up (regardless of linux distribution) until I upgraded to .15 kernel.

Now, I having strangeness I'm trying to debug.  Some websites which work fine for other people aren't working for me.  Truthfully, I'm pretty sure it worked for me before, but I can't be sure.

Here's what's happening.  When I do a short submit on a form, it appears to go through fine.  When I do a big submit (meaning there might be a good bit of data going back to the server), I get a continual wait (200s+) with the final error message (on the destination apache server) being:

 > [error] [client 10.10.10.45] request failed: error reading the headers

On my browser, I'm getting: 
> Bad Request

Your browser sent a request that this server could not understand.
Apache/2.0.54 (Unix) mod_ssl/2.0.54 OpenSSL/0.9.7g PHP/4.3.11 DAV/2 mod_perl/1.999.21 Perl/v5.8.6 Server at localhost Port 80

Here's the strange part:  This is not browser specific, nor server specific.  I get it in Firefox, IE, Epiphany when browsing to both an Apache server and to an IIS server.

The only common factor I can think of is that it appears to happen just to web sites inside our firewall, which means it could be something related to the Cisco VPN client I'm using (latest one from Cisco, BTW).> Cisco Systems VPN Client Version 4.8.00 (0490)

Can anybody shed some light on this???  Please help.

TIA
Mike

---

