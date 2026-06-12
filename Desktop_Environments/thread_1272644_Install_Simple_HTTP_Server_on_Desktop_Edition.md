---
title: "Install Simple HTTP Server on Desktop Edition"
date: 2009-09-22
forum: Desktop Environments
---

### Post by johnnywins on 2009-09-22
Hello everyone

I am new to Linux and this is my first post.  I am enjoying this so far.  Now I want to set up a simple web server so that I can allow friends and family to access my files.  I installed Ubbuntu Desktop edition, not Server edition.  How can I get this going?  I have found a bunch of links that show how to install Apache and all that on Ubuntu Server Edition, but is it different for Desktop Edition?  I have the newest 9.04.  This is what I have done so far:

*sudo apt-get install apache2*

Then I edited the default file in /etc/apache2/sites-available like so:
ServerAdmin <email>
        ServerName <site address>
        DocumentRoot <home folder>

Sadly enough, this is as far as I got because the documentation was confusing me a bit.

This is the link I was using: [https://help.ubuntu.com/6.06/ubuntu/serverguide/C/httpd.html](https://help.ubuntu.com/6.06/ubuntu/serverguide/C/httpd.html)

Is there a better link out there for someone who is a bit of a newb?

Do you guys understand what I am trying to do?  I just want to be able to send a friend a link, and have it take them to a specific folder on my computer so that I can share files with that folder.  I'd like them to have their own usernames too.  I already have a site name registered with DynDns.com and my router has the fucntionality for dynamic IP.

Sorry if I posted this in the wrong section.  Forums can be overwhelming sometimes with all the different sections.

Also, another question.  When using the Terminal, is there a way to enable ctrl-c and ctrl-v?  Instead of having to always right click?

Thanks for any help you can provide!

John

---

### Post by saj0577 on 2009-09-22
> Also, another question. When using the Terminal, is there a way to enable ctrl-c and ctrl-v? Instead of having to always right click?

Use Ctrl+shift-C and ctrl+Shift-v  and it should work find with gnome-terminal :)

Do you just want it to run html websites and that is it yes? Or would you also like it to run php,perl,python scipts etc aswell?

Let me know and I will adapt the more recent guide to be totally relevant for you.

[https://help.ubuntu.com/9.04/serverguide/C/httpd.html](https://help.ubuntu.com/9.04/serverguide/C/httpd.html)


For a really simple webserver if it is just html websites you want to run. then 
sudo apt-get install apache2
by itself is more then surfice for the installation.


Let me know

Saj

---

### Post by johnnywins on 2009-09-22
> **saj0577 said:**
> Use Ctrl+shift-C and ctrl+Shift-v  and it should work find with gnome-terminal :)

Do you just want it to run html websites and that is it yes? Or would you also like it to run php,perl,python scipts etc aswell?

Let me know and I will adapt the more recent guide to be totally relevant for you.

