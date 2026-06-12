---
title: "PHP module already loaded"
date: 2006-08-29
forum: Desktop Environments
---

### Post by benclinch on 2006-08-29
Hi,
I am configuring ruby on rails and phpmyadmin at the moment. Ruby on rails went fine, I now need to set up phpmyadmin.
I have installed it, now I am going to use the setup.php file to set it all up, but when i try to open it, it wants to download it. I have followed all instrctions [here]("https://help.ubuntu.com/community/ApacheMySQLPHP").
When I try to restart/stop/start/do anything with apache it always says
```
[warn] module php5_module is already loaded, skipping
```
Could somebody please help me by telling me what is going on?

Thanks alot

Ben

---

### Post by benclinch on 2006-08-29
Bump!

---

### Post by Ramses de Norre on 2006-08-29
I guess apache tries to load the php5_module everytime it starts but it's allready loaded then.. 
Do you have problems with php5? If not this is nothing to worry about, I've got the same warning here and everything works.

---

### Post by benclinch on 2006-08-29
> **Ramses de Norre said:**
> I guess apache tries to load the php5_module everytime it starts but it's allready loaded then.. 
Do you have problems with php5? If not this is nothing to worry about, I've got the same warning here and everything works.

I have the problem in that it asks to download local php files in /var/www rather than open and display them in the browser.

---

### Post by Ramses de Norre on 2006-08-29
I've got this problem too but I'm using apache1.3 so my solution probably wont work for you.. it's a common problem though so maybe a forum or google search will reveal the solution.

---

### Post by thirstygerry on 2007-02-22
I got the same message:

[warn] module php5_module is already loaded, skipping

and I couldn't even browse to 127.0.0.1
During the install I copied apachectl to /etc/init.d/httpd to make it start when I booted.
I removed /etc/init.d/httpd and rebooted once again.

Now I have to manually start apache2 and I still get the message but it all seems to work fine now.

---

