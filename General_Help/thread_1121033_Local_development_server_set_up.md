---
title: "Local development server set up"
date: 2009-04-09
forum: General Help
---

### Post by Johnr123 on 2009-04-09
Hi there,

I am new to Ubuntu 8.10. I previously ran windows XP. 

I have some web sites that I test and develop using a server on my local system. Previously while on XP, I used a Wamp server. Now that I have switched (and glad I did) to Ubuntu 8.10, I am having trouble figuring out how to duplicate the convienience of that Wamp server that I ran on XP. 

I thought tht it would be even easier to do this on Linux, but all my Google searches so far have lead me to setting up the "Server Edition" of Ubuntu, but that is not my goal. I want to set up a local development server within my "Desktop Edition" of Ubuntu. No matter how I word the search though, the end result points me to setting up the server edition. 

I am fairly certain that Apachi, PhP, and MySql are set up on mu Ubuntu desktop edition. I have even set the root password for MySQL, but I have no idea how to proceed to configure it all to recognize my 'local.[site name]' local version of my web site. 

Can anyone point me in the right direction via a good link that addresses this type of setup? I would really appreciate it. My former Wamp server on Windows was great. It allowed me to test site deveopment without being live, plus I could easily switch between different versions of PhP, Apache, and MySQL on the fly to test compatibilities. Surely this is even easier, or at least as easy, on Ubuntu.

Thanks for any help :-)

John

---

### Post by rage9 on 2009-04-09
Well the desktop and server versions are basically the same thing, and can be set up the same way.

Follow section: [17 Apache/PHP5/Ruby/Python ]("http://www.howtoforge.com/perfect-server-ubuntu-8.10-p6")

Then Section: [14 MySQL]("http://www.howtoforge.com/perfect-server-ubuntu-8.10-p4")

Finally install phpMyAdmin to make using MySQL easier:
>     apt-get -y install phpmyadmin

It might ask you what server to configure for, obviously choose apache2.

Now it wont work right out the box, we need to add a line to our Apache configuration:

    nano /etc/apache2/apache2.conf

Go to the end of the file and add this line:

    Include /etc/phpmyadmin/apache.conf

Ctrl + O, then Enter to save.  Ctrl + X to exit.  Now restart Apache:

    /etc/init.d/apache2 restart

That'll give you a good LAMP (Linux Apache MySQL PHP) setup.

---

### Post by Johnr123 on 2009-04-09
Thanks Rage9,

I really appreciate your information. I'll work through the steps you pointed to right away.

Cheers,
John

---

### Post by SoCalChris on 2009-04-09
You can also easily set up a fully configured and working LAMP server by running

```
sudo tasksel
```

and choosing the LAMP Server option.

---

### Post by Johnr123 on 2009-04-09
I ran the 'sudo tasksel' code yesterday and it would appear that I have a Lamp server installed since when I run  the code again now, the Lamp server option is already selected with an asterisk. Assuming that I have the Lamp server installed, how do I access it to configure it to serve up my local site (local version of live site)? I simnply want to be able to see my local version on my computer. I don't want to run a server for the live version.

I think I am in over my head to follow the other instructions referenced in the first response to my querie. I am not finding editing lines in the terminal that easy. I am too liable to make an error there. 

Thanks

---

### Post by SoCalChris on 2009-04-09
Your default www root should be in /var/www/. Any Apache configuration beyond that, I won't be of much help :)

---

### Post by Johnr123 on 2009-04-09
Thanks, I'll try and work that out. Appreciated :-)

John

---

### Post by cariboo on 2009-04-09
If LAMP is installed and configured correctly, just open Firefox and type:

```
http://localhost
```

it should display a page saying **It Works!**.

Jim

---

### Post by Johnr123 on 2009-04-09
Yes, it does that. Now I have to figure out how to point the server to my web site files. I can't copy them to the var/www folder as access is denied and I think it's best to point the server to files in my "Home" folder anyway, since it won't get written over on a Ubuntu upgrade. I also have to find out how to open the PhPMyAdmin interface to import my database and set stuff up.

---

### Post by Johnr123 on 2009-04-09
Okay, now I have found out how to open phpMyAdmin. I had to share the phpMyAdmin files into the var/www folder. Now I can log into phpMyAdmin.. 

It's a start.

---

### Post by mb_webguy on 2009-04-09
The Apache configuration files are a bit different on Linux than on Windows.  The Linux method takes a bit of getting used to, but it makes certain things *much* easier.

