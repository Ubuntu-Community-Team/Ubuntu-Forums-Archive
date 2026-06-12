---
title: "Installing Apache in Ubuntu"
date: 2006-05-04
forum: Desktop Environments
---

### Post by vanderbolt on 2006-05-04
Hi,
Havng troubles installing Apache Web Server in Ubuntu.

I have located the package using the Synaptic Package Manager... but it does not seem to install...

It is not located in my Applications list at all, yet under the Synaptic Package Manager it says that it is installed

Any Help??

Thanks

Derek

---

### Post by cgjones on 2006-05-04
Well, I'm not quite sure where to begin. Apache is what they call a daemon, a program that runs in the background doing it's thing. There isn't going to be an entry in the Applications menu for it. Most of the configuration for Apache is done using text files, although I believe that there might be some graphical tools for configuring it. I would start by doing some reading at the following link.

[http://httpd.apache.org/](http://httpd.apache.org/)

---

### Post by matthewstory on 2006-05-04
To see if apache is running open a terminal window:

applications > accessories > terminal

and type in the following command:

ps aux | grep apache

if apache is running that should return about 6 or 7 process lines, if its not, it won't return anything.  You can also figure it out by opening firefox and browsing to the IP of the machine apache is installed on, you should see an apache welcome page.  Then see the link the guy before me posted because you're gonna need to learn alot to get past this point with apache.

---

### Post by matthewstory on 2006-05-04
I'll try to give you enough info to do basic stuff with apache.  Apache really can only be handled from the command line, so open a terminal window (see previous post) apache starts when your machine starts and stops when your machine stops, but if you want to restart it or stop it you can do so with these commands. 

If you're running apache 1.3.x (i think this is default in the repository):

to start the server:
/etc/init.d/apache start

to stop the server:
/etc/init.d/apache stop

to restart the server:
/etc/init.d/apache restart

If you're running apache 2.x.x (probably not this):

to start the server:
/etc/init.d/apache2 start

to stop the server:
/etc/init.d/apache2 stop

to restart the server:
/etc/init.d/apache2 restart

The main configuration file for apache 1.3 is found in the file /etc/apache/httpd.conf, don't edit this untill you read how to edit it from the earlier link.  The main configuration for apache2 is found in the file /etc/apache2/apache2.conf, again don't edit this unless you know what you're doing.  To just host websites on your local network, you can put the files into apache's document root, which is located in the folder /var/www.  So lets say you wrote something in html called index.html, to have apache serve this file put it in the /var/www folder:

cd <path to index.html>
cp index.html /var/www

Then to view this go open a browser like firefox and type in the ip address of your server followed by /index.html.  So lets say your ip is 192.168.1.68, you'd type in 192.168.1.68/index.html.  That'll get you up and running.

---

### Post by vanderbolt on 2006-05-04
Thanks for the Advice... 
I have had Apache running in Windows XP but i am switching over to Ubuntu


Thanks Again

---

