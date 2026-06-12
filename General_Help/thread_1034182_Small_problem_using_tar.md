---
title: "Small problem using tar"
date: 2009-01-08
forum: General Help
---

### Post by jms1989 on 2009-01-08
Hi, I have a folder or web root, rather, I need to backup. Problem, exclude all subsites and only include just the files needed for the webapp.

The contents, an old drupal install along with a number of subsites.

```

jms1989@compaq-linux:~/domains/www.compaq-web.org/public_html$ ls 
anime          downloads    files     index.php          install.php  LICENSE.txt      misc     phpinfo.php  profiles    sites   torrent_files  Wallpaper
CHANGELOG.txt  favicon.ico  gallery   INSTALL.mysql.txt  INSTALL.txt  mail             modules  poll         robots.txt  tf      update.php     webalizer
cron.php       feeds        includes  INSTALL.pgsql.txt  lg           MAINTAINERS.txt  moviedb  poll.php     scripts     themes  UPGRADE.txt    xmlrpc.php

```

The idea, tar all files related to drupal install.

The reason, to backup before upgrade.

Below is the command I've been trying to use.
```

tar -pczf backup.tar.gz --exclude=anime/ --exclude=downloads/ --exclude=feeds/ --exclude=files/ --exclude=gallery/ --exclude=lg/ --exclude=moviedb/ --exclude=poll/ --exclude=tf --exclude=Wallpaper/ --exclude=webalizer/ --exclude=backup.tar.gz ./

```

The solution should be obvious but from the way I see it, it should be simple. The install isn't that big and yet it wants to create a 100mb+ file.

Help will be appreciated.

---

### Post by Tim Sharitt on 2009-01-08
Since you are pointing tar to the ./ directory, you need to use it in you excludes.
```
tar -pczf backup.tar.gz --exclude=./file ./
```

---

### Post by jms1989 on 2009-01-08
Thank you. It worked. :)

---

