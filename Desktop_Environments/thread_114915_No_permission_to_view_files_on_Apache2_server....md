---
title: "No permission to view files on Apache2 server..."
date: 2006-01-09
forum: Desktop Environments
---

### Post by bskov on 2006-01-09
Three times....  have I installed Ubuntu with Apache+PHP5 and it has never denied access to files on the server.

But this time Apache2 and php5 is not really working - I've tried to uninstall and reinstall and edit a lot of conf-files but nothing works.

when I open a simple HTML-file on the server i get this error.

```
[SIZE="5"]Forbidden[/SIZE]

You don't have permission to access /index.html on this server.
Apache/2.0.54 (Ubuntu) PHP/5.0.5-2ubuntu1.1 Server at localhost Port 80
```

well.... it does allow some access. since I am allowed to view the testphp.php wich I created with ```
sudo gedit /var/www/testphp.php
```

If i simply copy and paste in a HTML document it will not be shown - but if I copy the content of a HTML document and creates a new document with ```
sudo gedit /var/www/test.html
``` and pastes in the HTML-code it works fine.

But don't want to paste in hundreds of pages of code - there must be some configuration.

I also usually use an alias to use my /home/brian/websites as the place for my websites. But when I try to access files trough the Alias I get the same permission message.

- Hope someone has the answer for this - cause I need the server real bad.



---- To all the UBUNTU people developing - Nice work

---

### Post by Randomskk on 2006-01-09
If you know where the file is that you're not allowed to access...
sudo chmod 777 /path/to/file.php
or, if it's a dir (or you want everything in a dir allowed)
sudo chmod -R 777 /path/to/dir

try that, see if it helps

---

### Post by bskov on 2006-01-09
OK :razz: :smile: :D :) :smile: :p   - that was the trick

I have spend huors on this s....t an then you fix it in seconds  -  THANK YOU

---

### Post by bskov on 2006-01-09
but everytime I paste in a new directory I have to run ```
sudo chmod -R 777 /path/to/dir
``` Again, can it be true ???


well at least it is not as much work as copying all the code :rolleyes: :rolleyes:

---

### Post by Randomskk on 2006-01-09
Hm... well, the easiest thing to do is copy all the directorys now, and then do:
sudo chmod -R 777 /var/www
then all folders and files under /var/www are accessible.
If you make a new folder there, it should hopefully work, or you could always make a script to do the sudo chmod thing. 

Thing here is that it's more of a hack than a fix - really you need to give the user running the web server read (and maybe write for PHP) permissions to /var/www, that should fix it long term.

edit: just to add, I don't think I'm good enough to tell you how to do that, but look into the command chown. It sets who owns directories, I'd geuss chowning /var/www to the apache user should do the trick.

---

