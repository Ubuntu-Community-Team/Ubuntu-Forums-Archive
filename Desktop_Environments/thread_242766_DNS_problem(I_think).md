---
title: "DNS problem(I think)"
date: 2006-08-24
forum: Desktop Environments
---

### Post by titaniumz on 2006-08-24
I have reinstall entire ubuntu just to fix a problem and I have it again in the new version.
It seems that something is ****** up with the DNS thingy, also as last time I couldnt see webpages with firefox until Iv'e changed: network.dns.disableIPv6 on firefox config to true(I dont know what that mean I just know that only like that I can see webpages!),
also I cant add applications from the internet, cant update, and gaim wont connect with "login.icq.com" I have to ping it with terminal, see the IP and then insert the IP in the "Auth host"... these are all examples the problem I think is something with DNS and it concern all of my ubuntu system :\

any help will be much appraised.

---

### Post by hraposo on 2006-08-24
> network.dns.disableIPv6 on firefox config to trueHow you do that?

---

### Post by soutSA on 2006-08-24
Take a look at this thread, it might have something to do with it:

[http://www.ubuntuforums.org/showthread.php?t=202838](http://www.ubuntuforums.org/showthread.php?t=202838)

IPv4 apperently conflics with IPv6.

---

### Post by titaniumz on 2006-08-24
> **hraposo said:**
> How you do that?

on the address bar type: about:config then find Ipv6.. and dbl click to change its value.

---

### Post by titaniumz on 2006-08-24
> **soutSA said:**
> Take a look at this thread, it might have something to do with it:

[http://www.ubuntuforums.org/showthread.php?t=202838](http://www.ubuntuforums.org/showthread.php?t=202838)

IPv4 apperently conflics with IPv6.

I did it and it didnt work :\

can anyone please help me? every program who needs to do something with the internet cant... either it get stuck or give me erorr messages(exept firefox ..)

---

### Post by dr0ne on 2006-08-25
I also have this exact same problem as you described, i can only access things by pinging the hostname and entering the ip address manually.. for some reason its just not accessing the DNS normally...

---

### Post by true_friend on 2006-08-25
plz verify u are not behind an ISAserver. if u are behind and ISAserver u have to change the settings on server pc or you have to use NTLM APS. NTLM authorization proxy server. u can get it from sourceforge.org.

---

