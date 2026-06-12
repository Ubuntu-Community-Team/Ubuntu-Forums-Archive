---
title: "Some PHP Pages Display, Others Don't?"
date: 2009-06-05
forum: General Help
---

### Post by sleestak on 2009-06-05
Yesterday >> last night, I got my LAMP install all set up for use as a dev box in my home.

I have configured Apache with Virtual Hosts via: available - enables sites, restarted apache, set up my hosts file on my PC and also a Samba share to /var/www   so far so good.

I have tested all the site folders and they are displaying an index.html just fine. Then I dropped an index.php file in just output the version of PHP ... all good in all the sites. But as soon and I migrated the files of one of my sites into its site folder, I get errors:

```


Warning: Unknown: failed to open stream: Permission denied in Unknown on line 0



Fatal error: Unknown: Failed opening required '/var/www/jasonstumpf/index.php' (include_path='.:/usr/share/php:/usr/share/pear') in Unknown on line 0


```


I am pretty sure something has to be awry with my server set up, because these exact files display just fine on [www.jasonstumpf.com](www.jasonstumpf.com)  - which is hosted on another box.

Anyone have any ideas? I would GREATLY appreciate the help ... this is my first stab at setting up a dev box for web, so please be gentle, lol. ):P

---

### Post by Celauran on 2009-06-05
Do the pages call any PEAR modules that may not be installed? Are the permissions on index.html and index.php the same?

---

### Post by sleestak on 2009-06-05
There was nothing special about the pages, just some simple includes.

As it turns out, it was a permissions thing. I dragged the files over from Windows (I am sharing /var/www via Samba) and they just needed to be made 755.  It's the simple things that get you ... I must have been looking at this too long. 

Thanks a ton!

---

