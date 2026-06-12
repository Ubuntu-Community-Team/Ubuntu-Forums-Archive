---
title: "interrupted dpkg"
date: 2009-02-11
forum: General Help
---

### Post by themagicmanfromtrent on 2009-02-11
Hi,

I was installing updates, and my laptop ran out of battery and turned off. *(Yes ever since I updated to hardy it stopped warning me)*

I rebooted, and had a feeling something was going to be broken. I open synaptic, and it tells me to run **dpkg --configure -a**.

I did that, and now synaptic works, but I got this error:

```
danny@DAN:~$ sudo dpkg --configure -a
Setting up xfonts-scalable (1:1.0.0-6ubuntu0.8.04.1) ...
E: /var/lib/defoma/locked exists.
E: Another defoma process seems running, or you aren't root.
E: If you are root and defoma process isn't running undoubtedly,
E: it is possible that defoma might have aborted.
E: Please run defoma-reconfigure -f to fix its broken status.
dpkg: error processing xfonts-scalable (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 xfonts-scalable

```

What do I do?

---

### Post by roshanjose on 2009-02-11
just open synaptic package manager and go to EDIT --->Fix Broken Packages


This will help

---

### Post by themagicmanfromtrent on 2009-02-11
Thanks.

---

