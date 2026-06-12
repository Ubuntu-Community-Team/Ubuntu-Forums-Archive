---
title: "Jaunty LAMP server PHP problem?"
date: 2009-04-26
forum: General Help
---

### Post by Taoye on 2009-04-26
So I just did a fresh install of Xubuntu 9.04 on my laptop. I did a sudo apt-get install apache2 php5 mysql-server.

First bit of strangeness I get is this:

```
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
```

Yes, that extra 1 was there... never had that before.

Apache seems to work fine, I get the It Works! page. However when I try to test if PHP is working, by creating a test.php page, instead of processing the page, Firefox gives me the "Download file: test.php, open or save" window. Both 127.0.0.1 and 127.0.1.1 seem to lead my browser to the same directory... /var/www

Any ideas? Was I supposed to do something extra to make it work? Anybody else gotten it to work? It had all worked fine under Intrepid...

---

### Post by LoneWolfJack on 2009-04-26
in /etc/hosts, add

```
127.0.1.1 localhost
```

and change ServerName accordingly in your httpd.conf

as for php, did you try a file with just

```

<?PHP
phpinfo();
?>

```

?

---

