---
title: "COnfiguring proxy which needs authorization"
date: 2006-12-13
forum: Desktop Environments
---

### Post by marufsiddiqui on 2006-12-13
The name says it all. well my isp needs authorization for proxy ie it uses a proxy & whenever i try to open a site with firefox a dialog box appears & asked me to give my username & pass. well its ok and works fine

but i was actually talking about the synaptic. when i try to reload the repositories, it says it cant access the internet. i have configure the network proxy but yet it is not working. i know its a newb ques yet i need help on it.

how to coonfigure the proxy which also will include my usename & pass. bcoz synaptic does not show any dialog box to put usename and pass.

what to do now?

plz help

---

### Post by g3k0 on 2006-12-13
I am behind a proxy as well. Theres probably a better way to do it but this is what I do. All I did to get it to work was put in the proxy in system->preferences->network proxy.  I then open firefox and login with my name and everything before opening symantec.  When I click reload it works.  Hopefully that way will work for you if you cant find a better solution.

---

### Post by argie on 2006-12-13
I had to do this in Breezy and I did a straight upgrade to Dapper so I'm not sure if it's still necessary. Still it's still in there. If g3k0's solution doesn't work:
Try, in console,
```
gksudo gedit /etc/apt.conf
```
and type in
```
ACQUIRE {
http::proxy "http://username:password@proxy:port/"
}

```
replacing the relevant parts with your username, password, proxy and port.

And save it. Then, in console, try ```
sudo apt-get update
```

---

### Post by muddymind on 2007-08-01
Is there any other way of doing it? Filling the text file in ascii can be a security issue...

I'm trying to configure a linux box to use apt with the proxy of the company where I work... 

[]

---

