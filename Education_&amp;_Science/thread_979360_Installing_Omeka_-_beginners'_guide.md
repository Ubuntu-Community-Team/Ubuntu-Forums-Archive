---
title: "Installing Omeka - beginners' guide"
date: 2008-11-11
forum: Education &amp; Science
---

### Post by sirtah on 2008-11-11
How to install Omeka on Ubuntu (8.10) - 

I've used Ubuntu and the forum for over a year and a half now and I've never posted a how to, mostly because I've never done anything new before. I recently installed [Omeka]("http://omeka.org/") at home and I couldn't find a guide, so I thought I'd share (because I've been extremely thankful for all the guides I've used). This my first guide so it might not be perfect. Check the Omeka documentation and post your comments as needed. I may not be able to help, but in my experience, there is always another friendly Ubuntu user who can. 

I'm not a programmer and I know virtually nothing about server security. This guide is for installing Omeka on your own computer for testing and development. I also assume you're as stupid as me. 

Please read the entire guide before beginning (I've learned that one the hard way)

Step 1 &#8211; Select LAMP server for installation 
	
	-Open your Synaptic Package Manager 
	-Under Edit, select &#8220;Mark Packages by Task&#8221; 
	-Check LAMP Server 

Step 2 &#8211; Select phpmyadmin for installation 
	
	-With the Synaptic Package Manager open search &#8220;phpmyadmin&#8221; 
	-Mark phpmyadmin for installation 

Step 3 &#8211; Select ImageMagick for installation 
	
	-With the Synaptic Package Manager open search &#8220;imagemagick&#8221;
	-Mark imagemagick for installation 

Step 4 &#8211; Install Packages 
	
	-click Apply in the Synaptic Package Manager and install 
	-You'll have to set a root password for you mysql database
	-Select Apache2 for the type of server to configure phpmyadmin to.

Step 5 &#8211; Create mysql database for Omeka 

	-Open Firefox (or your preferred open source web browser :) 
	-Type in localhost/phpmyadmin as the url
	-Insert root as your username and type in your password 
	-Click on Privileges (roughly the 7th link under Create a  
         new database
	-On the next screen click Add a new User 
	-Type in a username, select localhost as the host, select a 
         password and retype it. 
	-On the same screen under Database for user select Create a 
         database with same name and grant all privileges 
	-hit Go and check for the new database

Step 6 &#8211; Enable mod_rewrite in Apache2 (the hardest part)
	
	-Open the terminal, and login as root (sudo -i and then enter 
         your root password)
	-Enter the command: a2enmode rewrite
	-Next command  nautilus
	-This will open up the Nautilus &#8211; which is probably easier than 
         the command line for rookies like myself. 
        -Navigate to the filesystem, then etc, then apache2-/etc/apache2/
	-Open the apache2.conf file (you really should back it up first)
	-At the bottom of the file copy in 
		
		# Enable mod_rewrite 
		<IfModule mod_rewrite.c>
			RewriteEngine On
		</IfModule>

	-Save the file and close it.  
	-Next go to sites-enabled 
	-open 000-default (again backup to be safe) and under 
          <Directory /var/www/>

		change 
			AllowOverride none	
		to
			AllowOverride All

	-Save the file and close it. 
	-Leave Nautilus open.	 

Step 7 &#8211; Download Omeka to your Desktop 

Step 8 &#8211; Extract Omeka to your Desktop 

Step 9 &#8211; Navigate back to your file system, then to var, then www
         /var/www/ 

Step 10 &#8211; Drag and drop the extracted Omeka folder into the www folder 
	  (I also recommend renaming it to something simple like Omeka)

Step 11 &#8211; Right click on the Omeka folder and select Properties. 

Step 12 &#8211; Go to the Permission tab and under Others change Folder access 
          to Create and delete files

Step 13 &#8211; Configure db.ini

		-Open the Omeka folder and select the db.ini folder 
		-Replace all the XXXX with the proper information 
			host = &#8220;localhost&#8221;
			username = &#8220;whatever user you created in step 5&#8221;
			password = &#8220;whatever the password you gave the 
                                    user in step 5&#8221;
			name = &#8220;whatever username you created in step 5&#8221;

Step 14 &#8211; Close the db.ini, close Nautilus, and switch make to the terminal to 
          restart Apache.
         -Enter the command /etc/init.d/apache2 restart

Step 15 &#8211; Switch to your browser and enter as the url  
            localhost/whatever you named the omeka folder/ 

Step 16 &#8211; Start playing with Omeka.

Hope this helps someone and let me know if I missed anything along the way.

---

### Post by 8bitzombie on 2009-01-05
Thank you very much for the guide. I tried setting up omeka on ubuntu 8.04 but had some problems. The first hitch i came to was the "a2enmode rewrite" which i cannot use, so I used "a2enmod rewrite" after googling around. I try to restart apache 2 but i only get "Could not reliably determine the server's fully qualified domain name, using 127.0.0.1 for servername." Is this the problem? I followed the rest of the guide to a T with minimal changes because of files being located in slightly different places, but then when I insert locahost/omeka into firefox I recieve the message "Access denied for user '   '@'localhost' (using password:YES)" Any help would be greatly appreciated, and I can supply more information if necessary. Thank you in advance

---

### Post by sirtah on 2009-01-05
8bitzombie, 

I'm not an expert but I'll try to help the best I can. Just to make sure we are coving the simple things first, is apache working? What happens when you go to [http://localhost/](http://localhost/) in firefox? Also you might want to check out this thread 
[http://ubuntuforums.org/archive/index.php/t-424573.html](http://ubuntuforums.org/archive/index.php/t-424573.html)
about the "Could not reliably determine the server's fully qualified domain name.." problem. It looks like you can just ignore it but there is a solution posted in the thread. 

I'm not sure about the a2enmode rewrite discrepency, that might be a typo. I'll check later tonight when I get the chance. 

You might want to check that you're omeka config file matches the information you need to access the database. The ''@localhost is curious and makes me think that there might be a problem with the database username and the omeka config file. 

Hope this helps

---

### Post by 8bitzombie on 2009-01-05
Yeah, very helpful! /localhost gives me "It works' (yay) but I realized something happened when I created my user and database so  iwent back in and deleted them, recreated them, and now it works!! Thanks so much for this guide its been a lifesaver!!

---

### Post by sirtah on 2009-01-05
No problem glad to help.

---

### Post by ulisseslima on 2010-04-11
Hello, very new linux user here. I hope someone can still help. I followed the above, and apache seems tp be working ok, but when I try to navigate to [http://localhost/omeka/](http://localhost/omeka/) in firefox, I get a 404 error:

The requested URL /omeka/ was not found on this server.
  Apache/2.2.11 (Ubuntu) PHP/5.2.6-3ubuntu4.5 with Suhosin-Patch Server at localhost Port 80

any idea what I did wrong?:confused:

---

### Post by sirtah on 2010-04-12
Hello, 

I'm not sure if I'll be able to solve this but let's start with some mistakes that I often make. What are the file permissions for /omeka/? Also what is the structure of your www folder?

---

