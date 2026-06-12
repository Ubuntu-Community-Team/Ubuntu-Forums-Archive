---
title: "PHP's GD image library?"
date: 2009-05-19
forum: General Help
---

### Post by Lakeside5 on 2009-05-19
I'm not really sure where this would go, sorry if I guessed wrong :) 
I have installed Joomlawork's Simple Image Gallery Pro into my Joomla website, and it doesn't seem to display the embeded photo gallery into my content (I apologize, I don't expect everyone to know what the heck I am talking about lol..just wanted to put this next part in context..) so I did some checking and found this on Joomlawork's website: In order for Simple Image Gallery PRO to function properly, please make sure that you are running at least PHP 4 and that PHP's GD image library is installed on your server (common webhosts have GD installed by default).

You also have to make sure that Joomla's /cache folder is writable, in other words, check that the permissions for this folder are 755 or 777.

So..I did the last part (permissions) but not sure about the php gd image library, would I check the synaptic package thing for that, and if it is not there, how would I get that? Sorry this post is so long, thanks for any help.

---

### Post by ad_267 on 2009-05-19
yes, just search synaptic for php gd, and you should find the package you need to install is php5-gd

---

### Post by guywithcable on 2009-05-19
You can also do it from a terminal with:

```
sudo apt-get install php5-gd
```

---

### Post by Lakeside5 on 2009-05-19
thanks to you both, good advice. I installed in the terminal and checked the synaptic, and it is there.  But I still cannot see the image gallery, must be a different problem.

---

### Post by guywithcable on 2009-05-19
You may have to restart Apache...

```
sudo /etc/init.d/apache2 restart
```

---

### Post by ActiveFrost on 2009-05-20
If you don't see it after restarting Apache, check if it's enabled ( installing does not mean enabling ) in php.ini.

---

