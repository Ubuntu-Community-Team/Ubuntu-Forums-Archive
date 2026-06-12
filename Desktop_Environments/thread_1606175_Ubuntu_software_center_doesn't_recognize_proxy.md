---
title: "Ubuntu software center doesn't recognize proxy"
date: 2010-10-26
forum: Desktop Environments
---

### Post by cuby on 2010-10-26
Hello.
I have a fresh install of Ubuntu 10.10 i386, desktop edition.
Since then I'm unable to install software using Ubuntu software center and update manager because this apps are not using the proxy configuration.
I have a proxy with authentication applied system wide. Synaptic has the same configuration and works well.

I'm frustrated about this because there are several bug reports and no one seems to care.
Bugs:
[https://bugs.launchpad.net/ubuntu/+source/empathy/+bug/658445](https://bugs.launchpad.net/ubuntu/+source/empathy/+bug/658445)
[https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/545134](https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/545134)

All other gnome applications are working well except Ubuntu one. It seems it cannot handle proxy authentication.
I have other machines without proxy and they work ok.
the result of the ```
sudo apt-get update
``` are in the attach.
Can someone help?

---

### Post by carl.davis on 2010-10-26
You could try to create a file at: /etc/apt/apt.conf containing

```
Acquire::http::proxy "http://127.0.0.1:3128";
```

And then try "apt-get update". This worked for me however I don't have a proxy that uses authentication. To insert the username and password use the following syntax:

```
http://[[user][:pass]@]host[:port]/
```

---

### Post by cuby on 2010-10-26
Thanks.
Yes, it worked but its a hack... Its not a good idea to have the password over there in plain text. :(
the correct syntax is:

```
Acquire::http::proxy "http://user:pass@proxy.xxxx.xxxx:port";

```

Ubuntu one doesn't connect with this.

---

### Post by carl.davis on 2010-10-26
> **cuby said:**
> 

Ubuntu one doesn't connect with this.

Unfortunately it appears as though Ubuntu One does not yet work behind a proxy.

[https://answers.edge.launchpad.net/ubuntuone-client/+faq/1006](https://answers.edge.launchpad.net/ubuntuone-client/+faq/1006)

---

### Post by cuby on 2010-10-27
Support was apparently added in 10.10, the current version. Unfortunately proxy WITH authentication is not working properly.

---

### Post by yesint on 2010-11-03
> **cuby said:**
> Support was apparently added in 10.10, the current version. Unfortunately proxy WITH authentication is not working properly.

No, it doesn't work in 10.10 even with proxy without autentification. If you know how to make it work - please share!

---

### Post by cuby on 2010-11-08
Sorry, I am unable to test proxy without authentication. What I said was based on the Ubuntu One roadmap. I only tested proxy with authentication and it doesn't work.

---

