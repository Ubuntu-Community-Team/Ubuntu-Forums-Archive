---
title: "php install not working"
date: 2009-02-05
forum: General Help
---

### Post by vegardlr on 2009-02-05
I want to start developing php pages on my laptop so I have tried for some time now to install apache2 and php5 on my laptop.I've followed many HOWTO's, of the more detailed ones is [this (Slicehost Articles: Ubuntu Hardy: Installing Apache and PHP5)]("http://articles.slicehost.com/2008/4/25/ubuntu-hardy-installing-apache-and-php5").

The simple test of navigated to the designated server [http://localhost](http://localhost) to confirm that Apache is correctly installed checked out. So apparantly, apache2 is good.

Still I'm not able to see php when loaded in my web browsers.I'm using the following test.php file: 
[INDENT]
<html>
<body>
html hello

<?php
	echo "Hello php";
	phpinfo();
?>

</body>
</html>
[/INDENT]

And the result in Epiphany Web Browser is just "html hello". Firefox for some reason is not able to load some php files in general (yet another problem I do not intend to discuss here now, unless someone now what is wrong with firefox, bug perhaps).

I'm running Ubuntu Inteprid Ibex, Kernel: 2.6.27-11-generic, x86.

Thanks!
Vegard

---

### Post by howlingmadhowie on 2009-02-05
have you restarted apache since installing modphp? (sudo /etc/init.d/apache2 restart)

can you install the command line interface to php (sudo apt-get install php5-cli) and try running your program through it? (navigate to the file in a shell and then enter php test.php)

how are you opening the file? what address are you calling? something like [http://localhost/test.php](http://localhost/test.php) ?

---

### Post by vegardlr on 2009-02-05
Hi howlingmadhowie

> **howlingmadhowie said:**
> have you restarted apache since installing modphp? (sudo /etc/init.d/apache2 restart)

Yes. Sorry for not saying so in my previous thread.

> **howlingmadhowie said:**
> 
can you install the command line interface to php (sudo apt-get install php5-cli) and try running your program through it? (navigate to the file in a shell and then enter php test.php)

Done, the result is (when i first commented out the line with phpinfo();):
```

vegard@alfven:~/Dokumenter/HTML/PHP$ php test.php 

<html>
<body>
html hello

Hello php
</body>
</html>

```

The output of "php test.php" without first removing the phpinfo() can be seen at this [link]("http://uteligger.org/vegard/linux/output.txt").

> **howlingmadhowie said:**
> 
how are you opening the file? what address are you calling? something like [http://localhost/test.php](http://localhost/test.php) ?

I'm opening the file with the addres *file:///home/vegard/Dokumenter/HTML/PHP/test.php*. 

Thanks for a quick reply!
Vegard

---

### Post by howlingmadhowie on 2009-02-05
> **vegardlr said:**
> 

I'm opening the file with the addres *file:///home/vegard/Dokumenter/HTML/PHP/test.php*. 

Thanks for a quick reply!
Vegard

and there's your problem!

firefox or epiphany don't know what php code means, but apache does. you have to open the document through the apache webserver. 

you recall you went to [http://localhost](http://localhost) and saw "It works" in your web-browser? that was a document which was delivered to you by the apache webserver. now epiphany and firefox are also able to open documents on your hard drive, but they only understand html and css and stuff, they don't understand php or python or perl or whatever language you use to generate the webpages. however apache does understand these languages (if you have the right module installed), so you can get apache to translate or process the php code and make html code out of it.

if you enter [http://localhost](http://localhost) in your browser, apache will send your browser a file at either /var/www/index.html or /var/www/index.php (seeing as you have the php module installed). so go to /var/www and create a folder called 'mywebpages' or something (you'll need to sudo this, because a standard user can't create files in /var/www) and save your file test.php in the new folder. the path to the folder according to your operating system is now /var/www/mywebpages/test.php and according to apache [http://localhost/mywebpages/test.php](http://localhost/mywebpages/test.php)

now apache will find the file and translate the php code into html and your browser will display it correctly :)

---

### Post by vegardlr on 2009-02-05
:D ;) :)

Fantastic! Thanks a bunch for your help. Now I can start to play around with php, finally!

With the best regards, Vegard.

---