[https://help.ubuntu.com/9.04/serverguide/C/httpd.html](https://help.ubuntu.com/9.04/serverguide/C/httpd.html)


For a really simple webserver if it is just html websites you want to run. then 
sudo apt-get install apache2
by itself is more then surfice for the installation.


Let me know

Saj

Thanks for the quick response!  Yes just HTML websites. So I have Apache installed.  Now what?  I followed the doc above for the Basic Setting section.  Now I think there is something I have to do with the ports.  Just not sure how.  I know that some ISPs do not allow server to run on port 80 right?  So what do I do?  On my router configuration, which port should I forward?  And how do I tell Apache which port?  Do I modify the "Listen" section in /etc/apache2/ports.conf to <IP>:<PORT>?  Which IP would it be?  My public IP or my local IP within my router?  And again, which port should I use.

---

### Post by saj0577 on 2009-09-22
Well what I would do in your situation is...

Sudo apt-get install apache2

Leave all config files to default for now. 

In your router make it forward all incoming port 80 to your computer (preferably static ip such as 192.168.0.5) 

Then when people access your external ip they will see the webserver.
If port 80 is blocked simply make it forward external port 8080 to port 80 on 192.168.0.5.

Make sense?

I also change where the default www files are stored but will explain more once you reply and understand so far. 

Saj

---

### Post by johnnywins on 2009-09-22
> **johnnywins said:**
> Thanks for the quick response!  Yes just HTML websites. So I have Apache installed.  Now what?  I followed the doc above for the Basic Setting section.  Now I think there is something I have to do with the ports.  Just not sure how.  I know that some ISPs do not allow server to run on port 80 right?  So what do I do?  On my router configuration, which port should I forward?  And how do I tell Apache which port?  Do I modify the "Listen" section in /etc/apache2/ports.conf to <IP>:<PORT>?  Which IP would it be?  My public IP or my local IP within my router?  And again, which port should I use.

OK I am just trying it with port 80 now all i see when i enter the site address is "It works!"

---

### Post by johnnywins on 2009-09-22
> **saj0577 said:**
> Well what I would do in your situation is...

Sudo apt-get install apache2

Leave all config files to default for now. 

In your router make it forward all incoming port 80 to your computer (preferably static ip such as 192.168.0.5) 

Then when people access your external ip they will see the webserver.
If port 80 is blocked simply make it forward external port 8080 to port 80 on 192.168.0.5.

Make sense?

I also change where the default www files are stored but will explain more once you reply and understand so far. 

Saj


OK so I uninstalled Apache and re-installed so that the config files would go back to default.  Now when I access my IP address, it shows "It works!"  So now what?

---

### Post by saj0577 on 2009-09-22
Right.


We need to check if it works from external so if you give me your ip from whatismyip.org I will see if you got router set up right.

If not if you tell me which make of router is I will be able to give more specific information on the router setup.

In your home folder create a folder called public_html  and then change the document root in the apache2 config file to 
/home/johnny/public_html
(for example)

this will allow you to add and edit files without any permissions problems. and means if you ever backup your home folder you dont forget to back up your www files (like I always use to)

Understood?

Hope it helps
Saj


After changing the apache2 congfig file run
sudo /etc/init.d/apache2 restart
to ensure it uses your new config file.

---

### Post by gordintoronto on 2009-09-22
> **johnnywins said:**
> OK so I uninstalled Apache and re-installed so that the config files would go back to default.  Now when I access my IP address, it shows "It works!"  So now what?

Put your html files into /var/www

---

### Post by johnnywins on 2009-09-22
> **saj0577 said:**
> Right.


We need to check if it works from external so if you give me your ip from whatismyip.org I will see if you got router set up right.

If not if you tell me which make of router is I will be able to give more specific information on the router setup.

In your home folder create a folder called public_html  and then change the document root in the apache2 config file to 
/home/johnny/public_html
(for example)

this will allow you to add and edit files without any permissions problems. and means if you ever backup your home folder you dont forget to back up your www files (like I always use to)

Understood?

Hope it helps
Saj


After changing the apache2 congfig file run
sudo /etc/init.d/apache2 restart
to ensure it uses your new config file.

OK - You said change the DocumentRoot in the Apache2 config file.  Did you mean this file? /etc/apache2/sites-available/default?

johnnywins.dyndns.biz should take you to my IP address.. Can you test with that?

---

### Post by saj0577 on 2009-09-22
Yeah that works. good job :).

And yeah I think its that file cant check as not currently got a webserver on this computer but sounds right to me.


Saj

---

### Post by johnnywins on 2009-09-22
> **saj0577 said:**
> Yeah that works. good job :).

And yeah I think its that file cant check as not currently got a webserver on this computer but sounds right to me.


Saj

OK cool. But what did you see when you went to johnnywins.dyndns.biz?  I see the following:

**Forbidden**

 You don't have permission to access / on this server.

---

### Post by saj0577 on 2009-09-22
Yeah thats because now you have the www folder in your home folder yeah?(dont worry wont stay like this)

Saj

---

### Post by johnnywins on 2009-09-22
> **saj0577 said:**
> Yeah thats because now you have the www folder in your home folder yeah?(dont worry wont stay like this)

