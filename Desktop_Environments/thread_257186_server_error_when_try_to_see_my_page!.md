---
title: "server error when try to see my page!"
date: 2006-09-14
forum: Desktop Environments
---

### Post by Lualah on 2006-09-14
```

Server error!

The server encountered an internal error and was unable to complete your request. Either the server is overloaded or there was an error in a CGI script.

If you think this is a server error, please contact the webmaster.
Error 500
192.168.1.5
Thu Sep 14 11:43:12 2006
Apache/2.0.55 (Ubuntu) PHP/5.1.2 mod_ssl/2.0.55 OpenSSL/0.9.8a 

```

i get this error when i try [http://192.168.1.5/~Lualah/page](http://192.168.1.5/~Lualah/page)

if i copy it to /var/www and try to see page by this url
[http://192.168.1.5/page](http://192.168.1.5/page) then works?


in apache error log i see this error
```
[Thu Sep 14 12:09:09 2006] [alert] [client 195.20.32.86] /home/Lualah/public_html/page/.htaccess: php_flag not allowed here

```

what is wrong?

---

### Post by mitjab on 2006-09-14
you must modifie apache2.conf and uncoment this lines

```

<Directory /home/*/public_html>
        AllowOverride FileInfo AuthConfig Limit
        Options Indexes SymLinksIfOwnerMatch IncludesNoExec
</Directory>


```

and change it to
```

<Directory /home/*/public_html>
        AllowOverride All
        Options Indexes SymLinksIfOwnerMatch IncludesNoExec
</Directory>


```

hope it works for you. How smart is this...

---

