---
title: "Authenticating internet users via a gateway"
date: 2006-01-26
forum: Desktop Environments
---

### Post by ijwilliams1975 on 2006-01-26
I am currently planning a small wireless network in halls of residence that will allow subscribers to connect to the internet via my wireless router.
What I would like to find out is how to set up: -
a facility that when a user tries to connect to the internet, if they have not logged in, have them diverted to a login page requesting usernames and passwords

a means to add and remove internet user names passwords and log access

I have just moved over to linux from MS and to be honest i dont know where to start!

My setup is a linksys wrt 54g wireless router with brain slayers ddwrt firmware connected to my DSL modem - all working ok for normal browsing
Ubuntu breezy 5.10 with the i686 kernel on a 3ghz intel processor with 512mb ram
i also have a 12 port unmanged switch...

ideally the process should go as follows:- user connects to access point - get diverted to internet login page... autheticates and browses or doesnt and gets a snotty message!
if any one can help it would be greatly appreciated!!!!!!
Many thanks,
Ian

ps. if I get somewhere with this I will create a step by step how-to guide!!!... google didnt turn much up...

---

### Post by cwaldbieser on 2006-01-26
[QUOTE=ijwilliams1975]I am currently planning a small wireless network in halls of residence that will allow subscribers to connect to the internet via my wireless router.
What I would like to find out is how to set up: -
a facility that when a user tries to connect to the internet, if they have not logged in, have them diverted to a login page requesting usernames and passwords

a means to add and remove internet user names passwords and log access

I have just moved over to linux from MS and to be honest i dont know where to start!

My setup is a linksys wrt 54g wireless router with brain slayers ddwrt firmware connected to my DSL modem - all working ok for normal browsing
Ubuntu breezy 5.10 with the i686 kernel on a 3ghz intel processor with 512mb ram
i also have a 12 port unmanged switch...

ideally the process should go as follows:- user connects to access point - get diverted to internet login page... autheticates and browses or doesnt and gets a snotty message!
if any one can help it would be greatly appreciated!!!!!!
Many thanks,
Ian

ps. if I get somewhere with this I will create a step by step how-to guide!!!... google didnt turn much up...[/QUOTE]

I am not really sure, but it sounds like something you would use a proxy server for.  Maybe squid can do this?

---

### Post by littlewood on 2006-01-26
Then you didn't search very well ;) 

Google turned up this on the first page: 
<http://www.faqs.org/docs/Linux-HOWTO/Authentication-Gateway-HOWTO.html>
and this
<http://www.crt.realtors.org/projects/hotspot/docs/Hotspot%20Authentication%20Gateway.pdf>

---

