---
title: "web and database integration"
date: 2006-08-29
forum: Desktop Environments
---

### Post by dmizer on 2006-08-29
okay, i'm in need of some advice for a workable solution that i'm not too sure how to tackle.

per japanese custom, my office has an obscene number of business cards.  we use those religiously in order to keep track of who we do business with.  but these business cards are physical records, and it's time consuming to hunt through them all in order to find the contact we desire.

so, what i would like to do is provide a web interface where these business card records can both be entered and searched according to various parameters such as name, company name, phone number etc.

once upon a time i created a database with pascal (something over 15 years ago), so i'm basically starting fresh.  i realize i will need a database of some sort, but i'm not familiar with what's available in ubuntu.

is there something out there already pre packaged that can do this type of function (something like gallery1.5 is to pictures)?  or will i need a combination of software?  (keeping in mind of course that all records will be entered in japanese)

our office is currently set up with an ubuntu dapper raid server that's basically only hosting samba shares.  it has plenty of room to add the needed software for apache etc.

---

### Post by Paul41 on 2006-08-29
You could use MySQL for the database.  For the web app front end you have several options.  I use php, but you could also use pearl, Ruby on Rails (there are others I am sure I am leaving off).  Sorry but I don't know how well any of these work with Japanese.

---

### Post by FuriousLettuce on 2006-08-29
Apache 2, MySQL & PHP are the normal route for big, cheap-deployment solutions. Although the code will have to be written in english, japanese characters within the database themselves should be no trouble.

---

### Post by nikhilk on 2006-08-29
> **FuriousLettuce said:**
> Apache 2, MySQL & PHP are the normal route for big, cheap-deployment solutions.

I have worked with Apache, PostgreSQL and PHP which has worked well to. Don't know much about MySQL, but I am activly involved in postgres development, maintainence etc, hence I can say this "PostgreSQL is a really impressive product".

---

### Post by az on 2006-08-29
Egroupware?

It's even in the repositories...

[http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=egroupware&searchon=names&subword=1&version=dapper&release=all](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=egroupware&searchon=names&subword=1&version=dapper&release=all)

---

### Post by dmizer on 2006-08-29
okay ... that's a fantastic start.

i do already have php and apache installed as i was anticipating the need.

from what i've seen of mysql, it's well beyond what i can pick up in a few days study.  how does PostgreSQL (which i've never heard of) and Egroupware compare?

don't know much about configuring php as a frontend either, but i think i could wedge my head around it with a few good tutorials ... much appreciated if someone could point me in that direction.

---

### Post by indytim on 2006-08-29
dmizer,

MySQL isn't hard to tackle.  If you are at all familiar with basic sql syntax, should be no problem.  Would recommend that you get-install phpMyAdmin AFTER you install the MySQL server.  Will make administering any MySQL databases a whole lot easier than the console, especially if you are just starting out.

Good Luck,

IndyTim

---

### Post by az on 2006-08-29
Why reinvent the wheel?  There are tons of web applications that do exactly what you need.  Egroupware is just one example.

You certainly do not have to write a web application from scratch just to keep a shared address book on your lan.

---

### Post by Roger Mudd on 2006-08-29
Evolution + LDAP?

---

### Post by dmizer on 2006-08-29
i'm all for not reinventing the wheel too.

i took a look at Egroupware last night. it's definitely something similar to what i'm looking for. it has a very cool addressbook function. but my problem with egroupware is that it seems to come along with a lot of extra bulk that i won't be needing.  of course, it lends itself more easily to future expansion that way though, so i'm continuing to look into it.

as far as evolution + ldap, won't evolution require a window manager to be installed (something i'd prefer to avoid)

something i'm concerned about is the organizing (japanese version of alphabetizing) the content so it's easier to find.  will something like egroupware (which appears to only have about 15% integration with japanese as of now) be able to handle the content in an organized manner?

edit:
also just noticed that egroupware's japanese doesn't seem to be there.  only 12% integration, and that's mostly developer tools.  i'll need the interface to be in japanese.

