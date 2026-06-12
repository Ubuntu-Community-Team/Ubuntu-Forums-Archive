---
title: "Pidgin and MS Lync 365"
date: 2015-01-30
forum: Desktop Environments
---

### Post by frytek on 2015-01-30
Hi, 

I am placing it here because it took me some time to make it work. 

Here's how to make Pidgin talk to Lync 365 users: 

1. Install pidgin-sipe
```
sudo apt-get install pidgin-sipe
```

2. In Pidgin: 
Accounts / Manage / Add / Protocol: Office communicator

3. Settings: 

Basic tab: 
Username: username you use to log in to Office 365 services, e.g.: [email]my_email@company.com[/email]
Login: same as username

Password: your password used to log in to the Office 365 services. 

Save password: ticked

Local alias: anything. 

Advanced tab: 
Server / port: empty
Connection type: Automatic
User Agent: UCCAPI/4.0.7577.314 OC/4.0.7577.314
Auth: TLS-DSK
Single login: not ticked. 

That's all. All others fields empty. 


Edit: 
I fount much newer user agent: 
UCCAPI/15.0.4420.1017 OC/15.0.4420.1017 (Microsoft Lync)
This one works with login empty (just with username and pass).

Works for me on Mint 17, based on Trusty.

---

