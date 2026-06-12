---
title: "Wordpress Ubuntu 9.04 help"
date: 2009-07-10
forum: Desktop Environments
---

### Post by toddbmobile on 2009-07-10
I have installed **Wordpress** and **LAMP** on my PC successfully. I can goto **[http://localhost/wordpress](http://localhost/wordpress)** and view my wordpress site with its CSS formatting fine. I have set permissions to the wordpress folder to **777**. I wanted to view the site from other computers on my network and at remote locations. I set my PC's IP to a static IP and in my router set port 80 traffic to forward to that IP address. When I try to access the site from other computers it comes up , but _all the CSS formatting is gone_ (it does not matter which brower you use the results are the same). I get the same result wither I access it via my IPS's provided IP Ex. **[http://71.34.23.334/wordpress](http://71.34.23.334/wordpress)** or if I access it via internal network ex. **[http://192.168.1.22/wordpress](http://192.168.1.22/wordpress)**. All I get it the text but no pretty formatting. I think it must be a permissions setting on my PC, but I'm not sure what to do. **Please someone help!!!!**

---

### Post by JohnLau on 2009-07-10
):P Don't worry, try this
```
sudo chown www-data /var/www/wordpress -R
```
John

---

### Post by noobvogelkopp on 2009-07-17
Hi, i got the exact same problem here. ```
sudo chown www-data /var/www/wordpress -R
``` does not work for me :(. Any more tips? thanks in advance

---

