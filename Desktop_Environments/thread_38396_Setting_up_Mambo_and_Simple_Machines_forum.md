---
title: "Setting up Mambo and Simple Machines forum"
date: 2005-05-31
forum: Desktop Environments
---

### Post by themoddingden on 2005-05-31
Hi;
I'm trying to set up Mambo and Simple Machines Forum  for hosting a small computer store and my own site.
I can view the apache start page but thats it(well i can view it after clicking on the dir it's in).
I have the files for the forum in a folder in a folder called public_html in my home dir.
Do I have to point to these some how in Apache???
or should I move them to the Apache dir or create a short cut in there.
I did a full install in order to use synaptic to install software.
I'm doing this via the gui and all attemps by me to follow the ubuntu guide to add extra sources to my etc/apt/sources list always result in 404 error for the new sources:(
I've tries commenting out the src areas and leaving them in also.
Does anyone have a newer guide for seting all this up or a guess of whats wrong ???
I thank you for all and any help I want to be able to host linux iso's and game demos etc.

---

### Post by kuleali on 2005-05-31
Are you using apache 2 ?

Download mambo to /var/www/apache2-default/

Point your browser to that file and follow the given instructions. use the same instruction for smf forum.


Are you using the bakcports ? Try to use the backport mirrors.

---

### Post by reid on 2005-06-15
themodingden,
Have you figured this out yet?  I am interested to hear your progress, as I am also starting a site with:
1) ubuntu (of course!)
2) mambo
3) smf

Currently I have mambo working, but have not tried to tackle the smf part of it yet.  By working I mean that the mambo content is visible from the internet.

I installed apache(2), MySQL(4.1), and php(4) all from synaptic.  I have the backports repository, not sure if that makes a difference or not for these components.
I will offer whatever assistance I can, there is a lot to learn!


Best of luck,

reid

---

### Post by mtron on 2005-06-15
this  will focus on Apache 1.3. As well, I think Webmin makes setting LAMP up very easy, even though we don't really use it for much. So this howto will include those instructions as well.

Considering the proliferation of Content Managers like Mambo  we will also make changes to allow for these scripts to run locally without impediment.


