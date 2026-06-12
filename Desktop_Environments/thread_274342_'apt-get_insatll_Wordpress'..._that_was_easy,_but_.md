---
title: "'apt-get insatll Wordpress'... that was easy, but what now??"
date: 2006-10-09
forum: Desktop Environments
---

### Post by kpm on 2006-10-09
Hi,

I installed the Dapper LAMP server.  I then used apt to install Wordpress.  I have installed Wordpress on Widows many times, but this is a first on Lunux. So I began the search for config files... Off to /etc/wordpress, where I found the wp-config file, but it told me NOT to touch it and to go to the readme.html, which I saw to be located at '/usr/share/wordpress/readme.html'.  So I open that file up using 'less readme.html' and think to myself I should really be looking at this file via a webbrowser (I am ssh'd into the bare bones old server from a laptop).  But now I am stuck... I don't know what url to use to get to that readme file... I know my web server root is /var/www/ and that if I enter the url [http://192.168.1.200/index.html](http://192.168.1.200/index.html) I can see the server up and running, can access phpmyadmin to get at MySQL, etc... but with the default install of Wordpress using apt, I am left a bit confused... I know I can copy the readme.html to the root of www, but, thought, that since Wordpress placed it /usr/share/wordpress/ that I should figure out what I have to do to Apache to get it to look there for it... Having come from Windows, I am used to having all the web pages dumped in a subdirectory of the Apache2 folder... Can anyone clue me in here on this??

---

### Post by s_p_a_r_k_y on 2006-10-09
do you have root on this box? or ability to edit the apache config files? You will want to add an alias of 
/wordpress to /usr/share/wordpress/ (or wherever the php files are)

Something similar to this should work
```
Alias /wordpress/ "/usr/share/wordpress/"
```

Then restart apache and you should be able to go to your IP/Domain plus /wordpress/

If not then have a looksie at the log file, /var/log/apache2/error_log

you may need to setup the directory in apache such as the following example I copied
```

<Directory "/usr/share/apache2/icons">
    Options Indexes MultiViews
    AllowOverride None
    Order allow,deny
    Allow from all
</Directory>

```
replaceing of course the directory in mine with yours. Enjoy setting up on your "lunux" box :)...its linux for the future

---

### Post by az on 2006-10-09
See here:
[https://help.ubuntu.com/community/WordPress](https://help.ubuntu.com/community/WordPress)

---

### Post by kpm on 2006-10-09
thanks!

just what I needed.

---

