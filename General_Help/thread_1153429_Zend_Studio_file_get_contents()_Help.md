---
title: "Zend Studio file_get_contents() Help"
date: 2009-05-08
forum: General Help
---

### Post by Bedpan.ca on 2009-05-08
This problem has been bothering me for probably a year now. The only work around I have been able to come up with is to run the windows version inside VirtualBox. Really not great.

So, my problem is any time I try to run file_get_contents() from inside Zend Studio, I get errors. From the command line, my installed PHP is able to run the same code fine.

Example code:
[PHP]<?
echo file_get_contents("http://www.google.ca/");
?>[/PHP]

Gives me this:
```
Debug Warning: PHPDocument1 line 3 - file_get_contents() [<a href='function.file-get-contents'>function.file-get-contents</a>]: php_network_getaddresses: getaddrinfo failed: Name or service not known
Debug Warning: PHPDocument1 line 3 - file_get_contents(http://www.google.ca/) [<a href='function.file-get-contents'>function.file-get-contents</a>]: failed to open stream: No such file or directory

```

I am trying to get version 5.5 running, as I prefer it to the Eclipse version, although I have tried the version 6 with the same results.

I have tried installing, and reinstalling Zend Studio to no avail.

Any help would be appreciated.
Thanks.

---

