---
title: "Way out of my league here -- hosting a website"
date: 2009-04-06
forum: General Help
---

### Post by nothingspecial on 2009-04-06
Ok, I`ve just offered to host my kids youth football team`s website. What should I be looking at. What do I need.

Thanks

---

### Post by KayakJim on 2009-04-06
If you plan to do anything with a database (e.g. storing player information and stats) then you will need MySQL (database engine) or you might be able to get away with SQLite.

You will need Apache (web server) to actually respond to requests and serve the pages.

If you plan to create dynamic pages using PHP then that will also need to be installed.

Before starting, you should ensure your repositories are up-to-date so run:
```
sudo apt-get update
```

To install MySQL, run:
```
apt-get install -y mysql-server mysql-client libmysqlclient15-dev
```
You will be prompted to provide a password for the root MySQL user.

To install apache, run:
```
sudo apt-get -y install apache2 apache2-doc apache2-mpm-prefork apache2-utils apache2-suexec libexpat1 ssl-cert
```

To install php, run:
```
sudo apt-get -y install libapache2-mod-php5 php5 php5-common php5-curl php5-dev php5-gd php5-imagick php5-mcrypt php5-memcache php5-mhash php5-mysql php5-sqlite
```

If you installed PHP, then you will need to restart Apache so it catches the changes:
```
sudo /etc/init.d/apache2 restart
```

Are you doing the development or will someone else? If someone else, then you will probably need an FTP server so they can connect to the server and upload/download files.
```
sudo apt-get -y install proftpd ucf
```
and select Standalone mode.

That will get you a standard and basic web server. Hopefully the above is of some help to you. :)

---

### Post by r1ch on 2009-04-06
Hi there,

are you intending to host the site on your own computer? Or manage the hosting for them by using a third party web hosting service?

If you are only going to be hosting their site on your own machine it may be a lot more work than is worth it for the benefit, as well as there being additional risks with opening up your computer as a web server.

If your intent was to use linux, then a vast majority of third party hosts have the option to use a shared linux server and it could save you a great deal of time and effort. 

any thoughts?

---

### Post by nothingspecial on 2009-04-06
> **KayakJim said:**
>  Hopefully the above is of some help to you. :)

Of some use to me :shock:

Thanks a million. I`ll get started on that right away. Brilliant  :KS:KS

---

### Post by nothingspecial on 2009-04-06
> **r1ch said:**
> Hi there,

are you intending to host the site on your own computer? Or manage the hosting for them by using a third party web hosting service?

If you are only going to be hosting their site on your own machine it may be a lot more work than is worth it for the benefit, as well as there being additional risks with opening up your computer as a web server.

If your intent was to use linux, then a vast majority of third party hosts have the option to use a shared linux server and it could save you a great deal of time and effort. 

any thoughts?

Oh, ........ tell me more. I was just planning on using my "home server" ie the old desktop that currently resides underthe stairs and has all my music and vids on it to host a website. But I am totally new to this stuff. Please expand.

---

### Post by r1ch on 2009-04-06
I guess the two options you have are, as you were originally planning to do, to host your own site or pay someone else to do it. 
Hosting it yourself is not something I have done myself, I only have apache running as a local web host and have never used it 'webside'. I probably would be loathed to as well, I think you would first need a static IP address, and there are probably other technical requirements set down by whichever organisation in your country is the internet registrar... in the UK it is [**_Nominet_**]("http://www.nominet.org.uk").

If you use a dedicated hosting company, most of the work is taken away from you. Usually all you have to do is sign up, pay the fee, wait a few days for the registration to go through and then upload your web site's files to the address they provide you upon registration. They usually provide additional services such as managed domain specific web-email accounts such as 'thecaptain @ myfootballteam.com' and so on.

Worth asking the person who designed your site what sort of technologies/language it uses as the more niche the tech, the less options you will have and the more you will have to pay. Usually a standard html/php site (possibly with a bit of MySQL) should be fine in most instances.

An example of a host I have used in the past is [**_Streamlinenet_**]("http://www.streamlinenet.co.uk/"). There's no reason to choose them over others, its all personal preference, but do have a look at the different options they have available as many will be standard across the industry.

Have a browse around, why not do a google search for "Web hosting" and see what's available in your country, and if you're comfortable letting the forum know which country you're in then somebody may have suggestions as to companies they've used in the past.

If you're fine with a bit of advertising then you may get a free option with a bit of looking around.

There are plenty of usefull guides and most hosts will have a beginners set up guide, feel free to message back if you have any questions.

---

### Post by wylfing on 2009-04-06
> **nothingspecial said:**
> Oh, ........ tell me more. I was just planning on using my "home server" ie the old desktop that currently resides underthe stairs and has all my music and vids on it to host a website. But I am totally new to this stuff. Please expand.

This is...a pretty bad idea. Now, it is entirely possible to install the software you need to serve web pages. In fact, it's easy to do so. 

However, what you're talking about doing involves putting your server "out there" on the Internet for everyone to abuse. That is not a trivial responsibility, unless you like the thought of being turned into a relay station for spam, malware, and illegal porn.

Properly running a secure server is best left to the professionals. Go spend $15 on some cheap hosting service and leave it at that.

---

### Post by nothingspecial on 2009-04-07
Thanks for the advice guys. I`ll have a dig around and keep you posted.

