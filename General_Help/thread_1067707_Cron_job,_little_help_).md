---
title: "Cron job, little help :)"
date: 2009-02-12
forum: General Help
---

### Post by ethernaly on 2009-02-12
Hello, I need to execute a php file every one minute (or every two minutes).

my OS configuration is:
Jeos 8.04 + apache2 + libapache2-mod-php5 + php5-gd + php5-imap + php5-cli + php5-cgi

well, I try to add a cronjob (super user) with :
```
sudo su
crontab -e
```

And I did add this line:
```
*/1 * * * * /usr/bin/php /var/www/file.php
```

After that I restart cron with:
/etc/init.d/cron restart

but this system doesn't not work :S (after one minute, nothing happen, I tried to wait 5 minutes but nothing...)


some1 can help me to configure cron? (I want to execute a php file every one minute ^^)


Thanks a lot and sorry for my bad english.

(I can't use GUI)

---

### Post by mister_p_1998 on 2009-02-12
> **ethernaly said:**
> Hello, I need to execute a php file every one minute (or every two minutes).

my OS configuration is:
Jeos 8.04 + apache2 + libapache2-mod-php5 + php5-gd + php5-imap + php5-cli + php5-cgi

well, I try to add a cronjob (super user) with :
```
sudo su
crontab -e
```

And I did add this line:
```
*/1 * * * * /usr/bin/php /var/www/file.php
```

After that I restart cron with:
/etc/init.d/cron restart

but this system doesn't not work :S (after one minute, nothing happen, I tried to wait 5 minutes but nothing...)


some1 can help me to configure cron? (I want to execute a php file every one minute ^^)


Thanks a lot and sorry for my bad english.

(I can't use GUI)

you need to put "export DISPLAY=:0 &&" in front of the command to tell the system you are outputting to display screen 0 (the first one)
eg:

*/1 * * * * export DISPLAY=:0 && /usr/bin/php /var/www/file.php

I had the same problem when trying to run a GUI program from a cron script. Linux can have many displays, and you have to tell it which one to send to.

Heres an example of my full cron script:

Display=DISPLAY=:0

# Icepodder
56 8,14 * * 1,2,3,4,5 export DISPLAY=:0 && /usr/bin/icepodder

# Kill Icepodder
15 16 * * 1-4 killall python
55 15 * * 5 killall python

# Restart Gdesklets
16 16 * * 1-4 export DISPLAY=:0 && /usr/bin/gdesklets
56 15 * * 5 export DISPLAY=:0 && /usr/bin/gdesklets
# Democracy Player
55 8,14 * * 1,2,3,4,5 export DISPLAY=:0 && /usr/bin/democracyplayer

# Kill Democracy Player
55 14,15 * * 1-5 killall democracyplayer

# Radio Paradise
57 8 * * 1-5 export DISPLAY=:0 && /usr/bin/audacious [http://scfire-nyk0l-2.stream.aol.com:80/stream/1048](http://scfire-nyk0l-2.stream.aol.com:80/stream/1048)
# 55 8 * * 1-5 export DISPLAY=:0 && /usr/bin/audacious /home/steve/music/rp.m3u

# Kill Radio Paradise Stream
28 16 * * 1,2,3,4 /usr/bin/killall /usr/bin/audacious
58 15 * * 5 /usr/bin/killall /usr/bin/audacious

# Note: Lines beginning with "#\" indicates a disabled task.


Steve

---

### Post by geirha on 2009-02-12
If you install the [mailx](apt:mailx) package, cron will mail you if there are any output from the command. Read such mail with 
```

mail
# or if it gets sent to root
sudo mail

```

Also, */1 can be set to simply *, because a * in the minute field means every minute.

---

### Post by hyper_ch on 2009-02-12
install php-cli then you can run php scripts by php /path/to/script.php

---

### Post by ethernaly on 2009-02-12
Thanks all :-)

---

