---
title: "Apache remote network access issue"
date: 2009-03-20
forum: General Help
---

### Post by rtrembecki on 2009-03-20
Hi,

I've got a problem on 8.04 desktop version with Apache.
I can access the webpages from another computer on the local subnet with no problems at all.

However if I try and access them from a different subnet then there is no response from the webserver.

I can ping the ubuntu machine from the remote subnet with no issues and access samba shares so I know that it's not a routing issue.

strace'ing the apache listening process shows no activity when attempting to access a web page from the remote subnet but does show activity when accessing from the local subnet.

on the firewall side ufw is unloaded.

ports.conf has blanket "listen 80"
sites-enabled/000-default contains:
DocumentRoot /var/www/
        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>
        <Directory /var/www/>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride None
                Order allow,deny
                allow from all
        </Directory>

Oh and just to confirm that there is no nat-ing between the subnets - just straight forward routing.

Any ideas would be gratefully recieved.

Thanks

Richard

---

### Post by rtrembecki on 2009-03-23
Any ideas anyone?

---

### Post by sudo make sandwich on 2009-03-23
It definitely sounds as though your requests aren't hitting your server on port 80. I assume you get no reply from the remote subnet when you type "telnet web.server 80"?

I suggest you focus your attention on the router/firewall between the two subnets. Is there an explicit rule on the router for port 139?

I can forsee the router being configured to allow some ports between the subnets for things like windows workstations on port 139, but it may not have been considered at initial config time that there would ever be a web server on that subnet.

As a test, is there another web server on the same subnet as your apache box? Can you get to that from the other machine?

---

### Post by rtrembecki on 2009-03-23
Hi,

Thanks for the reply.

You are correct in that a telnet yields the same result.

As for the router - it shouldnt be the source of the problem - I have other services running between them - both tradition http, https, samba etc that work correctly - its just this one webserver that's giving me grief.

Richard

---