---

### Post by hyper_ch on 2009-04-07
you don't need a static IP to host your website on your home computer but it makes things a lot easier.

First question: Do you have a static ip or not?
Second question: Do you have your own domain name or not?

---

### Post by nothingspecial on 2009-04-07
> **hyper_ch said:**
> you don't need a static IP to host your website on your home computer but it makes things a lot easier.

First question: Do you have a static ip or not?
Second question: Do you have your own domain name or not?

Not yet and I`m starting to think paying for this service might be a better short term idea.

However managing to do it eventually is something I am keen to try.

---

### Post by hyper_ch on 2009-04-07
paying for what service?

---

### Post by nothingspecial on 2009-04-07
Having the website hosted.
By a company that hosts websites
At least until I know a bit more about it.

---

### Post by hyper_ch on 2009-04-07
it's not difficult to host one's own website... it's more difficult to host one's own email server...

but I asked two questions and without an answer I can't provide help.

---

### Post by nothingspecial on 2009-04-07
The answer to both questions was not yet. In that from what I have read I understand I need both a static ip and a domain name I just haven`t done it yet.

The football club has a registered domain name  nameofclub.co.uk

But I understand I need one aswell.

---

### Post by nothingspecial on 2009-04-07
Thankyou for your help by the way.

I am reading about hosting web sites and there is a lot of information out there. I was hoping to have my searched narrowed by someone more knowledgeable than myself

---

### Post by Ben Crisford on 2009-04-07
If I were you I wouldn't host it on your computer, get a free host off the internet.

Mine is great, no-ads 10GB banwith and plenty disk space.

So check out [www.x10hosting.com](www.x10hosting.com) ;).

I don't remember the exact details.  You get a sub-domain of x10 either <yourname>.pcriot.com, <yourname>.exofire.net, <yorname>.x10hosting.com and one other but I don't remember.

You get 5 mail accounts, a cPanel with mysql phpmyadmin and all that :D, three sub-domains, webmail, file manager, f2p access...

I don't remember everything I get but its pretty cool.

Obviously you can re-direct a domain name there.  I use a free domain from:
[www.freedomain.co.nr](www.freedomain.co.nr) (which gives you <yourname>.co.nr FREE)
[www.co.cc](www.co.cc) (gives you <yourname>.co.cc FREE)

Hope this helped.

---

### Post by t.rei on 2009-04-07
I honestly suggest getting the website hosted "out of house". Meaning not in your house and not on your own server and internetconnection.

As soon as you start hosting some movies and pictures this can clog up your personal bandwidth big time. Especially when they are new and everyone and their grandparents want to get them. Also professional webhoster do usually have some sort of redundancy in hardware or software. So your website has a certain reliability regarding uptime. 

Some things you need to keep an eye on:
Traffic - a 500MB Video downloaded 50 times... well... it adds up. Carefull here!
Content - you may not host adult content or "similarly doubtfull" material on any host.

