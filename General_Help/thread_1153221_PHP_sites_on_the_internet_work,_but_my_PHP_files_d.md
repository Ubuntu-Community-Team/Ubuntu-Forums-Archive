---
title: "PHP sites on the internet work, but my PHP files don't"
date: 2009-05-08
forum: General Help
---

### Post by Leopardson on 2009-05-08
> Hi, I am trying to learn the basics of PHP.
I have Apache2 + PHP, the PHP extensions work fine on the internet.
HTML files work fine.

Whenever I try to start a .PHP file, it never even loads.

This is some basic code that won't even work:
```

<html>
<body>

<?php
echo "Hello World";
?>

</body>
</html>
```You can paste that in a text file, rename the text file to anything.php, and it should work.
Please try it.

Please help, I am trying to work with PHP, and it's pulling BS on me.


Edit:
Alright, Quanta Plus Preview doesn't show anything at all on PHP files.

Apparently, I stupidly didn't realize it was starting in Bluefish Editor, until I actually looked at the window and saw about 80 tabs called "Index.php".

Whenever I try to open my own PHP files in Firefox, it just opens a "Save file" window.

So...Firefox nor Quanta Plus recognize my PHP. Why?
Thanks to Alterax, the problem was fixed. 
Apparently, I didn't have everything I thought I did. Alterax posted a useful set of instructions that solved the problem completely. (Read post #4 if you have the problem too.)

---

### Post by Alterax on 2009-05-08
Actually, it kind of depends.  You probably know that php files are processed server-side, with the resultant code being presented to the client.  Which means that Firefox doesn't do the processing for PHP code; it must be processed by the PHP module on your apache setup to display correctly.

My assumption is that you're trying to open the file directly with firefox.  If this is the case, then it won't work, as it's not going through the php module on Apache.

Put the .php file into your /var/www folder, and call it up with the address:

[http://localhost/filename.php](http://localhost/filename.php)

If that works, then PHP is working properly.  If not, try enabling the module with sudo a2enmod php or sudo a2enmod php5.

(It's a real pain at first--gave me a bit of a headache until I got it all worked out)

---

### Post by Leopardson on 2009-05-08
Thanks! I had no idea.
I was trying to execute it from my desktop.

Unfortunately, to move something to /var/www/, I need administrative rights in Natilus.
When I type "gksu Natilus", it never starts. How can I start Natilus in Admin mode?

Edit: Doh. It's Nautilus, not Natilus.
Fail.

Edit: The file is called "Index.php".

When I type [http://localhost/index.php](http://localhost/index.php) Firefox still tries to save the file.

I tried a random person's Windows XP, and Firefox opens his PHP files properly.

How can I get Firefox to stop trying to save the file?

It's acting like a guy trying to drive a horse.


Edit: 
I tried using Opera. It also requests I download the PHP file.
I tried using "gksu Firefox" just in case it was a permissions problem.

It is neither of the browsers. Why can't I view the files?


Edit: 
I tried " sudo a2enmod php5", but got "Module Php5 already enabled".

---

### Post by Alterax on 2009-05-08
Got a better idea.  Make a directory in your home directory called php.  Put your PHP files into it.
Then, use these commands:
```
chown www-data:www-data ~/php
chmod -R 777 ~/php

```
Next, let's make a snazzy little softlink so that your php directory gets picked up by Apache2:

```
sudo ln -s ~/php /var/www/.

```

Finally, just to make sure you have all the php stuff needed:
```
sudo apt-get install apache2 php5 libapache2-mod-php5
sudo /usr/sbin/a2enmod php5
sudo /etc/init.d/apache2 restart
```

Now you will be able to browse to [http://localhost/php/yourfilename.php](http://localhost/php/yourfilename.php) to view it, and edit the file from the php directory you made.

---

### Post by Leopardson on 2009-05-08
It works!
Thanks!

---