---

### Post by nikhilk on 2006-08-30
Basically you would be looking at some sort of CMS (Content Management System) product if you do not want to build the system from scratch. Almost everyone of such systems is made up of the same building blocks viz. Apache, PHP and a database system (usually MySQL).

You have a plethora of options if you decide to go for a CMS. But it wont be a bare bones system and will come with lot of features which you may or may not require.

I do not know much about this CMS stuff but I have heard a lot about Joomla. You may want to try that out [www.joomla.org](www.joomla.org)
Just google for CMS and you will find more options than you possibly need :)

HTH

---

### Post by ayoli on 2006-08-30
@dmizer:
Did you consider other groupware solutions, like [http://phpgroupware.org/](http://phpgroupware.org/) [http://www.opengroupware.org/](http://www.opengroupware.org/) [http://www.hula-project.org/Hula_Project](http://www.hula-project.org/Hula_Project) 
these are just some, you can find a complete list [here]("http://en.wikipedia.org/wiki/List_of_collaborative_software")
I guess they have all some functions you don't need as you said for egroupware, but i dont think you 'll find a 'simple' web app that do only what you want.
regards.

---

### Post by dmizer on 2006-08-30
well, i found this: [http://www.corvalis.net/address/](http://www.corvalis.net/address/) which is more like what i'm looking for, but the problem with that (as well as egroupware and many of the others mentioned) is that the user interface is not translated into japanese.

---

### Post by ayoli on 2006-08-31
> **dmizer said:**
> well, i found this: [http://www.corvalis.net/address/](http://www.corvalis.net/address/) which is more like what i'm looking for, but the problem with that (as well as egroupware and many of the others mentioned) is that the user interface is not translated into japanese.
maybe you can try to make a translation for that, could be more useful than writing a whole app (that already exists).
regards.

---

### Post by dmizer on 2006-09-01
well, translating is significantly beyond my ability, but i could probably manage with some assistence.  but i'm running into other problems as well.  japanese characters aren't being handled well by sql.  sometimes i can search with kanji, but most of the time i get the following on search quiry's:
```

Warning: Attempt to assign property of non-object in /var/www/address/search.php on line 37

Warning: Cannot modify header information - headers already sent by (output started at /var/www/address/search.php:37) in /var/www/address/search.php on line 114
```

---

### Post by dmizer on 2006-09-05
i thought maybe this was an encoding issue where mysql didn't have the required character sets to recognize the kanji, but apparently that's not the case:
```
mysql> SELECT character_set_name, description
    -> FROM information_schema.character_sets
    -> WHERE description LIKE '%Chinese%'
    -> OR    description LIKE '%Japanese%'
    -> OR    description LIKE '%Korean%'
    -> ORDER BY character_set_name;
+--------------------+---------------------------+
| character_set_name | description               |
+--------------------+---------------------------+
| big5               | Big5 Traditional Chinese  |
| cp932              | SJIS for Windows Japanese |
| eucjpms            | UJIS for Windows Japanese |
| euckr              | EUC-KR Korean             |
| gb2312             | GB2312 Simplified Chinese |
| gbk                | GBK Simplified Chinese    |
| sjis               | Shift-JIS Japanese        |
| ujis               | EUC-JP Japanese           |
+--------------------+---------------------------+
8 rows in set (0.00 sec)

```
according to mysql homepage, these are the required character sets for reading japanese.

edit to add the referenced code from the error.

here is the section of the file refered to in the second error re: line 114:
```
<?php
        }
                else {
                header("Location: " . FILE_ADDRESS . "?id=$contact_id");
                }
        exit;
    }

?>

```

---

### Post by ayoli on 2006-09-05
try add at line 0 of this script:
```
ob_start();
```
and at last line:
```
ob_end_flush();
ob_clean();
```

---

### Post by dmizer on 2006-09-06
okay ... that helped me nail the problem.  it would appear that the script is written with iso-8859-1 encoding in mind, but my server does not have the ability to support it.

how can i install the encoding on a server without x installed?

---

