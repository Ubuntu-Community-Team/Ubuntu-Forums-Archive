---
title: "phpize errror"
date: 2006-02-22
forum: Desktop Environments
---

### Post by rtacconi on 2006-02-22
I am trying to install PDO for PHP on Ubuntu 5.10. I use pear php install... but I get this error:

root@ubuntu:/etc/apt# pear install PDO-alpha
downloading PDO-0.1.1.tgz ...
Starting to download PDO-0.1.1.tgz (21,459 bytes)
........done: 21,459 bytes
12 source files, building
running: phpize
sh: phpize: command not found
`phpize' failed
root@ubuntu:/etc/apt#



root@ubuntu:/etc/apt# pear install PDO_OCI-alpha
downloading PDO_OCI-0.1.tgz ...
Starting to download PDO_OCI-0.1.tgz (9,904 bytes)
.....done: 9,904 bytes
7 source files, building
running: phpize
sh: phpize: command not found
`phpize' failed
root@ubuntu:/etc/apt#
root@ubuntu:/etc/apt#

Does anybody has a solution? Thanks.

---

### Post by EmmEff on 2006-02-22
You need to install php4-dev or php5-dev to get phpize.

---

