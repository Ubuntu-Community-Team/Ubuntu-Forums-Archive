---
title: "local php pages won't open in firefox HELP!"
date: 2009-04-02
forum: General Help
---

### Post by fazza on 2009-04-02
hi all
er well I have an IT gcse project that has to be in tomorrow. Admittedly, I have left it rather late, but even so... I am finishing off the web pages at home.
Unfortunately, I am using Dreamweaver to build the pages, so have had to install it through wine at home. It runs fine - dreamweaver is not the issue and is possibly irrelevant.

My issue is - the pages won't display properly in wine-installed browsers, and native firefox won't display them either. They are in xhtml/php code, and when I open them in firefox, it simply pops up a box asking me what to open it with. I have checked other php pages off the net and they work fine, so it is obviously either to do with the coding (although they work fine at school), or the fact that it is locally stored... but I cannot see how that should affect it.

I DO NOT have time to rebuild every page. So if it is simply a case of "do the supporting work then finish the web pages at school", then I guess that'll have to be it...

Sorry if that's confusing :p

Thanks :)

---

### Post by kanikilu on 2009-04-02
You can't just open a PHP file as is like you would a regular HTML file, it needs to have a server to process it.

You'll either need to put them on a remote web server, or you can install Apache and PHP and run a web server on your local host.

The easiest way to do that in Ubuntu is ```
sudo tasksel install lamp-server
``` Of course, this will also install MySQL, so if you don't want that, you'll need to install apache2 and php5 individually.

For more information, check out this page:

[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

---

### Post by fazza on 2009-04-02
ahh ok thanks
that would explain why dreamweaver always shouted at me and no one else - I always seem to go for the different option to everyone else hehe

well that seems to be fine so cheers

even so... I still have to use Dreamweaver O.o not fun :p

oh and being a bit of a website noob... how do I host the pages on localhost? It's probably really obvious :S

cheers :)

---

### Post by kanikilu on 2009-04-02
After installing apache and php, I think the default server path is /var/www, so anything you put in there will be accessible.

All files need to be readable (sudo chmod -R a+r /var/www/*) and I think php scripts need to be executable (sudo chmod -R a+x *.php).

This is of course a simplified view of it. There can be *much* more involved with getting a web server up and working with your pages...

If you have more specific questions, just ask here or the server forum.

---

### Post by fazza on 2009-04-02
ok well I've set up /var/www and copied in my whole project... and set the permissions (why doesn't the "Apply to Enclosed files and folders" button work on files?). But now, the same box just pops up and asks me what I want to open the .php with. would I neeeed to restart my computer after installing apache? or is there a command I can run to start the server?

Thanks

---

### Post by kanikilu on 2009-04-02
I don't think you have to restart, but to force apache to restart (which you have to do if you make any configuration changes), you can use ```
sudo /etc/init.d/apache2 restart
```

I'm not sure why it's still asking you to download, though. Are you sure the PHP files are executable?

Also, I would try creating a new, very simple page to test with, for instance: ```
<?php phpinfo(); ?>
```

// Edit - You shouldn't necessarily need to do this, but if it's still not working, try adding **#!/usr/bin/php** to the top of your script (outside the php tags).

---

### Post by fazza on 2009-04-02
cheers, the problem was that they weren't executable... didn't know they needed to be, micro$oft created them :p (btw what are the limits to names we can call microsoft on here? hehe)

well, kinda works now. At least firefox displays them, just got to sort out file references and links. They are being really nasty to me :S

---

### Post by kanikilu on 2009-04-02
Glad you got it setup. Good luck getting everything else working and getting the project done in time ;)

---

### Post by fazza on 2009-04-02
thanks a lot, at least I can now use it in the future :p

unfortunately something in the wine registry broke, so i had to do a hacked re-install of Dreamweaver. Now I can't insert anything into the webpage without the whole program dying. So i've had to succumb to windows :'( and now i'm running dreamweaver in a vm of win7 beta.

I hate windows.

cheers anyway :)

---

### Post by fazza on 2009-04-05
aww it doesn't work again :(
I have php5 and apache2 installed, and all the php files are set as executable, can't think of anything else to do for it :\
The webpages need to work in firefox cos that's what the exam moderators are using to mark our coursework...

any ideas?

cheers :)

---

