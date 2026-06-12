---
title: "help with php"
date: 2009-05-04
forum: General Help
---

### Post by gfunkera on 2009-05-04
im a bit new to php and webservers...
 
i made a web server on my computer at home (apache2, phpmyadmin, theres also a mysql database there) and i can go localhost and use the site on my computer...
 
i came to work with all the html and php files to test it and work on it while im here..
 
the machines at work are using Vista..
 
i can open html files but whenever i try to access a .php from these computers, it never works.. the computer is asking me if i want to save the file to my computer, it wont actually open it like it does on my computer at home.. the web browser doesnt run the php script for some reason... it thinks its just a bunch of text or something..
 
i know that php runs on this computer (at work) because i go on websites that utilize php scripting...
 
any ideas on why its not working?

---

### Post by gfunkera on 2009-05-04
update: i just took the code in the .php files and embedded them into html files and updated all the links that the site uses so that it accesses the HTML files... it seems to work.. the CSS styles that i assigned are visibly working but the php portions of the code still arent showing up these windows machines... anyhelp?

---

### Post by Kai-vana on 2009-05-04
When you are at work are the files sitting on a properly configured web server? PHP is server side code it&#8217;s the server that interprets the code and gives the browser only the code it needs, if your files are say on a USB pen and you try browse to them from your web browser it will not work.
Your best bet is to set up your web server at home so you can see it from the web then the PHP code will work, you can then use FTP to get/put the files onto your web server.

---

### Post by gfunkera on 2009-05-04
hey thanks for your reply.. i was wondering if you could help me figure out how to set up my computer so that it can be accessed at work.. that sounds like esactly what i need.. that way i can go home and change what i need then come to work and test it...
 
you are awesome in advance!!:popcorn::popcorn:

---

### Post by Kai-vana on 2009-05-04
Ok your web server will be already running on port 80(default for web servers) all you will need to do to forward incoming port 80 to your PC in your router.

Then to access your server from any ware, enter your home external IP address into the browser.

Take a look at DynDNS.org if you are on a dynamic IP address at home. This will allow you to use a pseudo domain name that links to your (variable) home IP address and is free.

Note: Running a web server from your home PC may be against the terms and conditions of your ISP.

---

