---
title: "How to setup mysql so you can connect to it"
date: 2009-03-07
forum: General Help
---

### Post by jonwcode on 2009-03-07
How can I setup mysql server so that I can connect to it from another PC? I'm using a DNS right now. And I have ubuntu server install on my server. Mysql is install, and so is apache2. I'm able to view my pages fine in the www folder.

The problem is that I can't connect to mysql database from my computer here. My server is here at home. I was able to setup FTP on my server as well... All of that works okay... The last and final things that I need to get working is my SMTP server to work and to be able to connect to mysql server from my computer in my home without being on localhost. So how is this done? I've had people tell me to change the my.cnf file but whenever I change that file and then go to restart mysql server it, fails to start. So what am I doing wrong here?

---

### Post by warp99 on 2009-03-07
> **jonwcode said:**
> How can I setup mysql server so that I can connect to it from another PC? I'm using a DNS right now. And I have ubuntu server install on my server. Mysql is install, and so is apache2. I'm able to view my pages fine in the www folder.

The problem is that I can't connect to mysql database from my computer here. My server is here at home. I was able to setup FTP on my server as well... All of that works okay... The last and final things that I need to get working is my SMTP server to work and to be able to connect to mysql server from my computer in my home without being on localhost. So how is this done? I've had people tell me to change the my.cnf file but whenever I change that file and then go to restart mysql server it, fails to start. So what am I doing wrong here?

Did you port forward 3306 from your router to the host machine? That's the mysql default port I have setup for my MythTV server. Also are you allowing this port open on your firewall if you have this setup? In any case this is not very secure since anyone can access the database from the web. The best course of action is to setup a SSH tunnel, then port forward 3306 from your machine to the host.

---

### Post by jonwcode on 2009-03-07
How is the ssh done?

---

### Post by warp99 on 2009-03-07
Here's a howto in setting up SSH:

[https://help.ubuntu.com/community/SSHHowto](https://help.ubuntu.com/community/SSHHowto)

The guide also shows you how to set up Putty if you use Windows to access the server. Once you set that up you can port forward your local port to the mysql port on you server like this:

ssh -L 3306:localhost:3360 <remote_machine_IP>

That way your local machine will access the remote port just like if the port was on the local machine. Putty has options to do these with the GUI. Just Google a little, there's tons of information on how to do this. I would also set up you FTP server in the same manner if it's not public facing.

---

### Post by smooch101 on 2009-03-07
This might work:
[http://joeabiraad.com/linuxunix/installing-lamp-on-ubuntu-710-linuxapachemysqlphp/100](http://joeabiraad.com/linuxunix/installing-lamp-on-ubuntu-710-linuxapachemysqlphp/100)
i used this guide and it all WORKED.
when you install mysql it should be configured in apache then any scripts that require mysql will exucute.

Also follow the steps in the link above to install phpmyadmin to configure databases
If you can view scripts using for example 192.168.0.x or your modem ip on another computer it should all be fine

---

### Post by smooch101 on 2009-03-07
You can use php myadmin to change mysql settings and then you can access it on any computer on the same network

---

### Post by jonwcode on 2009-03-07
I tried installed phpmyadmin but I couldn't direct my browser to it.

---

### Post by warp99 on 2009-03-09
If your not sure what I'm talking about by using SSH here's a recent article about SSH Tunneling and Mysql that explains this in more detail:

[http://www.sitepoint.com/blogs/2009/03/10/how-to-administer-a-remote-mysql-database-using-ssh-tunneling/](http://www.sitepoint.com/blogs/2009/03/10/how-to-administer-a-remote-mysql-database-using-ssh-tunneling/)

---