As previously mentioned, the default Apache web root is /var/www.  To get easy write access, you could change the permissions on this directory using the chmod (e.g. "sudo chmod +rw /var/www") command, or you could change the group to a group of which your user account is a member with the chown command (e.g. "sudo chown root:*username* /var/www"), or both (e.g. "sudo chmod 775 /var/www; sudo chown root:*username* /var/www").

The main Apache configuration file is "/etc/apache2/httpd.conf", but unlike in Windows, you probably don't need to change it.  Pretty much any module you might want to add can be found in the Ubuntu repositories, and installing one automatically makes the appropriate changes to the Apache configuration file.  To control your website(s), you can edit the files in /etc/apache2/sites-available.  If you don't like having your web files in "/var/www", you can change it easily by editing the "/etc/apache2/sites-enabled/default" file and replacing each instance with "/var/www" with the location you'd rather use.  This is another way to gain easy write access to your web files -- just change the location of the web directory to one in your user's home directory.  You wouldn't want to do this on a production server, it's fine for a development server.

Btw, if the development server is on a network or connected to the Internet and you don't want others to view your webserver files, you might want to use ufw to configure iptables to block port 80.

The PHP configuration file is "/etc/php5/apache2/php.ini", and is essentially the same as on Windows.

As for MySQL, I prefer to use the [official GUI tools]("apt://mysql-admin") to administer the databases instead of phpMyAdmin, but it's just personal preference.  The default database directory is "/var/lib/mysql", but if you want to move it to a different location, you can follow [these directions]("http://ubuntuforums.org/showthread.php?t=897354").

---

### Post by Johnr123 on 2009-04-09
Thanks so much for all this information. It will help greatly. I managed to get into MySQL using the root password and changed the privileges for localhost, then went back into phpMyAdmin using localhost log in and created a new user and a new database using the same names and passwords as I had previously on the local version I ran on windows using Wamp. 

After that, I successfully imported my database. Now I have to ensure that the files are in the proper location and the address on my local site is jiving with everthing. My site is a wordpress site so I will need to edit the database wp-options table to change the URL and HOME sections to reflect an address that will work with the localhost server. 

My former Wamp installation used a vitual host named LOCAL so my local site url was [http://local.sitename](http://local.sitename). Since I haven't created a virtual host this time (I'm using localhost), I think I will need to change those addresses to [http://localhost.sitename](http://localhost.sitename), or do you think I should use a forward slash instead of the dot after localhost? 

My machine is connected to the net. I am behind a router with full secutity eneabled plus I have "Firestarter" firewall enabled on the machine. Would I still require extra security measures?

Anyway, tomorrow I'll figure all this out. Your info will help trmenously. Thank you very much for helping

Cheers :-)

---

### Post by Johnr123 on 2009-04-10
Hi,

I'm hoping you can make sense of what I've done. All was going well. I imported my database into the newly created database of the same name as the former one, but no matter what I tried in altering the database WP-Options table to change the url to localhost and variants of, I could not connect to the local site. I only got as far as the files list in /var/www. When I tried to get past that into the web site files and load the site, it indicated I did not have permission to access the site. 

That lead me to believe that I need to change the ownership and permission of all the folders within and including /"var" (the phpmyadmin and web site folders were previously copied to the www folder within var). I changed ownership and gained permission of all folders and files by using the "sudo chown -R $USER:$USER /folders-and-files" command. That changed the ownership of these from "root" to "my user" account. I then applied that permission to all sub-folders using the permissions dialog box.

That didn't help though; in fact it made things worse as then when trying to access [http://localhost/phpmyadmin](http://localhost/phpmyadmin), I got this error message: 
[INDENT]**"Error**
The configuration file now needs a secret passphrase (blowfish_secret).        "
[/INDENT]I then did the same change of ownership and permission access for the phpmyadmin and mysql folders within the usr/share folder, thinking that the ownership and permissions were not complete and uniform across all the folders involved. 

I still get the same error message though, and cannot get into phpmyadmin, despite all the above. Likely, it is BECAUSE of all the above. I am obviously in over my head. So I am wondering how to reverse things and/or put it right considering the errors I have made.

I sure understand if you don't want to respond. I was trying to be self-sufficient, but ended up needing more help as a result :-)

If anyone can shed some light on where I went wrong and how to correct things. I will appreciate it.

---

