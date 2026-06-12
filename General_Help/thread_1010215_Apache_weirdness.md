---
title: "Apache weirdness"
date: 2008-12-13
forum: General Help
---

### Post by cuzz on 2008-12-13
I just set up a new install, and one of the first thing I do is set up lamp and install php wiki. I generally do this in ~/public-html/wiki but decided on this box I would install it in /var/www. The problem is when I try to access localhost/wiki the download dialog pops up and is looking to download the index.php file. Figured there may be something wrong with the download so started over, same issue. Here is where it gets weird, if I rename the wiki directory to anything else, like wiki2, it works fine.

Scratching head at an unbelievable pace.

Any thoughts?

installed wiki download [phpwiki-1.2.11]("http://sourceforge.net/project/showfiles.php?group_id=6121&package_id=14187&release_id=585044")

---

### Post by cariboo on 2008-12-13
Does your /etc/apache2/mods-available/dir/conf look like this?

```
<IfModule mod_dir.c>

          DirectoryIndex index.html index.cgi index.pl index.php index.xhtml index.htm

</IfModule>
```

Jim

---

### Post by lordadi on 2008-12-13
I think the issue is that Apache doesn't know it has php installed -- happened to me too.

I believe it can be fixed by doing

```
sudo a2enmod php5
```

and then

```
sudo /etc/init.d/apache2 restart
```

But that still wont explain why it happened to me and would work by renaming the folder!!

Lordadi.

---

### Post by cuzz on 2008-12-14
Thanks for the feedback.

/etc/apache2/mods-available/dir.conf

```

<IfModule mod_dir.c>

          DirectoryIndex index.html index.cgi index.pl index.php index.xhtml index.htm

</IfModule>

```

PHP is installed. The thing works fine when it's in a subdirectory with any other name accept 'wiki'. Bounced system, bounced Apache and the issues persists. phpinfo() returns configs with no issues or conflicts. It's just weird!

Going to try the MoinMoin Wiki since it's more dominate in the OS circles. Will post if the same issue prevails.

Does anybody know of a good Apache2 forum where I could post this issue?

---

