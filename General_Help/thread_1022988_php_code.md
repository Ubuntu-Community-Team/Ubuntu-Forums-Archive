---
title: "php code"
date: 2008-12-27
forum: General Help
---

### Post by garrynigel on 2008-12-27
hi i wanted to learn php and learn a bit of web designing...and i needed to run the php code how do i go about it..i installed the php5 server thru the repo.. and now want to run d code .. which text editor do i use.. can i run it on d terminal.. how do i do dat..?

---

### Post by cariboo on 2008-12-27
I would suggest installing the LAMP server to get the full benefit of php. To do this go to System-->Administration-->Synaptic Package Manager-->Edit-->Mark Packages by Task and select LAMP from the menu for installation.

Jim

---

### Post by garrynigel on 2008-12-27
dude but how do irun d code 
wat do i use .. d terminal or wat text editor

---

### Post by x1a4 on 2008-12-27
Hi,
Use PHP inside html pages with a php extension.  The code is than processed by a the PHP interpreter running on top of a web server, so install Apache.  When you have Apache installed open [http://localhost/](http://localhost/) in your browser.  

Use whatever editor you like.  A good editor is [medit]("http://mooedit.sourceforge.net/") which is in the repositories.  Also, jEdit and NEdit are quite good.  phpEdit is a web development IDE with focus for PHP development. You should also visit [php.net]("http://www.php.net") to find out what PHP is and how to use it. 

An example of a php script:
```

<?php
$conn=mysql_connect('localhost', 'db_name', 'db_pass',FALSE) or die('Error: Could not connect to database: '.mysql_error());
$db=mysql_select_db('db_name',$conn) or die('Error: Could not select database');
$query=mysql_query('select `id`,`date`,`news` from `table_name` order by `date` desc') or die('Error: Database query (query) failed: '.mysql_error());
$page_title="Funky page title";
/*   Some more PHP code goes here   */
?>
<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.0 Transitional//EN"
        "http://www.w3.org/TR/REC-html40/loose.dtd">
<html lang="en-CA">
  <head><title><?php  echo $page_title   ?></title>
    ...
    /*   Some PHP code may go here   */
  </head>
  <body>
    ...
    <?php
    /*   Some PHP code may go here   */
    ?>
  </body>
</html>
<?php
mysql_free_result($query);
/*   Some PHP code may go here   */
?>

```

---

### Post by Iowan on 2008-12-27
My LAMP installation did not come with CLI PHP enabled (I haven't checked to see if a module will enable it or not). I've done editing with **nano** - not fancy, but comes with server, and works. You can try something as simple as:
<?php
phpinfo();
?>
Save it with .php suffix.  I can't remember if I had to change anything in the configuration.

---

### Post by hyper_ch on 2008-12-27
(1) you need apache
(2) you need libapache2-mod-php5
(3) you need to enable the php5 module for apache
```

sudo a2enmod php5

```

---