Saj

yea, i basically added it just like you said, /home/john/public_html

so what now?

also, is this normal?
sudo /etc/init.d/apache2 restart
 * Restarting web server apache2         
 apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
 ... waiting apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName

---

### Post by saj0577 on 2009-09-22
Yeah that error is to do with the hosts file I believe.

In terminal run
sudo chmod +r /home/john/public_html

this will give everyone read rights to the files in public_html


Saj

---

### Post by johnnywins on 2009-09-22
> **saj0577 said:**
> Yeah that error is to do with the hosts file I believe.

In terminal run
sudo chmod +r /home/john/public_html

this will give everyone read rights to the files in public_html


Saj

OK, ran that.  Still seeing the same error

---

### Post by saj0577 on 2009-09-22
Going to install apache2 now give me 2minutes.

Saj

---

### Post by johnnywins on 2009-09-22
> **saj0577 said:**
> Going to install apache2 now give me 2minutes.

Saj

OK- thanks.  Maybe this is it.. in the default file there is this section below.  Maybe I need to change the directory:

<Directory /var/www/>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride None
                Order allow,deny
                allow from all
        </Directory>

---

### Post by saj0577 on 2009-09-22
Fixed it just gonig to right it up now. :)

Saj

---

### Post by saj0577 on 2009-09-22
Right Its not working fully so for now.
sudo mv /home/john/public_html/ /var/www/


Then change the config file to say /var/www/public_html/  for the document root.

This will allow you to create files in /var/www/public_html which appear over the internet, (where as in the www you dont have permissions to create files). 

We could change the www to be owned by you but we will leave it belonging to root. As when I fix the problem your web directory will be in your home folder which is better.

Sorry for an inconvenience I will have a play around if I don't fire up my other machine.

Saj

---

### Post by johnnywins on 2009-09-22
> **saj0577 said:**
> Right Its not working fully so for now.
sudo mv /home/john/public_html/ /var/www/


Then change the config file to say /var/www/public_html/  for the document root.

This will allow you to create files in /var/www/public_html which appear over the internet, (where as in the www you dont have permissions to create files). 

We could change the www to be owned by you but we will leave it belonging to root. As when I fix the problem your web directory will be in your home folder which is better.

Sorry for an inconvenience I will have a play around if I don't fire up my other machine.

Saj

Hey Saj, ya know what, I hardly ever backup my stuff anyway, don't worry about it, I'll just use the www folder :).

Now that I have this setup, I have some more questions...

How can I enhance this whole thing?  You mentioned a couple things at the start of this thread, like PHP etc.  I am not familiar with what all that stuff does and how it works...

One thing I'd like to get setup for sure is to have separate usernames for people who access my site.

---

### Post by johnnywins on 2009-09-22
> **johnnywins said:**
> Hey Saj, ya know what, I hardly ever backup my stuff anyway, don't worry about it, I'll just use the www folder :).

Now that I have this setup, I have some more questions...

How can I enhance this whole thing?  You mentioned a couple things at the start of this thread, like PHP etc.  I am not familiar with what all that stuff does and how it works...

One thing I'd like to get setup for sure is to have separate usernames for people who access my site.
  I also want to figure out how to default johnnywins.dyndns.biz to my index.html file that i just created in /var/www/public_html

That way its like my own website, is that possible?  I added the index.html part in the DocumentRoot field but now when i try to access the site its saying 
**Not Found**

 The requested URL / was not found on this serv

---

### Post by johnnywins on 2009-09-22
> **johnnywins said:**
> I also want to figure out how to default johnnywins.dyndns.biz to my index.html file that i just created in /var/www/public_html

That way its like my own website, is that possible?  I added the index.html part in the DocumentRoot field but now when i try to access the site its saying 
**Not Found**

 The requested URL / was not found on this serv

OK.... i feel stupid, i did not have to at "/index.html" to the DocuemntRoot.  I just took it off and left it /var/www/public_html   and when i went to johnnywins.dyndns.biz it autoatically took me to index.html.  Sweet! This is perfect

---

