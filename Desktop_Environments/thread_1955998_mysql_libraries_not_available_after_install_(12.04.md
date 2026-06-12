---
title: "mysql libraries not available after install (12.04)"
date: 2012-04-10
forum: Desktop Environments
---

### Post by wtriba on 2012-04-10
Finished a fresh install of Ubuntu 12.04 Beta2, MySQL server (5.5.22) and libmysqlclient-dev (16). MySQL is up and running, header files are there as well. I was expecting lib files to be available in /usr/lib/mysql. They are not (the folder is there) and builds cannot resolve the references. Am I missing something else? or is something broken with the mysql dev install?

Thanks
BR

---

### Post by treta on 2012-06-27
Using Ubuntu 12.04 LTS

Same problem here.

If you are using 64bit Ubuntu, the location of the libraries are in /usr/lib/x86_64-linux-gnu/

But be warned that you will not be able to compile nothing with libmysqlclient, as every symbol (mysql_init(), etc.) will not be found. (That's the reason I found your question here, looking for a solution) ;)

---

### Post by scott_g on 2012-11-04
I managed to compile something with libmysqlclient after installing the 'libmysqlclient-dev' package from apt-get on Ubuntu 12.04.  

Ie:
```

sudo apt-get install libmysqlclient-dev

```

Hope this helps,
Scott

---

