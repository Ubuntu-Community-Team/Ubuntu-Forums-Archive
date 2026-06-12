---
title: "PHP and Apache..not linking"
date: 2009-04-08
forum: General Help
---

### Post by gaaurav_singh on 2009-04-08
Hi There,

My name is Gaurav Singh, I have installed Php and Apache with the help of Synaptic....while i was testing that Apache is working or not on local host..the Apache page is not coming...But a line displays "It Works"...what does this mean...and I was trying to test the Php with phpinfo(); it is also not showing the PHP configuration page...

Kindly suggest what to do.?

Thanks in advance
Gaurav
India

---

### Post by _Purple_ on 2009-04-08
If you can see "It works", then your Apache is working fine. Thats the default page.

phpmyadmin might be in /usr/share/phpmyadmin, not in /var/www. If so, you can link them by terminal command:

```

sudo ln -s /usr/share/phpmyadmin /var/www
```

---

