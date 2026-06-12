---
title: "PHP on localhost"
date: 2008-11-18
forum: Desktop Environments
---

### Post by DFHIII on 2008-11-18
I am trying to execute a php script on localhost.  I enter the following URL:
-------------------------------------
[http://localhost/home/dan/BobsAutoParts/orderform.html](http://localhost/home/dan/BobsAutoParts/orderform.html)
-------------------------------------
I get the following response:
-------------------------------------
Not Found

The requested URL /home/dan/BobsAutoParts/orderform.html was not found on this server.
Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.3 with Suhosin-Patch Server at localhost Port 80
--------------------------------------
orderform.html is located at /home/dan/BobsAutoParts/ on the local computer.  How do I tell localhost where to fine orderform.html?

Thanks,

Dan H.

---

### Post by anaranjado on 2008-11-18
Hello, DFHIII

Have you installed LAMP server on your computer?

The default PHP script directory is : /var/www/

or you can create a link in /var/www/: ln -s /home/dan/BobsAutoParts/ ./mysite

---

### Post by DFHIII on 2008-11-18
Apache2 is insatlled on my computer.

Below is what I entered from the Terminal and the results:

dan@dan-desktop:/var/www$ sudo -p ln -s /home/dan/BobsAutoParts/./orderform.html
/home/dan/BobsAutoParts/./orderform.html: line 1: syntax error near unexpected token `<'
/home/dan/BobsAutoParts/./orderform.html: line 1: `<html><body>'

'<html><body>' is from the file orderform.html, so it did find the correct file.

I still can't get the browser to find the file.

How do I get permissions to copy the folder BobsAutoParts to the /var/www/ folder?  If I did that would the localhost be able to find the pages?

Thanks,

Dan H.

---

### Post by Mazin on 2008-11-18
Yeah, just copy the whole folder into /var/www and see if it works.
If you don't own /var/www, run nautilus as root (gksu nautilus) and then do the file operations you need.

---

### Post by ad_267 on 2008-11-18
Your link command is all wrong.
```
ln [OPTION]... [-T] TARGET LINK_NAME
```

So you want to do:
```
sudo ln -s /home/dan/BobsAutoParts /var/www/BobsAutoParts/
```

Note the space between the target and the link name.

Then you can go to [http://localhost/BobsAutoParts/orderform.html](http://localhost/BobsAutoParts/orderform.html) to view your page.

---

### Post by DFHIII on 2008-11-18
nautilus worked!!  I was able to move the folder and execute the php code.

I was unable to exit nautilus.  How do I close it?

You got me by a real barrier, now I can procede.

Dan H.

---

