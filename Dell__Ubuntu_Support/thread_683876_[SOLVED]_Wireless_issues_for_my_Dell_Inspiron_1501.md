---
title: "[SOLVED] Wireless issues for my Dell Inspiron 1501"
date: 2008-01-31
forum: Dell  Ubuntu Support
---

### Post by Drag0nFr3ak on 2008-01-31
Ok, so I have a Dell Inspiron 1501, Ubuntu 7.10 and I am sure my wireless isn't working properly. I can use the internet and download things. So far so good, but my add/remove applications thing is forever failing to download files and having to retry them again and again. Also, my firefox seems to stop working once in a while. Is this something to do with my wireless card? I am new to Linux, so all help will be great.

---

### Post by faulkes on 2008-02-01
> **Drag0nFr3ak said:**
> Ok, so I have a Dell Inspiron 1501, Ubuntu 7.10 and I am sure my wireless isn't working properly. I can use the internet and download things. So far so good, but my add/remove applications thing is forever failing to download files and having to retry them again and again. Also, my firefox seems to stop working once in a while. Is this something to do with my wireless card? I am new to Linux, so all help will be great.

The technical answer is "possibly".  Which wireless card came with the dell (usually either intel or broadcomm), that will tell us which driver you're using.

If you are unsure, you can issue a:

```
lspci
```

and paste the results back here.

Next, have you configured a proxy server or do you know if your ISP is using one?

Next, when you start to encounter the issue, I would consider ping'ing an outside/external address and see if there is any packet loss (that won't tell us if its the card but it will let us know a network problem exists).

Faulkes

---

### Post by Drag0nFr3ak on 2008-02-01
My wireless card is a broadcomm using the 43xx driver from the restricted drivers.

As far as I know there is no proxy server, and as it is a home network Iwouldn't think the ISP would have one assigned to me.

How would I carry out a ping test?

---

### Post by faulkes on 2008-02-01
> **Drag0nFr3ak said:**
> My wireless card is a broadcomm using the 43xx driver from the restricted drivers.


You may wish to try and use ndiswrapper and the dell supplied windows drivers for the card then.  My experience (and this is just my experience) is that the 43xx restricted drivers are the cause of, rather than the cure of a number of dell wireless issues under ubuntu.

> 
As far as I know there is no proxy server, and as it is a home network Iwouldn't think the ISP would have one assigned to me.


Then that is likely the case, unless your isp is using a transparent proxy, in which case it would be somewhat hard to determine.  For now we will assume there is no proxy involved.

> 
How would I carry out a ping test?

```

ping -c 10 <ip address>

or 

ping -c 10 www.google.com

```

When the ping stops, it will output some statistics which you can post back here.


Faulkes

---

### Post by Drag0nFr3ak on 2008-02-01
Ok, I will try out the ndiswrapper driver and then I will try out the ping when I get home from work.

Edit: I think it has worked, just to see if it will cut out. Thanks for all of your help.

---

### Post by zeroed on 2008-02-01
I have the same problem in VMWare. I have installed vmware tools, but it doesn't fixed the problem.

---

### Post by Drag0nFr3ak on 2008-02-01
It's working great, just thought I would say that it is now working properly! Thanks again.

---

