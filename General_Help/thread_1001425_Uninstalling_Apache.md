---
title: "Uninstalling Apache"
date: 2008-12-03
forum: General Help
---

### Post by JohnNY05 on 2008-12-03
I've been trying to un-install Apache for the past 2 days now without any success, have use

apt-get remove apache2 (and) apt-get remove --purge apache2

without any success, every time folders 
/etc/apache2
/var/www

are still there ](*,)

Can someone please help me by telling me exactly what am I doing wrong here?!!

---

### Post by fooey on 2008-12-03
have you tried doing it via synaptic? ...if you're even using a GUI, obviously

---

### Post by JohnNY05 on 2008-12-03
Yep, tried synaptic and it is still there :(

---

### Post by fooey on 2008-12-03
you tried the "complete removal" ? hrmm..

---

### Post by linorics on 2008-12-03
How did you install it? apt-get, server edition install, etc?

---

### Post by JohnNY05 on 2008-12-04
> **fooey said:**
> you tried the "complete removal" ? hrmm..
Would you please explain more what do you mean exactly by 'complete removal'?

What I have tried so far is apt-get remove and apt-get remove --purge

---

### Post by gabril on 2008-12-04
Try sudo aptitude purge <program>

---

### Post by JohnNY05 on 2008-12-04
> **linorics said:**
> How did you install it? apt-get, server edition install, etc?
Yes I did install using 

apt-get install apache2

now after a couple of installations and un-install, I made another install and when browsing to 127.0.0.1, it shows page:

Unable to connect

under FireFox :(

---

### Post by JohnNY05 on 2008-12-04
> **gabril said:**
> Try sudo aptitude purge <program>
Tried it now and the folder 

/etc/apache2

is still there, containing all the old configuration files :(

---

