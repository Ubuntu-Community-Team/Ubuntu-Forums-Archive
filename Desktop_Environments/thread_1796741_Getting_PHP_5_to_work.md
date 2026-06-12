---
title: "Getting PHP 5 to work??"
date: 2011-07-04
forum: Desktop Environments
---

### Post by blackasnight on 2011-07-04
Hi,
I have installed php5under Apache and addedmysql also. My problem is I have acreated a file in var/www called testphp.php and try to run it from a command prompt. Keep being told it cant find it! It only has one line running info.php. Keeps saying there is a swp file of this name in var/www. How do I delete this and get my copy of php working properly? Any help would be most appreciated.
A Newbie
Rick Stewart

---

### Post by pAsM on 2011-07-05
> **blackasnight said:**
> Hi,
I have installed php5under Apache and addedmysql also. My problem is I have acreated a file in var/www called testphp.php and try to run it from a command prompt. Keep being told it cant find it! It only has one line running info.php. Keeps saying there is a swp file of this name in var/www. How do I delete this and get my copy of php working properly? Any help would be most appreciated.
A Newbie
Rick Stewart

Hello,
[INDENT]It seems you posted this in the wrong section, but try running this

sudo apt-get install php5-cli php5 apache2 phpsysinfo

Once done, restart apache and run a test in the terminal with

php /var/www/info.php


You can also browse to [http://localhost/phpsysinfo](http://localhost/phpsysinfo) to test a full page
[/INDENT]

---

