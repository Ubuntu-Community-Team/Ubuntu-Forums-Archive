---
title: "command to remove proxy"
date: 2009-08-30
forum: Desktop Environments
---

### Post by vksingh on 2009-08-30
I exported proxy by using following command:

$ export http_proxy="http://192.168.3.254:8080"

$ export ftp_proxy="http://192.168.3.254:8080"

I want to remove the above exported proxy. Please help...:(

---

### Post by kerry_s on 2009-08-30
log out & back in.

you could also try doing it again but have it blank.
export http_proxy=""

---

### Post by vksingh on 2009-10-05
Thanks , It worked.

In which file ubuntu saves the proxy server IP address and related details?

Please Help..........

---

### Post by Lars Noodén on 2009-10-05
> **vksingh said:**
> I exported proxy by using following command:

$ export http_proxy="http://192.168.3.254:8080"

$ export ftp_proxy="http://192.168.3.254:8080"

I want to remove the above exported proxy. Please help...:(

```
unset http_proxy;
unset ftp_proxy;
```

---

### Post by vksingh on 2009-10-05
can you please tell me in which file in ubuntu does the proxy is stored?

Thanks,

Vivek

---

### Post by Lars Noodén on 2009-10-06
> **vksingh said:**
> can you please tell me in which file in ubuntu does the proxy is stored?


It depends on what you are doing.  For package management it might be in 
the file /etc/apt/apt.conf or in a file with 'proxy' in the name somewhere in the directory /etc/apt/apt.conf.d/

The individual web browsers seem to have their own settings.

---

