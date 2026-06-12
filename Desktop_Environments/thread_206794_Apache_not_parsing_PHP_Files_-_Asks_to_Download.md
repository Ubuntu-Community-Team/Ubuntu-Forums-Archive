---
title: "Apache not parsing PHP Files - Asks to Download"
date: 2006-06-30
forum: Desktop Environments
---

### Post by v8YKxgHe on 2006-06-30
Hey, 

I think, I have PHP/Apache working - MySQL ...... geeee =\ what a load of **** that is, still doesn't work. Will someone help me to install MySQL aswell ( I need to get LAMP working for work, and this is the second day now i've been trying to get it working, driving me crazy ). 

Ok, my main problem is that when I go to, eg localhost/index.php it will ask me to download the file instead of displaying it. I think this has something to do with /etc/apache2/httpd.conf ? I had a look in there, and there is only 6 lines all of which are commented out. I thought httpd.conf was suppose to be like 1000+ lines long? 

Please will someone help me, 2 full days of getting LAMP to work is driving my insane ..... pwease :-({|=

---

### Post by jujoje on 2006-06-30
Hi,

Been trying to setup a lamp server myself. Being a bit of a noob at this kinda thing I'm not sure what the problem is. I did have the same problem but I'm not sure how I fixed it #-o  . 

However the guide on howto forge seemed to work well, so it might be worth having a look at how they set it up, particularly the php section. 

The link is
[http://www.howtoforge.com/perfect_setup_ubuntu_6.06]("http://www.howtoforge.com/perfect_setup_ubuntu_6.06")

There's also some stuff on the ubuntu wiki about setting a lamp server up.

Hope that helps.

---

### Post by az on 2006-06-30
[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

---

### Post by v8YKxgHe on 2006-07-01
Azz, that's the guide i've followed 6 times - all with no luck. Jujoje I shall check that link out now, thanks,

---

### Post by v8YKxgHe on 2006-07-01
Well geeee, even that guide Jujoje doesn't work. Why can things just not work ffs, this is my 3rd day of trying to get LAMP to work with no luck on any of them. I thought Linux was suppose to be great as a server? In XP it took me 10 mins to get Apache/MySQL and PHP working, compare that to 3 days in Linux.

---

### Post by az on 2006-07-01
Are you using php4 or php5?

---

### Post by v8YKxgHe on 2006-07-01
I'm using PHP5, well trying to

---

### Post by az on 2006-07-01
What does 
sudo a2enmod php5
say?

If it does not say that it is already loaded, then that was your problem.

sudo /etc/init.d/apache2 restart

---

### Post by v8YKxgHe on 2006-07-01
It said, 

> Module php5 installed; run /etc/init.d/apache2 force-reload to enable

So I do force-reload and it worked! BUT when I go to localhost/phpmyadmin it says ( FRom Firefox )

> You have chosen to open:

which is a PHTML file
from: [http://localhost](http://localhost)

What do you want to do, Save/Open

EDIT: I just tried a2enmod mysql to see if mysql was working, and I get this:

> alex@alex-ubuntu:~$ sudo a2enmod mysql
This module does not exist!

So I go to install it and I get this:
> alex@alex-ubuntu:~$ sudo apt-get install mysql
Reading package lists... Done
Building dependency tree... Done
Package mysql is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package mysql has no installation candidate


Now i'm confused

---

### Post by mumushi on 2006-07-01
>  alex@alex-ubuntu:~$ sudo apt-get install mysql
Reading package lists... Done
Building dependency tree... Done
Package mysql is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package mysql has no installation candidate


I got the same error message. I installed the LAMP server :(

---

### Post by az on 2006-07-01
Well, the packages you need are detailed on that page:
mysql-server
libapache2-mod-auth-mysql
php5-mysql

You do not need to enable a mysql apache module.


I just installed apache2, php5 and mysql and then popped drupal onto that box and I can connect to it fine.

I did not have to do any fiddling.  The config that comes with those packages is all set up for you.  You must have tried to install both php4 and php5 at the same time or something like that to screw up some otherwise default config.  

So are you sure that all the packages mentioned on the wiki page are installed?

---

### Post by v8YKxgHe on 2006-07-02
Atleast i´m not the only one then!

Edit: Never saw Azz´s post - yes they are all installed. I did try to install PHP 4 to begin with etc, so I think this has messed it up. Would it be possible for you to post most of your configuration files so that I can copy them over to mine?

---

### Post by az on 2006-07-02
[QUOTE=AlexC_]Atleast i´m not the only one then!

Edit: Never saw Azz´s post - yes they are all installed. I did try to install PHP 4 to begin with etc, so I think this has messed it up. Would it be possible for you to post most of your configuration files so that I can copy them over to mine?[/QUOTE]
And what happens when you run

sudo a2enmod php5

---

### Post by v8YKxgHe on 2006-07-03
[QUOTE=azz]And what happens when you run

sudo a2enmod php5[/QUOTE]

Woops, I forgot to say - I reinstalled Ubuntu yesterday and when I came to install LAMP via that guide, it worked straight away. Well the only thing I can't do is add a new user to mysql - but I can still login via root to phpmyadmin. I must of messed some things up while trying all the different guides. 

Thanks =)

---

### Post by az on 2006-07-03
[QUOTE=AlexC_]Woops, I forgot to say - I reinstalled Ubuntu yesterday and when I came to install LAMP via that guide, it worked straight away. Well the only thing I can't do is add a new user to mysql - but I can still login via root to phpmyadmin. I must of messed some things up while trying all the different guides. 

Thanks =)[/QUOTE]
mysql -u root

mysql> GRANT ALL PRIVILEGES ON *.* TO 'yourusername'@'localhost' IDENTIFIED BY 'yourpassword' WITH GRANT OPTION;

That adds a new user with a heavy set of permissions.


It used to be that installing LAMP was a chore, then you had to figure out all of the intricacies and interrelationships between Apache (1.3 or apache2?) php (four or five?) and mysql (root or root?)

Now, with the turn-key installer, you are given a working LAMP, but you are not told that you can't have both php4 and php5 at the same time.  You are not told which applications uses php5 or php4.  You are not told how to use the stuff.

So, it is a little more convenient, but still complicated.

I'm gonna put some love into those docs on the wiki.

---

### Post by v8YKxgHe on 2006-07-03
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: NO)

That's what I get when I do mysql -u root. I did this at the start following the guide,  it worked and I manged to set up another user, how ever I can not login with that extra user I created. Nor root like in that error,

---

### Post by az on 2006-07-03
[QUOTE=AlexC_]ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: NO)

That's what I get when I do mysql -u root. I did this at the start following the guide,  it worked and I manged to set up another user, how ever I can not login with that extra user I created. Nor root like in that error,[/QUOTE]
mysql -u root -p

You will have to know the mysql root password.

---

### Post by v8YKxgHe on 2006-07-03
Aye, that works! Thanks very much =)

---

### Post by mumushi on 2006-07-13
azz i see your the person who has knowledge into this server thing. i installed LAMP server on my pc using the ubuntu server disc and everything works well. I have read this thread lately and saw the option of installing GUI i used the code: > sudo apt-get install linux-386 ubuntu-desktop and it did work however after the installation and upon restart it ask me for the screen resolution. Since im not sure if my video card (which is Gforce Fx5500) is supported i selected the 800x600 but unfortunately my screen goes blank... i can't see anything.. what must i do? Your professional advice is highly appreciated. Thanks in advance.

---

### Post by ZHOUND on 2006-07-13
For the PHP problem, make sure apache is starting with SSL.

---

### Post by nix4me on 2006-07-13
The wiki docs for apachephpmysql work fine.  There are 2 commands in the note that most people miss.

```
Troubleshooting

Does your browser ask if you want to download the php file instead of displaying it? If Apache is not actually parsing the php after you restarted it, install libapache2-mod-php4. It is installed when you install the php4 package, but may have been removed inadvertently by packages which need to run a different version of php. You may also need to actually enable it, by doing sudo a2enmod php4 followed by sudo /etc/init.d/apache2 restart
``` 


nix4me

---

### Post by az on 2006-07-13
> **mumushi said:**
> Since im not sure if my video card (which is Gforce Fx5500) is supported i selected the 800x600 but unfortunately my screen goes blank... i can't see anything.. what must i do? Your professional advice is highly appreciated. Thanks in advance.

Boot into recovery mode and run

dpkg -reconfigure -phigh xserver-xorg

and then reboot.  If that does not fix it, please start a new thread about that problem in specific.

---

### Post by matko on 2006-07-26
Hello apache and php gurus.
i have problem that apache doesnt want to download file, but show it as plain text.
> <?php 
// phpSysInfo - A PHP System Information Script
// [http://phpsysinfo.sourceforge.net/](http://phpsysinfo.sourceforge.net/)
// This program is free software; you can redistribute it and/or
// modify it under the terms of the GNU General Public License
// as published by the Free Software Foundation; either version 2
// of the License, or (at your option) any later version.
// This program is distributed in the hope that it will be useful,
// but WITHOUT ANY WARRANTY; without even the implied warranty of
// MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
// GNU General Public License for more details.
// You should have received a copy of the GNU General Public License
// along with this program; if not, write to the Free Software
// Foundation, Inc., 59 Temple Place - Suite 330, Boston, MA  02111-1307, USA.
// $Id: index.php,v 1.73 2004/08/14 11:22:52 webbie Exp $
// phpsysinfo release version number
$VERSION = "2.3";

define('APP_ROOT', dirname(__FILE__));

ini_set('magic_quotes_runtime', 'off');
ini_set('register_globals', 'off');

if (!file_exists('/etc/phpsysinfo/config.php')) {
  echo '<center><b>Error: config.php does not exist.</b></center>';
  exit;
}

require('/etc/phpsysinfo/config.php'); // get the config file

if (!extension_loaded('xml')) {
  echo '<center><b>Error: phpsysinfo requires xml module.</b></center>';
  exit;



where can bee problem. i attach my settings. look at them. if you see also any other mistake please tell me. thank you for help.

some other info
> 
ccc@ch:/var/www$ cat /etc/apache2/mods-enabled/php4.conf
<IfModule mod_php4.c>
#  AddType application/x-httpd-php .php .phtml .php3
#  AddType application/x-httpd-php-source .phps
</IfModule>
ccc@ch:/var/www$ ls /etc/apache2/sites-enabled/
000-default
ccc@ch:/var/www$ cat /var/www/.htaccess
cat: /var/www/.htaccess: Adresár alebo súbor neexistuje
ccc@ch:/var/www$


---

### Post by n.arciss.us on 2006-07-29
I would like to join the fray.

I too have followed all the wikis and posts mentioned concerning setting up LAMP. But apache2 still seems to not handle php files.

All I want to do is set up a server for local web dev, no outside access.

I was able to do this no problem in Breezy but am having one hell of a time in Dapper.

Yahoo!IM:fishbne2

---

### Post by matko on 2006-07-30
i solved it very funny and bad in one. way.
i installed php5 instead of php4. php4 didnt work how you can in previous thread. now i have apache2 + php5 + ssl + mysqlmod + securitymod + all .htaccess and other hints.

---

### Post by dgold1958 on 2006-07-30
You need to uncomment the "Add Application-type" line.  Apache will then parse your php pages

---

### Post by dgold1958 on 2006-07-30
> **matko said:**
> Hello apache and php gurus.
i have problem that apache doesnt want to download file, but show it as plain text.


where can bee problem. i attach my settings. look at them. if you see also any other mistake please tell me. thank you for help.

some other info


Uncomment this line, I misstyped it in my original reply...you can leave the .php3 part off, since you are more than likely never using this extension 

# AddType application/x-httpd-php .php .phtml .php3

---

### Post by n.arciss.us on 2006-07-30
Ok ... I need to get a clean start with this. What's the best way to ensure that all AMP traces are gone so I'll be starting from sqaure one?!

---

### Post by undefined on 2006-07-30
Same as n.arciss.us, I've reinstalled everything (apache2, php, libapache2-mod-php5) so many times, I think I need a fresh start. And I'm not in the mood of reinstalling ubuntu. 
Oh, by the way, I've done everything suggested in this thread, and it doesn't work, it's always the same, it asks me to download the file.
Thx.

---

### Post by n.arciss.us on 2006-07-30
> **n.arciss.us said:**
> Ok ... I need to get a clean start with this. What's the best way to ensure that all AMP traces are gone so I'll be starting from sqaure one?!

Ok ... I unistalled everything.

Installed with:
```
sudo apt-get install apache2 php5-mysql libapache2-mod-php5 mysql-server
```

then tried:
```
sudo a2enmod php5
```

and got this:

```
chris@chris-laptop:~$ sudo /etc/init.d/apache2 force-reload
 * Forcing reload of apache 2.0 web server...                                   apache2: Could not determine the server's fully qualified domain name, using 127.0.0.1 for ServerName
apache2: Could not determine the server's fully qualified domain name, using 127.0.0.1 for ServerName

```

so :!: hits me ... I enter 127.0.0.1 instead of localhost and SUCESS!!  This may have been a giant noob mistake ....

Thanks for all the tips.

---

### Post by undefined on 2006-07-30
Still doesn't work for me ^^U, now even apache2 doesn't answer.

---

### Post by n.arciss.us on 2006-07-30
> **undefined said:**
> Still doesn't work for me ^^U, now even apache2 doesn't answer.

Did you try 127.0.0.1 instead of localhost?

---

### Post by adamkane on 2006-07-30
This is all you need to do:

Apache2/PHP4/MySQL4 (breezy or dapper):
```

sudo apt-get install apache2 php4 mysql-client mysql-server phpmyadmin libapache2-mod-php4 libapache2-mod-auth-mysql php4-mysql

``` 
Apache2/PHP5/MySQL4 (breezy or dapper):
```

sudo apt-get install apache2 php5 mysql-client mysql-server phpmyadmin libapache2-mod-php5 libapache2-mod-auth-mysql php5-mysql

``` 
Apache2/PHP5/MySQL5 (dapper):
```

sudo apt-get install apache2 php5 mysql-client-5.0 mysql-server-5.0 phpmyadmin libapache2-mod-php5 libapache2-mod-auth-mysql php5-mysql

``` 
Reboot (or start mysql manually).

Open phpmyadmin:
[http://localhost/phpmyadmin](http://localhost/phpmyadmin)

Name: root
Pass: [blank]

If this doesn't work, then you may be faced with the reality that you may need to re-install your system.

No one has come up with a way to completely uninstall/re-install LAMP on Ubuntu.

---

### Post by lobo-tuerto on 2008-01-16
> **adamkane said:**
> This is all you need to do:

If this doesn't work, then you may be faced with the reality that you may need to re-install your system.

No one has come up with a way to completely uninstall/re-install LAMP on Ubuntu.

Is this still true????? OMG :confused:

---

### Post by zebog13 on 2008-03-03
here's what i did. with apache2/php5
In my /etc/apache2/httpd.conf I added, below the NameVirtualHost

<IfModule mod_php5.c>
        # If php is turned on, we repsect .php and .phps files.
        AddType application/x-httpd-php .php
        AddType application/x-httpd-php-source .phps

        # Since most users will want index.php to work we
        # also automatically enable index.php
        <IfModule mod_dir.c>
                DirectoryIndex index.html index.php
        </IfModule>
</IfModule>

then sudo /etc/init.d/apache2 restart 

If you are going to install openSSL, or activate ssl certificates, then you gotta a2enmod php5 again

---

