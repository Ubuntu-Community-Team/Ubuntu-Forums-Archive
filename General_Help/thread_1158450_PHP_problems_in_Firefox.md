---
title: "PHP problems in Firefox"
date: 2009-05-13
forum: General Help
---

### Post by emilav on 2009-05-13
I have some problems with opening PHP files in Firefox. 
The browser tries to download instead of opening and running the script.
I tried to set it to default open with firefox, but it still doesn't work.

I use Ubuntu Jaunty and latest Firefox version (that came with the distribution).

I googled the problem and I found clearing cache and cookies could help. I tried, no improvement.

Emil

---

### Post by albert ozzy on 2009-05-13
Running local php files from file manager would not help you run the php script in Firefox.PHP is a server side scripting language.So in order to make your scripts work you have to install php and a webserver(e.g: apache) onto your machine then you have to point firefox to your local server address(e.g: [http://localhost/index.php](http://localhost/index.php)). This way you can run the scripts inside your php file.

---

### Post by emilav on 2009-05-13
Yes. I have a server installed.

How do I point firefox to my localhost?

Thanks for the quick reply.
Emil

---

### Post by albert ozzy on 2009-05-13
if you haven't changed it, the address after default apache installation is [http://127.0.0.1/](http://127.0.0.1/) (You should see the text: "It Works"). You can have a detailed explanation about how it works or where to put your files from here:

[https://help.ubuntu.com/community/ApacheMySQLPHP#Installing%20Apache%202]("https://help.ubuntu.com/community/ApacheMySQLPHP#Installing%20Apache%202")

---

### Post by Kareeser on 2009-05-13
emilav, please note that albert ozzy's suggestions pertain to _HOSTING_ PHP pages. If you have problems with viewing PHP pages on other websites, then you are getting the wrong information.

---

### Post by albert ozzy on 2009-05-13
Ohhh! I've never thought of it. @Kareeser is absolutely right. I was giving info about php files that you write or have on your disk. I'm not talking about browsing php files on other sites (like this one)

---

### Post by emilav on 2009-05-13
Well, that's exactly the problem.

I can open my own. My localhost is working fine. 

It's other websites that are a problem.
For exp. I am not able to post here from my computer.

Emil

---

