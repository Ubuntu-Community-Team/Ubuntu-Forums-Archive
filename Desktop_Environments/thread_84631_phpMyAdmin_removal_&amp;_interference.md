---
title: "phpMyAdmin removal &amp; interference"
date: 2005-10-31
forum: Desktop Environments
---

### Post by blubery on 2005-10-31
Ever since I installed phpMyAdmin everything went down hill...hmm. I never could get it to work properly anyhow, so I used the Synaptic Package Manager and chose to remove and it gives me an error basically saying no you cant uninstall this. My latest error I received is from when I tried to uninstall mysql (via Synaptic) and during removal  this popped up in the "Changes applied" dialog box:

E: phpmyadmin: subprocess pre-removal script returned error exit status 127

I was not even trying to uninstall phpMyAdmin, just mysql. I dunno if it has anything to do with this whole phpMyAdmin thing but I can no longer use juK, it crashes constantly, I have tried removing reinstalling etc, different crash info I get each time from it. So I guess my questions are:

1.) how to completely uninstall phpMyAdmin?
2.) (less important secondary question) what to do about juK or can you suggest a similar mp3 player?

I have searched these forums and read on almost similar problems and searched linux google but to no aveil I am writing here, thanks for your time & help.

---

### Post by HermanAB on 2005-10-31
Hi there,

The way I resolve issues like this, is to go to the project home page on Sourceforge, download the source and compile and install it from scratch:
[http://sourceforge.net/projects/phpmyadmin/](http://sourceforge.net/projects/phpmyadmin/)

See this:
[http://www.aerospacesoftware.com/compile-howto.html](http://www.aerospacesoftware.com/compile-howto.html)

Cheers,

Herman
[http://www.aerospacesoftware.com](http://www.aerospacesoftware.com)

---

### Post by wrtrdood on 2005-11-01
Hmmm... not quite sure why installing phpmyadmin would cause problems.  To make it work you have to create a link to the install directory (/usr/share/phpmyadmin) in the /var/www directory (or wherever you keep your webserver).  Don't forget to change the owner of the phpmyadmin directory to the webserver user (www-data in my case).  There's some other setup to do (config.inc.php) but that should get you started.  Removing it should be just as simple as:

  sudo apt-get remove phpmyadmin

Now, removing mysql is another issue.  Here's what my system tells me will happen (-s means simulate)

apt-get -s remove mysql*

which then says it will do this:

The following packages will be REMOVED:
  libdbd-mysql-perl libmysqlclient10 libmysqlclient12 libpam-mysql
  mysql-client mysql-common mysql-server php4-mysql phpmyadmin

0 upgraded, 0 newly installed, 9 to remove and 0 not upgraded.

Notice what's at the end of that list ;)  Taking out MySQL will pull most dependencies to keep things clean.  However, you should be able to remove phpMyAdmin by itself with no trouble.  Try using apt-get at the command line.  It should give you a bit more information as to what's wrong.  Synaptic (and Adept) are great tools but they tend to insulate the user a bit much for my taste when I run into issues.  Chances are what you should to do get things stabilized is to run: sudo apt-get -f install
This should help some (no, there's no package -- this is to fix broken things which is probably the message you'll get running apt-get at the command line.)

Good luck.

---

### Post by blubery on 2005-11-02
Well, when I use apt-get on the command line I get the same error, this: 
---------------------------------------------
blubery@ubuntu:~$ sudo apt-get remove phpmyadmin
Password:
Reading package lists... Done
Building dependency tree... Done
The following packages will be REMOVED:
  phpmyadmin
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B of archives.
After unpacking 11.1MB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 116757 files and directories currently installed.)
Removing phpmyadmin ...
/var/lib/dpkg/info/phpmyadmin.prerm: line 12: db_get: command not found
dpkg: error processing phpmyadmin (--remove):
 subprocess pre-removal script returned error exit status 127
Errors were encountered while processing:
 phpmyadmin
E: Sub-process /usr/bin/dpkg returned an error code (1)
--------------------------------------------

But when I run a -s I get some different information, like this:
--------------------------------------------
blubery@ubuntu:~$ sudo apt-get -s remove phpMyAdmin
Reading package lists... Done
Building dependency tree... Done
The following packages will be REMOVED:
  phpmyadmin
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Remv phpmyadmin [4:2.6.4-pl1-1ubuntu1.1]
--------------------------------------------

When i give this command I get:
--------------------------------------------
blubery@ubuntu:~$ sudo apt-get -f install phpMyAdmin
Reading package lists... Done
Building dependency tree... Done
phpmyadmin is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
--------------------------------------------------
great information from both of you, I've learned somethings from all that, thanks! I still can't get rid of the thing though :???: ...any other ideas? 
thanks

---

