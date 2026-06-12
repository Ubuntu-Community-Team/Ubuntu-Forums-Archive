---
title: "tcp_wrappers package?"
date: 2009-05-18
forum: General Help
---

### Post by firsttimeuser on 2009-05-18
ubuntu 8.10, what is the tcp_wrappers's name in the software repository? 

I am trying to apt-get and the system does not know tcp_wrapper...

---

### Post by 73ckn797 on 2009-05-18
> **firsttimeuser said:**
> ubuntu 8.10, what is the tcp_wrappers's name in the software repository? 

I am trying to apt-get and the system does not know tcp_wrapper...


Look in Synaptic and search for "tcp". In Jaunty there are several apps already installed and several other related utilities. I do not see "tcp-wrapper".

Are you wanting to install a wireless driver?

---

### Post by firsttimeuser on 2009-05-18
already took a look and got no luck there...

i am trying to instal tacacs plus, which needs tcp_warpper

---

### Post by 73ckn797 on 2009-05-18
> **firsttimeuser said:**
> already took a look and got no luck there...

i am trying to instal tacacs plus, which needs tcp_warpper


Not familiar with what you are wanting to accomplish but I assume you checked back ports and other sources?

---

### Post by firsttimeuser on 2009-05-18
problem fixed, the lib called libwrap-dev

apt-get install libwrap-dev

thanks for the effort and have a good day!

---

