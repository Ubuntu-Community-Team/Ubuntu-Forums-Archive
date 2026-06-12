---
title: "enable .htaccess for directory and asterisk addons package"
date: 2009-01-07
forum: General Help
---

### Post by hosdes on 2009-01-07
1/
I'd created .htaccess with php_flag values in a directory.  How do I get our server to use these php_flag instead of php.ini values for this directory.

2/
I installed all the asterisk repos from our server.  I don't know if this included asterisk-addons.  it downloaded 1.4.17 asterisk.  Does it comes with asterisk-addons or do I have to wget from digium's site and install this way?

I am using ubuntu 8.04 LTS 64 bit and mostly everything was dowloaded by repos.

---

### Post by mssever on 2009-01-07
> **hosdes said:**
> 1/
I'd created .htaccess with php_flag values in a directory.  How do I get our server to use these php_flag instead of php.ini values for this directory.
Make sure Apache is configured to use .htaccess files, and make sure that php.ini allows override of its settings via .htaccess.

---

