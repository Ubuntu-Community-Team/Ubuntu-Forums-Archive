---
title: "Evolution and Proxies"
date: 2004-12-06
forum: Desktop Environments
---

### Post by kmf on 2004-12-06
I'm struggling connecting to my Mailserver via a http proxy.
Any ideas or suggestions that I can try

Karl

---

### Post by JonAtkinson on 2004-12-06
First, the proxy checklist:

Have you set the GNOME proxy in Preferences/Network Proxy

Have you set your HTTP_PROXY environment varible? On the console:```
$ export http_proxy=http://proxy.address.com:portnumber
``` 

(note you can set this as the default for all your logins by appending it to the bottom of /etc/bash.bashrc).

Now, try running Evolution again. Failing that, you might have to be clever and mangle your mail server address to something like: [http://proxy.address.com:portnumber/your.mailserver.com](http://proxy.address.com:portnumber/your.mailserver.com) - something along those lines anyway.

--Jon

---

### Post by kmf on 2004-12-07
Yes 
I tried Port Forwarding it worked :)

Karl

---

### Post by tomash_cz on 2006-02-02
Hi, i have just probably stupid question from the total begginer. I also struggle with evoloution and proxies. I am at work and the only information i can get about proxy is what i find out by myself (i doubt about administrator good will..). according your advise, i should do 

$ export http_proxy=http://proxy.name.com:port

what i know from windows settings, there is a proxy called 'isaserver' or 'isaserver.feihua.hangzhou', the port is 8080. does this mean that i need to write it like following?:

1. $ export http_proxy=isaserver:8080
or
2. $ export http_proxy=isaserver.feihua.hangzhou:8080
or
3. $ export http_proxy=http://isaserver:8080
or
4. $ export http_proxy-http://isaserver.feihua.hangzhou:8080

please help the total newbie in linux and ubuntu as well with low experience with windows as well :-D  but a big ubuntu fan

thanks, would be nice to use ubuntu at work too!

---

