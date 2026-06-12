---
title: "problem with source.list"
date: 2007-03-06
forum: Desktop Environments
---

### Post by cybernet on 2007-03-06
[http://img220.imageshack.us/img220/6707/screenshotba0.png](http://img220.imageshack.us/img220/6707/screenshotba0.png)

after add this : [http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/XGL#Adding_the_Beryl_Project_repositories](http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/XGL#Adding_the_Beryl_Project_repositories)
gives the error in the screenshot 
why ??:( 
please help
my english is bad sory for that

---

### Post by nyinge on 2007-03-06
I think you will need to add the keys properly.  If you've done it, try again and watch for any errors.

```
[FONT=monospace]
[/FONT]$ wget [http://ubuntu.beryl-project.org/root@lupine.me.uk.gpg](http://ubuntu.beryl-project.org/root@lupine.me.uk.gpg) -O- | sudo apt-key add -[FONT=monospace]
[/FONT]$ wget [http://download.tuxfamily.org/3v1deb/DD800CD9.gpg](http://download.tuxfamily.org/3v1deb/DD800CD9.gpg) -O- | sudo apt-key add - [FONT=monospace]
[/FONT]$ wget [http://www.beerorkid.com/compiz/quinn.key.asc](http://www.beerorkid.com/compiz/quinn.key.asc) -O - | sudo apt-key add -

```

---

