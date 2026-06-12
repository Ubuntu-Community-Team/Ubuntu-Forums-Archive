---
title: "Change Apache Docroot, Lose PHP"
date: 2008-12-11
forum: General Help
---

### Post by ddmorin on 2008-12-11
I am trying to set up a LAMP server (PHP5 in case it's still relevant to say that) with one simple request - I want to point the docroot somewhere other that /var/www.  For the life of me I can't get it to work.  I've made the necessary changes in the config files to change DocumentRoot and Directory.  

That much appears to work in so far as Apache looks in the right spot.  Only if I ask for a *.PHP file it offers to download it, and if I ask for a *.PHP5 file, it displays it as text.

If I simply create a softlink inside /var/www/foo to point to my directory, PHP files work fine.  So I'm relatively confident that Apache is loading all the necessary modules and in general knows what to do with PHP.  It's just the act of changing the docroot that makes it lose that.  (I would rather not go the softlink route, as that would make my sandbox URLs different from my live production URLs and I'd like to prevent that for consistency and testing.  I am working with a legacy application so I have no way of knowing how many variations on absolute URL construction I'd have to deal with.)

I would have thought this a common problem, but I've been googling for 2 days and can't find anything to help.  Most stuff I find is variations of putting the softlink under the default docroot.  I've made no end of changes to the permissions, giving everything under the sun 777, and even changing the apache-run-user to be my own user name and group (the directory I'm testing with is a CVS checkout in my home directory).  No luck, same behavior every time.  I even tried making /var/www itself a softlink directly to my desired docroot, but no dice.

I'm not normally a LAMP guy (coming out of a Rails world), so I apologize if this is a FAQ someplace (or in general a dumb thing I shouldn't be doing) and I've just managed to miss it.  I'm fairly confident that it's something in the apache config I've missed.  Thanks!

---

### Post by albinootje on 2008-12-11
There should be an easy solution to this :

* sudo grep -r -i /var/www /etc/apache2/
* then replace all /var/www by e.g. /var/test in those files
* restart apache

I've just tested this with apache2 on Ubuntu Intrepid, and my test php file loads fine

(Example taken from [http://www.htmlite.com/php003.php](http://www.htmlite.com/php003.php) and saved as index.php)

Did you forget to restart apache ?
Can you try with a different browser ? 
Firefox is sometimes very persistent in using cached files, you can install a clean cache add-on for it. Or test with konqueror or galeon.

---

### Post by albinootje on 2008-12-11
As an add-on. Because i was curious why you had this problem i did a fresh install of apache2 + the php5 apache module. 
I assume that you didn't change a lot more in your apache config compared to the default ?

---

