---
title: "Web Server Howto: Is there one?"
date: 2005-08-15
forum: Desktop Environments
---

### Post by YaAqoB on 2005-08-15
Can someone please point me in the right direction for a howto to create and configure a web server using ubuntu. 
Cheers

---

### Post by Sam on 2005-08-15
There is an [Ubuntu Wiki](https://wiki.ubuntu.com/) with a lot of articles ! There is [ApacheMySQLPHP](https://wiki.ubuntu.com/ApacheMySQLPHP) about setting up a web server with PHP and MySQL.

---

### Post by sviestainis on 2005-08-15
```

apt-get install apache2
apt-get install php4
apt-get install mysql-server
apt-get install php4-mysql
apt-get install phpmyadmin 

```

---

### Post by YaAqoB on 2005-08-15
Thank you for your help :)
I'll give it a go. :)

---

### Post by SGC on 2005-08-15
Web server in less than 1 minute!

1- download xampp from: [http://www.apachefriends.org/download.php?xampp-linux-1.4.15.tar.gz](http://www.apachefriends.org/download.php?xampp-linux-1.4.15.tar.gz)
2 - extract the file with: tar xvfz xampp-linux-1.4.15.tar.gz -C /opt
3 - run the server with: /opt/lampp/lampp start

---

### Post by YaAqoB on 2005-08-15
Thats great. Thanks.:)
Will this setup host many domain names?
Hey this is all new to me so I was wondering if anyone can direct me to somewhere where they step by step setup your webserver to recognise domain names and how to make it so that when someone wants to visit any of the domain names I will host , it gets directed to my server?
Thanks again.

---

### Post by Zyrix on 2005-08-17
[QUOTE=YaAqoB]Thats great. Thanks.:)
Will this setup host many domain names?
Hey this is all new to me so I was wondering if anyone can direct me to somewhere where they step by step setup your webserver to recognise domain names and how to make it so that when someone wants to visit any of the domain names I will host , it gets directed to my server?
Thanks again.[/QUOTE]

I'm in the middle of setting something similar up myself. What I did was go to [www.godaddy.com](www.godaddy.com) and set up my domain name. I then enabled forwarding to forward it to my ip address. 

I'm not sure how much you know about this so this is basically every step I did:

Install apache:
```
sudo apt-get install apache2
``` 

Install php:
```
sudo apt-get install php4
``` 
```
sudo /etc/init.d/apache2 restart
``` 

Install MySQL:
```
sudo apt-get install libapache2-mod-auth-mysql
``` 
```
sudo apt-get install php4-mysql
``` 
```
sudo /etc/init.d/apache2 restart
``` 

I then put my website (just a simple index.html for now) into the /var/www/ directory.

Then, from my Windows box I entered in [http://servername/](http://servername/) into the URL and verified I was able to view that page. 

After verifying that the web server worked as an intranet, I logged into my Router (Linksys)
```
192.168.1.1
``` 

I then put port forwarding (there are different names for this in router brands) on for port 80 to 192.168.1.140 (internal address of my webserver)

Then I looked in the router to find out what IP address my ISP gave me (64.x.x.x) and wrote it down. 

Browsed to [www.godaddy.com](www.godaddy.com) and put forwarding on my domain name to that IP address (Note: If you are on DHCP from your ISP this address will change and your site will be down. There are services like DynDNS.org and noip.com that you can sign up for that will change your dynamically changing IP address to your domain name each time it changes)

Waited for the change to replicate and then put in the www address ---- website up and running.

That's as far as I got so far. Going to try for a phpbb2 board and such after I get the hang of it. 

Please feel free to correct any mistake or security risk that my procedure imposes.

---

### Post by cragmonkey on 2005-09-08
I have set up almost exactly the same thing. I can see the site from anywhere in my internal network but in order to get my site to show up on the net I had to edit the /etc/resolv.conf to include my DNS info from my ISP. How long does it usually take to replicate the changes across the internet usually?

---

### Post by UbunuAndrew on 2005-11-19
You had to edit you /etc/resolv.conf ? My /etc/resolv.conf already included my DNS, etc. Although I think I'm going to have to try another way people still cannot see my personal server. I'm not planning to use it for anything much as obviously this is my desktop, and it would be ungodly slow otherwise.

---

### Post by UbunuAndrew on 2005-11-19
My issue has been fixed. I had to edit my port to 8080, because my ISP blocks port 80 so people 'wont' host a website.

---

### Post by gazz on 2006-05-12
[QUOTE=SGC]
1- download xampp from: [http://www.apachefriends.org/download.php?xampp-linux-1.4.15.tar.gz](http://www.apachefriends.org/download.php?xampp-linux-1.4.15.tar.gz)
2 - extract the file with: tar xvfz xampp-linux-1.4.15.tar.gz -C /opt
3 - run the server with: /opt/lampp/lampp start[/QUOTE]

SGC: Thanks, great tip, truly one minute!

But I had to add sudo in front to make it work - there might be other people having the same problem, so I thought I'd share it with them:

1- download xampp from: [http://www.apachefriends.org/downloa...-1.4.15.tar.gz](http://www.apachefriends.org/downloa...-1.4.15.tar.gz)
2 - extract the file with: **sudo** tar xvfz xampp-linux-1.4.15.tar.gz -C /opt
3 - run the server with: **sudo** /opt/lampp/lampp start

---

