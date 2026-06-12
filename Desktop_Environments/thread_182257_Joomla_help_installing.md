---
title: "Joomla help installing"
date: 2006-05-25
forum: Desktop Environments
---

### Post by Simian on 2006-05-25
I have been trying for two days now to install Joomla.
I am trying to install through a browser. I enter the details on step 1, hostname, msql username, password etc, then I click next and it goes to a blank page and that's it.

I have a feeling that the problem is with MySQL. at the opening check list it says that there is no MySQL support. Somebody Freenode #joomla someone said that PHP isn't handling MySQL but they didn't elaberate.

I have installed MySQL5, PHP5.

I have tried googleing for my answer but the problem is that I'm not quite sure what questions I should be asking?

---

### Post by Ptero-4 on 2006-05-25
You should ask about how to make PHP take the HTML queries and make them into MySQL queries that get feed to the SQL DB, and then transform the responses from the SQL DB back into HTML and inject them into the PHP webpage.

---

### Post by Simian on 2006-05-26
Thanks for your reply Ptero-4. It is starting to look like I have bitten off more than I can chew.

I've found [Joomla! Install For Beginners]("http://www.joomlaya.com/content/view/130/83/")

I will see if I can learn something from there. But if anyone knows any better tutorials I would love to hear about them

---

### Post by dom on 2006-07-20
I just installed Joomla on Xubuntu DD (6.06 LTS).

These are the modules I installed with Synaptic :
[LIST=1]
[*]apache2
[*]php5
[*]mysql-server
[*]php5-mysql
[*]libapache2-mod-auth-mysql
[/LIST]

Then I set up mysql :

```
mysqladmin -u root password *<new-password-here>*
```

```
mysql -u root -p
```
*<enter the new root password you just set>*

```

create database joomladb;
GRANT SELECT, INSERT, UPDATE, DELETE, CREATE, DROP, INDEX, ALTER, CREATE TEMPORARY TABLES, LOCK TABLES ON joomladb.* to 'mrjoomla'@'localhost' identified by '*<mrjoomlas password>*';
flush privileges;
quit

```

Then I went and downloaded Joomla_1.0.10-Stable-Full_Package.tar.bz2 and unzipped to **/var/www/joomla**.

I chmod'd everything in /var/www/joomla and the folder itself to be writable by others :
```

chown -R www-data:www-data  /var/www/joomla

```

Then I went to [http://localhost/joomla](http://localhost/joomla) in my browser. 

The installation page came up and everything was ok in the list except for mysql access. I looked around and found [http://www.ubuntuforums.org/showthread.php?t=197660]("http://www.ubuntuforums.org/showthread.php?t=197660") so after a read of that I done :

```

sudo dpkg-reconfigure php5-mysql
sudo /etc/init.d/apache2 restart

```

Then I clicked the recheck button on the first installation page and all was green.

In the mysql settings I entered 'localhost' for the server name, 'mrjoomla' for the user, the the password i set for mrjoomla earlier, then 'joomladb' for the database. 

On my initial tries I hadn't installed the package "[*]libapache2-mod-auth-mysql" and could not get past this step.

It worked and I finished off with the next page. After doing :
```

sudo rm -rf /var/www/joomla/installation

```
I hit the show site icon at the top right and it all seems to hvae worked swimingly.

Now to figure out how to use the thing :)

Best of luck !

---

### Post by az on 2006-07-20
[https://help.ubuntu.com/community/Joomla](https://help.ubuntu.com/community/Joomla)

---

### Post by KingBahamut on 2006-07-20
[http://doc.gwos.org/index.php/ServerGuide#Joomla](http://doc.gwos.org/index.php/ServerGuide#Joomla)

---

### Post by az on 2006-07-20
That's twice that someone reccommends 

GRANT ALL PRIVILEGES ON Joomla.*
TO nobody@localhost IDENTIFIED BY 'password';

Maybe you don't want to grant *all* proviledges...

---

### Post by KingBahamut on 2006-07-20
Ill have a writer correct, Capn.

---

### Post by dom on 2006-07-21
> **azz said:**
> That's twice that someone reccommends 

GRANT ALL PRIVILEGES ON Joomla.*
TO nobody@localhost IDENTIFIED BY 'password';

Maybe you don't want to grant *all* proviledges...

That's true azz, I was just being lazy after spending the evening just wanting to see it work, I'd go back and fix the permissions as per [https://help.ubuntu.com/community/Joomla](https://help.ubuntu.com/community/Joomla) now that I know what they should be :)

Also, the file permissions mentioned there are better than in my e.g. above.

Also, I don't think the module phpmyadmin as mentioned in my e.g. is required.

---

### Post by Mr K on 2007-11-16
The only thing that I'm sorry for is that i still can't manage to load joomla... i tested my apache2 server with a small php script and it works well.. but when i try to load joomla it wants me to download it instead! Do you have any idea about this mess i'm in?

---

### Post by Mr K on 2007-11-16
Ok i figured it out smashing my head in to the dark! :)

---

### Post by Kundalinux on 2007-11-23
I hope someone makes a deb or something. No?

---

### Post by konradk on 2007-12-22
Hmm, I just followed the instructions laid out here: [http://www.howtoforge.com/ubuntu_lamp_for_newbies](http://www.howtoforge.com/ubuntu_lamp_for_newbies)
That installed LAMP (Apache, mySQL and PHP) and as for Joomla they have a very good installation manual 
available in .pdf , did everything it said and got it all working fairly quickly.
 I found the manual in the Docs section of the Downloads page.

Hope that sheds some light, good luck.

---

