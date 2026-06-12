---
title: "userdir and public_html in apache2.conf"
date: 2007-04-24
forum: Desktop Environments
---

### Post by mitjab on 2007-04-24
I reinstall feisty and install LAMP in it by this howto
[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

now i open apache2.conf file and i am looking for userdir and public_html but i can not find.

where i can fix this in feisty?

---

### Post by mlind on 2007-04-24
To enable userdir module in apache2
```

sudo a2enmod userdir

```
It's installed by default apache2 packages in feisty.
No need for manual editing. Conf files can be found from /etc/apache2/mods-available and enabled configurations from /etc/apache2/mods-enabled

Use a2enmod to enable, a2dismod to disable modules.

---

### Post by mitjab on 2007-04-25
thx for help!

---

### Post by aldin on 2007-07-17
> **mlind said:**
> To enable userdir module in apache2
```

sudo a2enmod userdir

```
It's installed by default apache2 packages in feisty.
No need for manual editing. Conf files can be found from /etc/apache2/mods-available and enabled configurations from /etc/apache2/mods-enabled

Use a2enmod to enable, a2dismod to disable modules.


thanks, worked for me (k/ubuntu 7.04)
sudo a2enmod userdir
sudo /etc/init.d/apache2 force-reload
mkdir $HOME/public_html
[http://localhost/~aldin](http://localhost/~aldin)

---