***********************
Open up your Synaptic, get the [extra repositories](http://ubuntuguide.org/index.html#extrarepositories)  and install the following:


apache
apache-common
apache-utils
libapache-mod-perl
libapache-mod-php4
libapache-mod-ssl
*********
mysql-client
mysql-common
mysql-server
libmysqlclient12
libqt3c102-mt-mysql
libdbd-mysql-perl
php4-mysql
*********
php4
php4-pear
php4-imagick
php4-common
php4-gd2
*******************

Some of the applications already come pre-installed with Ubuntu, and some will include dependancies. As well, you may not want to install php4-imagick, or php4-gd2, but you will find that some scripts (SugarCRM) will want these and others.


*******************

To make things a little easier we work with Webmin. Goto:
[http://prdownloads.sourceforge.net/webadmin/webmin-1.210.tar.gz](http://prdownloads.sourceforge.net/webadmin/webmin-1.210.tar.gz)

and pick your mirror. Once downloaded, extract webmin into a directory of your choice and open a terminal. Goto the extracted webmin directory land type the following:

sudo sh setup.sh /usr/local/webmin

From there follow the prompts, mostly just enter. You may choose your port, uname and password. You may also decide to run Webmin securely - always a good idea. You must have SSLeanet (SP) installed. It's in the repository, or - you can install it when you are in Webmin. As well, you may choose to have Webmin start at boot or no. I choose yes.

If you want to run it as a service, the command to start Webmin when you need it is the following:

sudo /etc/webmin/start to stop it when your finished: sudo /etc/webmin/stop

Everything installed? Good. Close everything. Shake it off.

***********************************

Open a terminal and type the following command as a regular user:
mysqladmin -u root password <password> (pick a <password> instead)

Now start Webmin. You can leave the terminal open. Open your browser and point to: 127.0.0.1:10000 Of course, if you changed the port at installation you would choose that port instead of 10000. As well, if you had ssleanet installed already and webmin installed allowing secure browsing, you would point to this address:

[https://127.0.0.1:10000](https://127.0.0.1:10000)

*********************************

Navigate to the SERVERS aspect of Webmin. You will see Apache and 2 below it you will see MySQL. Click on Apache. The first screen you see will "confirm" your modules. You should see "php4" and a few others. Choose OK. If you don't see what you want, it might be installed with Apache anyway. This howto is limited. Next screen you will see your Apache modules, at the top of your screen you will see commands to Apply Changes, Stop/Start Apache, etc. Stop Apache.

You will see an icon for "edit config files" Click that. There are 4 or 5 things to change. I only change enough to run Mambo sites, and cgi scripts locally. I'm no Apache expert.


Scroll down in the config file until you come to this section:

# First, we configure the "default" to be a very restrictive set of
# permissions.
#
<Directory />
Options SymLinksIfOwnerMatch
AllowOverride None <<<<<<<<<<change None to read: All
</Directory>


Goto this section next:
# This controls which options the .htaccess files in directories can
# override. Can also be "All", or any combination of "Options", "FileInfo",
# "AuthConfig", and "Limit"
#
AllowOverride None <<<<<<<<<<<<<<change None to All

next:

<IfModule mod_dir.c>
DirectoryIndex index.php index.html index.htm index.shtml index.cgi
</IfModule>

Make sure that "index.php" is FIRST in the above line.

Next, if you want to run cgi-bin locally and you have your cgi-bin in your /var/www directory change the following to reflect that:

<IfModule mod_alias.c>
ScriptAlias /cgi-bin/ /var/www/cgi-bin/ <<<<<<<<<<<<<<<<<<<<<<<<<<<

#
# "/usr/lib/cgi-bin" could be changed to whatever your ScriptAliased
# CGI directory exists, if you have that configured.
#
<Directory /var/www/cgi-bin/> <<<<<<<<<<<<<<<<<<<<<<<<<
AllowOverride None
Options ExecCGI -MultiViews +SymLinksIfOwnerMatch
Order allow,deny
Allow from all
</Directory>
</IfModule>

I think the default local for cgi-bin is : var/lib/cgi-bin or something like that.

Next goto the following section:

# And for PHP 4.x, use:
#
#AddType application/x-httpd-php .php <<<<<<<<<<<<<<<<<<<uncomment,del #
#AddType application/x-httpd-php-source .phps <<<<<<<<<<<<uncomment,del #

Check that there are no other Aliases active (eg for images), if so it is better to comment them by setting a # at the beginnig of the corresponding lines.


That's all I ever do to change my config file. Click the SAVE button.

*********************

Next, you need to change php.ini to alloy running the mysql add-on. Alt-Tab to your terminal, start another session and type the following:

sudo gedit /etc/php4/apache/php.ini

ctrl+F to find : mysql.so it will be in the Dynamic Extensions area. Looks like this:
; Example lines:

;extension=mysql.so
;extension=gd.so
;extension=udb.so

remove the semi-colon for mysql.so. Scripts like SugarCRM need to run the GD Graphics library that's why we installed the module originally and you can uncomment it now in your php.ini file. Save the file, close it.

*******************************

Alt-Tab back to Webmin. You may now Start Apache. Click on the Servers icon in Webmin, click on MySQL. You should be greeted with a uname/passwd login screen. Your password that you chose earlier is already in the field as stars. You may click login. Now you may Start MySQL.

****************

You are finished. You may close everything out, run the STOP comand for Webmin and unpack the mambo installer to your /var/www folder, and set all files to 777 for the beginning, then point your browser to [http://localhost](http://localhost) and the mambo installer pops up.


This HOWTO is from the Warty section, a bit modified for hoary for the original howto by machiner see [here](http://www.ubuntuforums.org/showthread.php?t=17876)

---

### Post by themoddingden on 2005-06-15
Hi;
I'm sorry but I moved to siteman.
I'm useing it cause my skill with databases is nil heck and nix too is not all that great .

It's easy the basic mambo setup but it's getting mysql setup etc 

I'm sorry I've not been around here to check i'm doing other items that needed to be done.

---

### Post by andlinux21 on 2005-06-17
I dont have my own server running yet but I do have a site with Mambo working and I also ran Mambo when i had my SuSE 9.1 box if you need some help let me know I don't know a lot but I got it working.

---

