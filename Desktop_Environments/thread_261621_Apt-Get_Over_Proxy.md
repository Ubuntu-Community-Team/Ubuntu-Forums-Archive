---
title: "Apt-Get Over Proxy"
date: 2006-09-20
forum: Desktop Environments
---

### Post by rohan! on 2006-09-20
Hi,
My girlfriend has recently moved into Edinburgh University student halls, and I have set up her ResNet account. Only problem is that when I apt-get anything i get errors, I think this is because the connection is done via proxy... is there anyone out there that knows how to sort this out??

---

### Post by Dors Venabili on 2006-09-20
You can set the proxy variable in your profile: open a terminal and type

```
export http_proxy=http://*insert_your__http_proxy_here:port*
export ftp_proxy=ftp://*insert_your_ftp_proxy_here:port*
```
this should work.

---

### Post by StephenL on 2006-09-20
You can add the proxy to /etc/apt/apt.conf

Just change where it says "false" to the actual proxy.

---

### Post by rohan! on 2006-09-21
> You can add the proxy to /etc/apt/apt.conf

Just change where it says "false" to the actual proxy.


When I set up firefox, the address that I entered was an Automatic Proxy Configuration URL. I tried to use this URL as the proxy for apt and it failed, is there anyway of using an Automatic Proxy Configuration URL with apt??

---

