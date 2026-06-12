---
title: "NetBeans 6.5 xampp PHP"
date: 2009-05-17
forum: General Help
---

### Post by lazman on 2009-05-17
I would like to setup NetBeans 6.5 to use to develop a PHP application. I have installed xampp and it appears to be working good. I have also installed NetBeans 6.5. It seems to be working also, I have been following these webpages. [http://www.netbeans.org/kb/trails/php.html](http://www.netbeans.org/kb/trails/php.html)

On this page [http://www.netbeans.org/kb/docs/php/wish-list-lesson1.html](http://www.netbeans.org/kb/docs/php/wish-list-lesson1.html) at the top on Creating the User of the Database. NetBeans fails to connect to mysql. I have tried using root and the password when setting up xampp and I have also tried using lampp and the password when setting up xampp. It still fails to connect. However, when I browse to [http://localhost/phpmyadmin/](http://localhost/phpmyadmin/) I can login as expected. I do not understand why it will not work as expected. 

My question is this. Has anyone here setup an environment such as this? If so what is the correct procedure to follow? 

The application I will be working on with have a lot of input fields, check-marks, and such on the interface, and I foresee quite a few tables being used on the database. This will eventually be in a production environment. I have used PHP for a while now, but I have always used a windows platform for creating projects. It looks like NetBeans is a good IDE for a large project. This is why I have chosen NetBeans. 

Question two. Has anyone here developed a large PHP, MySql, AJAX project, if so, what development environment did you use?

I have tried searching for the answer to these questions and have not got a clear answer. If this has been answered before please provide a link!

I am using Ubuntu 9.04 64bit
Thank you!

---

### Post by lazman on 2009-05-17
Well, this is just too annoying. I am probably missing something small to make this work, but I just can't find it. It is frustrating to have a decent working environment to work on a PHP application on linux. Now I see why most people just uses simple text editors in linux to get things done.

Disappointed...

---

### Post by rootkowski on 2009-06-03
I've been using many different versions of netbeans and have the very same problem. Now, I decided to finally fix it so I ambitiously googled for the whole error message that Netbeans gives. It paid off :)

The problem is that Netbeans connects over the network, right, using port 3306, while lampp (mysql) has skip-networking option activated. The result of that setup is as painful as we know. To get it working go to /opt/lampp/etc and open the my.cnf file as root. Comment out the line ```
skip-networking
``` and restart the xampp server (sudo /opt/lampp/lampp restart). DONE!

---

