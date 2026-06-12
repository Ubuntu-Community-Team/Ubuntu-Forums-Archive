---
title: "Noob trying to install Quake4"
date: 2006-06-02
forum: Gaming &amp; Leisure
---

### Post by the_FNG on 2006-06-02
Hi, 
First off, I'm about as green as they come, and seem to be having some difficulty installing Quake4.  So far, I've downloaded the latest linux file for it (quake4-linux-1.2.1.x86.run) but of the life of me can't get this thing started.  I've tried:
```
chmod +x /home/me/Desktop/quake4-linux-1.2.1.x86.run
```
like I googled here: [http://schelstraete.dyndns.org/tiki-read_article.php?articleId=23](http://schelstraete.dyndns.org/tiki-read_article.php?articleId=23)
but found it didn't do anything.  As well, I've found this: [http://zerowing.idsoftware.com/linux/quake4/](http://zerowing.idsoftware.com/linux/quake4/) but so far it doesn't make much sense since can't even get it started (however, I do understand about copying the pak files).  I also found this helpful tutorial: [http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/) but it really never mentioned about run files.

Actually this is the first time I've really attempted to install anything on linux, and would really find this game handy for blowing off steam while i get aquainted with this  awesome new OS.

Thanks in advance people, and if you can dumb it down a shade for now, I certainly won't be offended  :-D

---

### Post by Gnobody on 2006-06-02
[quote=the_FNG]Hi, 
First off, I'm about as green as they come, and seem to be having some difficulty installing Quake4.  So far, I've downloaded the latest linux file for it (quake4-linux-1.2.1.x86.run) but of the life of me can't get this thing started.  I've tried:
```
chmod +x /home/me/Desktop/quake4-linux-1.2.1.x86.run
``` like I googled here: [http://schelstraete.dyndns.org/tiki-read_article.php?articleId=23]("http://schelstraete.dyndns.org/tiki-read_article.php?articleId=23")
but found it didn't do anything.  As well, I've found this: [http://zerowing.idsoftware.com/linux/quake4/]("http://zerowing.idsoftware.com/linux/quake4/") but so far it doesn't make much sense since can't even get it started (however, I do understand about copying the pak files).  I also found this helpful tutorial: [http://monkeyblog.org/ubuntu/installing/]("http://monkeyblog.org/ubuntu/installing/") but it really never mentioned about run files.

Actually this is the first time I've really attempted to install anything on linux, and would really find this game handy for blowing off steam while i get aquainted with this  awesome new OS.

Thanks in advance people, and if you can dumb it down a shade for now, I certainly won't be offended  :-D[/quote]

after you chmod it to make it executable type the following in a terminal: 
/home/me/Desktop/./quake4-linux-1.2.1.x86.run

or double click it, and select "run in terminal".

---

### Post by Gnobody on 2006-06-02
Also, you may need libgtk1.2 because the Loki installers use gtk version 1.2 (which is really old, and not included in Ubuntu).  In which case, open a terminal and type:

sudo apt-get install libgtk1.2

---

### Post by bschelst on 2006-06-07
[QUOTE=the_FNG]Hi, 
First off, I'm about as green as they come, and seem to be having some difficulty installing Quake4.  So far, I've downloaded the latest linux file for it (quake4-linux-1.2.1.x86.run) but of the life of me can't get this thing started.  I've tried:
```
chmod +x /home/me/Desktop/quake4-linux-1.2.1.x86.run
```
like I googled here: 
[/QUOTE]


First you need to go in your KDE or GNOME console (konsole, xterm)
And then type:

#> sh /home/me/Desktop/quake4-linux-1.2.1.x86.run

or 
#> chmod +x  /home/me/Desktop/quake4-linux-1.2.1.x86.run
#>  /home/me/Desktop/quake4-linux-1.2.1.x86.run


rgrds,

   Bart

---