There are a lot of good hosts out there, and a lot of rubbish. Read carefully. Ask questions. Phone them and see if they are competent. Hey, you can also just ask here.

---

### Post by hyper_ch on 2009-04-07
well, if you host them on your own computers then you should have a decent upload on your internet connection. Also you might need to check with your ISPs terms & services - as they might forbid tha you have an active server.

However a static IP address is not required - it just makes things easier.

Also on home-hosting you need to have a backup plan. You should have backups anyway for all the computing stuff you do.

---

### Post by mb_webguy on 2009-04-07
If you have broadband internet, your IP address is going to be relatively static.  With an always-on internet connection, your IP is usually only changed if you get disconnected for some reason and have to reconnect.  

As long as this is the case, then hosting your own website is actually a lot easier than some here have indicated.  (And stick with me here, because while it may take me a bit to explain, it really *is* rather easy, even for a beginner.)

First, you'll need to install a webserver on the machine you want to act as the host.  In Ubuntu, this is extraordinarily simple.  Just open Synaptic, go to Edit->Mark Packages By Task, check the box next to "LAMP Server", click OK, and then click Apply.  Congratulations, you now have the Apache webserver installed, along with support for the PHP scripting language and the MySQL database.  You can test it by entering "localhost" in your web browser's address bar.  

Now, if you're behind a router, you need to give the host computer access to the router.  First, go to System->Network Configuration and give the host computer a static IP.  You'd do this by editing your network configuration, selecting the IPv4 Settings tab, selecting Manual, and entering the appropriate data for your computer and network.  For example, the internal IP address of my router is 192.168.2.1, and I'd use this for the Gateway and DNS Servers, with a Netmask of 255.255.255.0, and I'd set an Address for the computer of 192.168.2.xx (with xx being whatever I want as the static internal IP for the computer).

The second part of exposing the server to the outside world involves some router configuration, and I can't walk you through it because the exact method differs from one manufacturer to the next.  Basically, you need to enter your router's IP address (which for my Belkin router is 192.168.2.1) in your web browser to open your router configuration page.  Next you need to look for something like "port forwarding" or "virtual servers", to set up port forwarding for the web server.  This basically involves adding an entry for the web server's IP address (which is whatever you previously set), a port (which in the case of a web server would be 80), and a protocol (which for a web server would be TCP).

Now, if you type in your external IP, which you can find (among other places) on your router's configuration page, it should go to your new web server.  Of course, we don't want to have to use the IP to get to the server, but unless you're really sure you want to start hosting a web site, you don't want to have to buy a domain, either.  So that's where a URL redirect service comes in.  There are several free URL redirect services out there, but the one I've used in the past is [No-IP]("http://www.no-ip.com/").  You basically sign up for a free account, give it your webserver's external IP, create a domain name, and you're done.  No-IP even has a client that will update your No-IP account for you if your external IP address changes.

As to making the web site itself, everything you need to know can be found at [W3Schools]("http://www.w3schools.com/").  Your html and php files go in the /var/www directory (which you may need to use sudo to access unless you change some permissions, but I'm not sure).  The XHTML tutorials will teach you everything you need to know to make a simple, static web page.  For more complex pages, you'll need to learn a bit of PHP or JavaScript.

---

### Post by GoldNugget on 2009-04-10
Whether you host the site yourself or not should really depend on how much work you want to do. As others have stated, paying for hosting is by far the easiest and fastest way to go. However, you don't learn anything.

If you are curious to try, I think you should. There are lots of great tutorials on the web for getting started. I would suggest starting with a basic web page, using just Apache. You can choose to add email, databases or interactive pages later if you need them. A simple webserver is not that hard to set up and manage.

If you need a gui to administer it, there is Webmin, which has improved greatly over the years and is quite intuitive. 

I have a static IP address, but I know others who host without it, using a free service such as dyndns to keep it updated.

If you don't enjoy tinkering, then go with a paid service. If you want the experience and pride of doing it yourself, go for it! If this 50 year old grandma can do it, so can you.

---

