---
title: "Apache not running php files"
date: 2005-10-19
forum: Desktop Environments
---

### Post by t_ras on 2005-10-19
Using Apache 2 (well..I seem to somehow have both Apache and Apache2 working...) and it doesn't run PHP files.
I rtyed adding handler and type in apache\httpd.conf and apache2\apache.conf. it doesn't help, browser tryes to d/l the PHP file instead of server running it.
I have Apache2-mod-PHP installed.

Any Ideas?

---

### Post by Psy-Q on 2005-10-19
Did you restart (not just reload) the Apache service after installing the PHP package?

Also, which browser are you using? Firefox has a tendency to cache things a bit too aggressively. If you've fiddled with settings after looking at the page with Firefox, you might not be looking at the actual situation. Maybe what you're seeing is just Firefox's "oh, I've seen this page, let's pop up the download dialog and serve up the file from cache" behavior, when instead it should contact the server. Try emptying the cache or using another browser.

---

### Post by t_ras on 2005-10-19
I stopped apache,apache2,apache-perl and apache-ssl services and then started them again.
the I restarted computer.
I tryed uninstalling apache and leaving only apache2. 
I also tryed from IE in windows computer.
all the same.... :(

(THANKS for helping!!)

---

### Post by invalid on 2005-10-19
I bet that you are trying to view the file by an absolute path, instead of a web-address..

If you point your browser to /some/path/to/file.php - it will try to download.
If you point your browser to [http://your-domain-or-localhost/file.php](http://your-domain-or-localhost/file.php) - it will try to execute the script.

Cheers,
Cb

---

### Post by munitras on 2005-10-19
can you post your config files (apache2.conf, site config maybe even .htaccess)?

---

### Post by t_ras on 2005-10-19
I was trying by my adress [www.terrenis.net/lam](www.terrenis.net/lam) (ldap...)

---

### Post by t_ras on 2005-10-19
hara are my configurations files.

---

### Post by munitras on 2005-10-19
Nothing obvious seems wrong. 
If you have the time to burn you can try:

Comment out the following lines in the apache2.conf
```

AddHandler cgi-script .cgi
AddHandler application/x-httpd-php .php .phtml

```
these are deprecated in the apache2.conf file (see 2 below)

2. Make sure you have a file named php4.conf in /etc/apache2/mods-available *and* /etc/apache2/mods-enabled directories. This is where the AddType will load handlers for php files.

If the file is not in mods-available you'll need to (re)install the php mod for apache2. If it is not in mods-enabled run
```
sudo a2enmod
```
and select the appropriate php module.

**EDIT: I should perhaps mention that mods-enabled merely uses sym-links to files in mods-available. Also confirm that the path to /usr/lib/apache2/modules/libphp4.so in /etc/apache2/mods-available/php4.load is pointing to valid library. Ordinarily these would all be good but perhaps as a result of installing multiple versions of apache things went a little screwy.**

3. Double check that you aren't killing (overriding) settings in either the site specific file (if you aren't using default site) or the .htaccess.

good luck

---

### Post by t_ras on 2005-10-19
all is fine, still doesnt work.
the index.html file of site (/usr/share/ldap-acount-manager/index.html is pretty inosent load of login.php and no other html files there, aslo conf files there says nothing about php.

it is soooooooooooo frustrating....
good to have people helping here...

---

### Post by t_ras on 2005-10-19
might be because I don't have this:
php4-universe-common

---

### Post by Chris Cromer on 2005-10-19
No that's universe, you don't need that.

This is what I had installed for php4:
apache2
apache2-common
apache2-mpm-prefork
apache2-utils
libapache2-mod-php4
php4
php4-common

And this is what I have installed now for php5:
apache2
apache2-common
apache2-mpm-prefork
apache2-utils
libapache2-mod-php5
php5
php5-common

Works great out of the box... although I did have to do some modifying to get mysql, sqlite, and other various things working in php.

---

### Post by oxEz on 2005-10-19
Yea what he said, I fixed that on computer by installing libapache2-mod-php5
```
sudo apt-get install libapache2-mod-php5
```

Good luck!

---

### Post by t_ras on 2005-10-20
the problem is I think LAM needs PHP4...but I'll try, Thanks!

---

### Post by jamyskis on 2005-10-20
It might be a case of permission problems and as such installing libapache2-mod-suphp is worth a try. It's exactly the same problem I had. Under Hoary there appears to be a bug that causes some kind of server error, I don't know if this is the case in Breezy - but delete suphp.conf and suphp.load from /etc/apache2 after you've installed the module.

---

### Post by l.tambiah on 2005-10-20
Hello,

Use the wiki page on LAMP to set up your environment. You can't go wrong with this guide.

[https://wiki.ubuntu.com/ApacheMySQLPHP?action=show&redirect=LAMPForHoary]("https://wiki.ubuntu.com/ApacheMySQLPHP?action=show&redirect=LAMPForHoary")

---

### Post by t_ras on 2005-10-21
I tryed installing php5, I tryed libapache2-mod-suphp, I tryed the wiki pages, it just doesnt work! and I failed to install mail server also....
I think if I'll try to reinstall and if it doesnt work I think I'll just leave Ubuntu (and probblly all debian) it is the best linux desktop by far! but I'm not such a linux hacker (though I do know the basics) and with Fedora I menaged to make it work (the treth is that it worked without me :) ... )
soooooooo frustrating.....I don't wan't to go backt o Fedora :(

---

### Post by KLineD on 2005-10-21
My apache2 server was working in Hoary with PHP, now it always return 404 Not Found even with testphp.php in /var/www

Reading this thread I noticed:

> 
I should perhaps mention that mods-enabled merely uses sym-links to files in mods-available. Also confirm that the path to /usr/lib/apache2/modules/libphp4.so in /etc/apache2/mods-available/php4.load is pointing to valid library. Ordinarily these would all be good but perhaps as a result of installing multiple versions of apache things went a little screwy.


and when I cat /etc/apache2/mods-available/php4.load I get 
```

LoadModule php4_module /usr/lib/apache2/modules/libphp4.so

```

The lib is there, the permissions for the file are 755 (I tried with 777 with no luck) and the owner of the file is root. As I said, this configuration was working before I really don't know what could that be so that I always get a file not found and I'm 100% sure it's there!

Any help is greatly appreciated
[B]
EDIT:[/B] Sorry I feel so dumb, somehow my default root directory changed to /var/www/apache2-default and that's why it could never find anything. I got it running now thanks!

---

### Post by munitras on 2005-10-22
Hi t_ras.

If it is not too late, and you have not already scrapped the box  - then don't give up just yet. 

I have experienced this problem once before. Also after having had both apache and apache2 installed due to a _bad_ upgrade (warty->hoary) on my part. 

I eventually resolved it by removing all apache/apache2 versions/files/configs and then just re-installing the apache2 version, at the time using with php4.

I'll bet it is an apache2 config/setup problem - not php.

Please post current versions of the following files/commands:
1. /etc/apache2/apache2.conf
2. ls /etc/apache2/mods-enabled/
3. cat /etc/apache2/mods-enabled/php4.conf
4. cat ./sites-enabled/000-default *(assuming you are running this on the default site)*
5. cat /var/www/.htaccess
6. cat /var/www/apache2-default/.htaccess
7. ls /etc/apache2/sites-enabled/
8. cat /etc/apache2/sites-available/default *(assuming you are running this on the default site)*

try not to miss any one of the above items.

---

### Post by t_ras on 2005-10-22
I've allready resintalled my system, so I'll do everythin from the beggining...

---

### Post by t_ras on 2005-10-22
ok, now , after resintallig and going through [https://wiki.ubuntu.com/ApacheMySQLP...t=LAMPForHoary](https://wiki.ubuntu.com/ApacheMySQLP...t=LAMPForHoary) I I can run php (installed php5).
just one question - when typing [www.terrenis.net](www.terrenis.net) (my host) I get directory listing of /var/www  how do I denay directory listing?

wel.. maybe two questions: any one knows a good "how to make mail server?"

THanks for all the HELP!!

---

### Post by duminas on 2005-10-22
Look for a line similar to this in httpd.conf:
```
    Options Indexes Includes FollowSymLinks MultiViews ExecCGI
```And change **Indexes** to **-Indexes**, then restart Apache.

---

### Post by l.tambiah on 2005-10-23
When Lamp has been set up successfully your directory on your local machine should be [http://localhost]("http://localhost") which should display your /var/www directory. There should be no reason to go back to Fedora. Have you ever tried to set up apache mysql and php on windows? Its harder to set up than on GNU/Linux believe me.

I did not use php5 i installed php4, i think it is better to use php4 as it is more stable and most hosters at current are also using php4.

If you are having serious problems setting this up, give me a private message and i will help sort it out for you......

---

### Post by t_ras on 2005-10-25
thank you all!

---

### Post by MatthewMetzger on 2005-11-19
"sudo a2enmod" was the solution for me. it asked which mod I wanted to enable and gave me all the options. php4 and php5 were options. I chose php5 and ran:

sudo /etc/init.d/apache2 force-reload

*IMPORTANT* Remember to clear Firefoxes cache. Edit > Preferences > clear cache button. After I did this, Php5 worked fine. Thanks for the help, munitras.

---

### Post by PokerFacePenguin on 2005-11-20
[QUOTE=Chris Cromer]No that's universe, you don't need that.

This is what I had installed for php4:
apache2
apache2-common
apache2-mpm-prefork
apache2-utils
libapache2-mod-php4
php4
php4-common

And this is what I have installed now for php5:
apache2
apache2-common
apache2-mpm-prefork
apache2-utils
libapache2-mod-php5
php5
php5-common

Works great out of the box... although I did have to do some modifying to get mysql, sqlite, and other various things working in php.[/QUOTE]



Out of the box did you have server installed or did you have the default installation with breezy?  or perhaps you upgraded?  I have built a new partition just to try to get this going and installed the gnome ubuntu default install and am still having problems.  My original intent was to install drupal, but that has not worked out so well.  I thought maybe it was due to php not getting loaded up correctly, so i have decided to try to work it out step by step instead of letting drupal install my dependencies.  I throw a little php script in the default directory (/var/www) and try to get it to do a php(info) and now following what you have installed, I am unable to get apache2 to even accept connections from my local machine by going to [http://localhost/](http://localhost/)

For a while there I was under the impression that I was running apache2.  But noticing the bottom of the page when you [http://localhost](http://localhost) I saw apache1.3.33, yet I had apache2 directories from attempting the drupal install (which loads up the mpm prefork).  So I uninstall apache -completely- and reinstall the packages per this forum message.  No web server at all.  Im stumped.

Are there config files that you had to tweek to get the default install to run the web server (apache2)?  I tried PHP4 and PHP5 upgrade.   Not working.

I have never run a website on apache or apache2 before so this is all new to me.



** Update **

Ok, I followed the wiki instructions here [https://wiki.ubuntu.com/ApacheMySQLPHP](https://wiki.ubuntu.com/ApacheMySQLPHP)
except for the following part:
> Edit Apache Configuration

You may want your current user to be the PHP pages administrator. To do so, edit the Apache configuration file :

$ sudo gedit /etc/apache2/apache2.conf

Search both the strings starting by "User" and "Group", and change the names by the current username and groupname you are using. Then you'll need to restart Apache. (look at the next chapter concerning apache commands)

Configuration options relating specifically to user websites (accessed through localhost/~username) are in /etc/apache2/mods-enabled/userdir.conf.


and

 and got the apache2 running (verified by the text at the bottom of the default page)
but the blasted same thing keeps happening....it is trying to download the test.php file.

---

### Post by SuperMike on 2005-11-25
[QUOTE=t_ras]Using Apache 2 (well..I seem to somehow have both Apache and Apache2 working...) and it doesn't run PHP files.
I rtyed adding handler and type in apache\httpd.conf and apache2\apache.conf. it doesn't help, browser tryes to d/l the PHP file instead of server running it.
I have Apache2-mod-PHP installed.

Any Ideas?[/QUOTE]

You weren't having a problem with your libapache2-mod-php(x) file, were you? I was. I think there's a bug. I finally got it to work after multiple attempts to uninstall and reinstall. Here's my story and I hope it helps...

I think I'm seeing a pattern of an undocumented Ubuntu Breezy bug in PHP5 and PHP4 installs with the libapache2-mod-php4 or libapache2-mod-php5. If you uninstall and reinstall multiple times, you'll find that it just sort of works if you repeat the process several times. I had to repeat the same exact process like 5 times on my PC before it just worked. And when you uninstall PHP, it will warn you that libapache2-mod-php(x) didn't get installed in the first place, so it can't remove it.

My running theory here is that either there's a bug in the Canonical web farm with some of the mirror servers we're hitting. I cannot figure out any other reason why the libapache2-mod-php(x) would install one time and not another.

And if you do a search on ubuntuforums.org, you'll find that a lot of people are having this issue. The net effect of this is that even though you have installed Apache2, PHP(x), and libapache2-mod-php(x), and have cleared your Firefox cache, you find that Firefox still asks you what to do with the PHP file, instead of Apache2 pre-processing it at the server. This is because the libapache2-mod-php(x) is failing to be compiled and inserted properly into the Apache2 framework -- even though you can clearly see the various .conf files are properly updated and the libphp(x).so file is in the proper place.

I finally got my PHP4 to work in Breezy. A couple days ago, I also had my PHP5 working too. So it *can* be done. Just keep playing with Synaptic and the install, trying different ways to install it, or install just what you need first and add other extra PHP items you need as you go. You'll find if you keep fighting with it for like 4 hours, it finally just *works*, somehow.

I wish there was a way I could easily report this as a bug to be checked. If you all know where to post this, let me know. The bug can be easily reproduced. Just upgrade from Hoary (with a loaded PHP4 install) to Breezy, and then uninstall completely the PHP4 and/or PHP5. Then, reboot. Then, try to install PHP4 again with Universe option enabled. Or, for that matter, try on a separate PC to install PHP5 again. Both PHP4 and PHP5 will intermittently have the same issue of not compiling the libapache2-mod-php(x) file properly.

I'd also like to know how I can become a tester for Canonical's PHP installs. It sounds like they didn't test this very well and could stand to have a developer help them.

P.S. There's been some discussion about uncommenting some Mime type info in the /etc/apache2/apache2.conf file. You don't have to do that. Here's the real story...

If the Mime type is not uncommented in the apache2.conf file, there's another way to make the conf file look in another directory for adding extra stuff. You'll find the uncommented version in:

/etc/apache2/mods-enabled/php4.conf

or

php5.conf in the same dir.

The installer is supposed to do this for you. However, like I said, it only intermittently compiles the libphp4.so or libphp5.so file (libapache2-mod-php(x)) properly -- you have to fight with the process of uninstallation and reinstallation, along with reboots, until it finally just "takes".

---

### Post by ExemplarUbuntu on 2005-12-09
I thought I had replied to this but can't see my posting.

If you are still unable to get the php files to be parsed by the php
process then edit the apache2.conf and find the line that begins
with "AddType" and ends with ".php"

Uncomment this line and then apache2 -k restart

---

