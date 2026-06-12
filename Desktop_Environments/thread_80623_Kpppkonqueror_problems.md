---
title: "Kppp/konqueror problems"
date: 2005-10-22
forum: Desktop Environments
---

### Post by phil66 on 2005-10-22
Kubuntu Breezy 5.10 

Set up kppp to use with dial-up ISP
The login shows to be connected
When I try and use Konqueror  I get an error message
"Unknown Host"
Tried pinging three different dns and all replied
" Network unreachable"

To reach this point I used Kppp hand book and made the following changes to KPPP

In /etc/ppp/options removed auth and lock and proxyarp
In /usr/sbin  I verfied it was a binary file and setuid was checked
In /usr/lib I verfied setuid was unchecked

Auto configure host Name is unchecked
Have two dns addresses
File /etc/host.conf have" order host bind" entries

In Konqueror I verfied "Accept cookies from originating servers" was unchecked

Thanks in advance for any help
Ray

---

### Post by phil66 on 2005-10-24
Anyone help with this problem

or refer me to where I can get help

Ray

---

