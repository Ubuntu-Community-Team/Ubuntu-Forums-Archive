---
title: "question about symbolic links in /usr/share/dokuwiki/"
date: 2009-02-02
forum: General Help
---

### Post by NinjaWork on 2009-02-02
Hi, I was looking at dokuwiki, which is installed on my system. Here's the following ls printout:

```

drwxr-xr-x   5 root root  4096 2009-01-30 12:32 .
drwxr-xr-x 384 root root 12288 2009-02-01 14:10 ..
drwxr-xr-x   2 root root  4096 2009-01-30 12:32 bin
lrwxrwxrwx   1 root root    13 2009-01-30 12:32 conf -> /etc/dokuwiki
lrwxrwxrwx   1 root root    22 2009-01-30 12:32 data -> /var/lib/dokuwiki/data
-rw-r--r--   1 root root  2080 2008-05-05 13:10 doku.php
-rw-r--r--   1 root root 10624 2008-05-05 13:10 feed.php
-rw-r--r--   1 root root  1533 2008-10-08 09:36 .htaccess
drwxr-xr-x   6 root root  4096 2009-01-30 12:32 inc
-rw-r--r--   1 root root   185 2008-05-05 13:10 index.php
-rw-r--r--   1 root root 16038 2008-05-05 13:10 install.php
drwxr-xr-x   7 root root  4096 2009-01-30 12:32 lib
-rw-r--r--   1 root root    47 2008-10-08 09:36 prepend.php

```

I'm confused about the symbolic links. Is this program meant to be aliased in apache and run straight from /usr/share/dokuwiki/ ? When I have installed on a web server before I just copied the whole package into public_html.

Thanks for any insights

---

### Post by whitegourd on 2009-02-03
A symbolic link is similar to a shortcut in windows.  It can point to either a directory or another file.  If you're modifying the "conf" file in that directory, you're actually modifying the /etc/dokuwiki file.

---

### Post by NinjaWork on 2009-02-04
Thanks for the reply, whitegourd. Where I'm getting a bit confused is how does Dokuwiki or Drupal run from /usr/share ...I always thought web apps run from public_html in a home directory.

---

### Post by NinjaWork on 2009-02-04
I think this is it...when you copy from /usr/share/dokuwiki into the web directory, the symbolic links are also copied over, so:

```

conf -> /etc/dokuwiki
data -> /var/lib/dokuwiki/data

```

meaning conf info is stored in /etc and data in /var

correct?

---

### Post by whitegourd on 2009-02-05
yes.

---

### Post by NinjaWork on 2009-02-05
> **whitegourd said:**
> yes.

ah, thank you! I'm kind of catching on now ;)

---

### Post by whitegourd on 2009-02-05
No problem.  More detail is in this guide too if you want to take some time to read it.  I find it very helpful.

[http://www.ubuntupocketguide.com/aboutthebook.html](http://www.ubuntupocketguide.com/aboutthebook.html)

---

