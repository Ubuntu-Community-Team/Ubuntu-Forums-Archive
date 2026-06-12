---
title: "looking for an application or script to relaunch a crashed application"
date: 2009-02-18
forum: General Help
---

### Post by iconoclast_tm on 2009-02-18
ktorrent crashes on a regular basis but I don't want to switch clients, I am looking for something that will monitor the program and automatically relaunch it upon crash. all I can find so far is a mac app called keep-it-up which is obviously useless to me. I'm by no means a great scripter but I can usually fidge my way through if someone points me in the right direction. thanks in advance.

---

### Post by mikewu on 2009-02-18
If it doesn't have to be up instantly, I think cron or a shell script could work. 

```
#! /bin/sh
pgrep ktorrent
if [ $? != 0 ]; then ktorrent & fi

```

Then run crontab -e and add the job.
* * * * * /home/user/check_ktorrent.sh

If you want to do just in a shell script

```
#! /bin/sh
while [ 1 ];
do
sleep 60;
pgrep ktorrent;
if [ $? != 0 ];
then 
ktorrent &
fi
done
```

---

### Post by bodhi.zazen on 2009-02-18
> **iconoclast_tm said:**
> ktorrent crashes on a regular basis but I don't want to switch clients, I am looking for something that will monitor the program and automatically relaunch it upon crash. all I can find so far is a mac app called keep-it-up which is obviously useless to me. I'm by no means a great scripter but I can usually fidge my way through if someone points me in the right direction. thanks in advance.

I know you stated you do not wish to change clients , but ...

First, I would try to address why ktorrent is crashing & fix that. Run it from teh command line and post any error messages.

Second, while writing a script is easy, an alternate *might* be an alternate torrent client.

I respectfully suggest you consider rtorrent, it is command line only, but you can run it in the background with screen and automate the process greatly.

        [http://kmandla.wordpress.com/2007/05/02/howto-use-rtorrent-like-a-pro/](http://kmandla.wordpress.com/2007/05/02/howto-use-rtorrent-like-a-pro/)

        [http://www.g-loaded.eu/2007/06/23/rtorstat-a-simple-rtorrent-status-web-page-generator/](http://www.g-loaded.eu/2007/06/23/rtorstat-a-simple-rtorrent-status-web-page-generator/)

Otherwise, yes running a script from cron makes sense.

---

