---
title: "Gallery2 help needed (."
date: 2006-01-10
forum: General Help
---

### Post by Lofticus on 2006-01-10
Hi guys, I installed Joomla, downloaded com_gallery2 (installed it) and installed gallery2 in my /var/www/, then made my browser finish the gallery2 installation.

gallery2 is functioning now in [http://günay.net/gallery2](http://günay.net/gallery2)

however, if I want to access that in my backend in Joomla it throws me an exception:

> Fatal error: Call to undefined function: curl_init() in /var/www/components/com_gallery2/classes/g2curl.class on line 69

I've googled and forum'd for that thing about 3hours now.
In some forum there's standing i have to active curl in my php.ini, but where is that php.ini and how do I activate it?

Please help, I really need this going!

Ty, lofticus

---

### Post by Lofticus on 2006-01-10
Oh someone just has to know how I can change this? 

damn gallery ):

---

### Post by LanceM on 2006-01-10
I have not had this happen to me personally. All I have heard/read about it is the need to restart Apache and it should start working.

---

### Post by lamego on 2006-01-10
Just installing the curl php module should be enought:
sudo apt-get install php4-curl (or php5 if its the case)

Then i am not sure if you need to restart apache (i think the package install already takes care of that).

---

### Post by LanceM on 2006-01-10
Wouldn't hurt to restart apache just to be sure.

---

### Post by Lofticus on 2006-01-11
well I just took an older version of gallery 2 (2.10 instead of 2.11) which now works flawlessly... but thanks for the advise, I will look into upgrading!

Lofticus

---

