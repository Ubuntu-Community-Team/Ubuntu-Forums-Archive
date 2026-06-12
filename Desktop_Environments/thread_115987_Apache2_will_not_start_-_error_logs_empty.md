---
title: "Apache2 will not start - error logs empty"
date: 2006-01-11
forum: Desktop Environments
---

### Post by jamespi on 2006-01-11
hi,

i have an atlhon 1100 512MB running breezy with a k7 kernel. the only things i installed without apt-get/synaptic was firefox 1.5 and at one stage i tried to install peerguardian but  dont think it happened.

i set up ruby on rails with apache2 (no mean feat in itself) and everything was fine and dandy, then two months after i first booted up my clean install of unbuntu i had to restart it (i had switched the sound over to alsa in order to get scummvm to play sounds properly and the FAQ told me i had to restart)

anyway i couldnt log in to gnome - this was the solution ([http://ubuntuforums.org/archive/index.php/t-1583.html](http://ubuntuforums.org/archive/index.php/t-1583.html))

so now everything is up and running except apache2 which wont start.

i tried this: 
sudo /etc/init.d/apache2 restart

and all i got was this:
* Forcing reload of web server  (Apache2)...                     [fail]

so i checked var/logs/apache2/error.log and all other apache logs

but they are empty and have modification timestamps from before i rebooted so they havent even been touched.

my syslog just has hourly timestamps from cron in it.

i tried stopping apache, that just says [fail] too. i tried ps -A, no apache or httpd or whatever in that list.

this far from the first mystery i've had with ubuntu, but this is the first dead end that even the mighty google could not help me out of.

any ideas?

thanks,
james

---

### Post by jamespi on 2006-01-13
BUMP!?!?!?

someone must know something obvious i missed.


dont make me revert to windows for god's sake.

ubuntu will have one less user i'm warning you.......

---

