---
title: "network proxy settings"
date: 2009-05-23
forum: General Help
---

### Post by bryncoles on 2009-05-23
My google-fu is weak. I cant figure out how to set system-wide proxy settings in xubuntu, which means I cant use synaptic package manager!

And all I see is dead threads on this topic on the forums!

how do I set the network proxy for a xubuntu system, does anyone know?

---

### Post by Neural oD on 2009-05-23
> **bryncoles said:**
> My google-fu is weak. I cant figure out how to set system-wide proxy settings in xubuntu, which means I cant use synaptic package manager!

And all I see is dead threads on this topic on the forums!

how do I set the network proxy for a xubuntu system, does anyone know?
if u use command line apt-get - you can always use: export http_proxy=http://proxy_address_here:port_here

---

### Post by bryncoles on 2009-05-23
I'm a little dumb sometimes...

i just typed 

```
export http_proxy=http://proxy_address_here:port_here
```

and it didnt work. should i have tried 

```
apt-get export http_proxy=http://proxy_address_here:port_here
```?

---

### Post by bryncoles on 2009-05-23
google-fu!

[https://lists.ubuntu.com/archives/xubuntu-users/2007-June/000755.html](https://lists.ubuntu.com/archives/xubuntu-users/2007-June/000755.html)

told me to edit 

```
 gksudo mousepad /etc/environment
```

and add the line:

```
http_proxy="http://url::port_number
```

then log out/in. now it works fine! yay!

---

### Post by Neural oD on 2009-05-23
Glad u came right 
Google is always a good friend

---

### Post by bryncoles on 2009-05-23
yeah, good ol' google!

thanks for trying to help though, i appreciate it! :-)

---

