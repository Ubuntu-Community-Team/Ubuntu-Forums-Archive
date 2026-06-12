---
title: "Rtorrent Basics"
date: 2008-12-29
forum: General Help
---

### Post by j.smith on 2008-12-29
[B]Hi

I install Rtorrent Today . and i found they 
are different configuration some suggest 
to use  XMLRPC-C  and other suggest to use 
PUTT/openssl  so my question is 

- how to add the torrent file 
- can i put torrent file in 
folder and point the link to that folder
- rtorrent.rc where to put this file 
and what modify .
- What configuration i use 

:popcorn:

Regards
[/B]

---

### Post by rampageoberon on 2008-12-29
Hi,

With regards to adding torrents and controlling rtorrent please refer to [http://libtorrent.rakshasa.no/wiki/RTorrentUserGuide](http://libtorrent.rakshasa.no/wiki/RTorrentUserGuide)

For the .rtorrent.rc configuration file it should be in the home directory. When you run rtorrent a default one will be automatically created for you. Refer to [http://libtorrent.rakshasa.no/browser/trunk/rtorrent/doc/rtorrent.rc?rev=latest](http://libtorrent.rakshasa.no/browser/trunk/rtorrent/doc/rtorrent.rc?rev=latest) and [http://libtorrent.rakshasa.no/wiki/RTorrentCommonTasks](http://libtorrent.rakshasa.no/wiki/RTorrentCommonTasks) for more guidance and if you have any specific questions do ask.

Hope that helps

---

### Post by j.smith on 2008-12-30
What the different between config Rtorrent 
with "XMLRPC-C" and configuration with "openssl(SSH)"

---

### Post by hyper_ch on 2008-12-30
if you want to run rtorrent I'd first advice to have a read here:

[http://kmandla.wordpress.com/2007/05/02/howto-use-rtorrent-like-a-pro/](http://kmandla.wordpress.com/2007/05/02/howto-use-rtorrent-like-a-pro/)

Also I would set a session and watch folder (enabling them in the config and create according directories). If done, then you just download the .torrent files into your watchfolder.

In addition I also recommend you have a read at this:  [http://jmcpherson.org/screen.html](http://jmcpherson.org/screen.html)

And then, as the previous poster has pointed out, have a look at te rtorrent userguide and also common tasks.

If you say any keycombos that are like:  ^a --> it means:  ctrl+a

---

### Post by tsali on 2008-12-30
THIS IS IMPORTANT!

If you are connecting to rtorrent through SSH or something similar, remember that rtorrent typically runs as a user process.

Therefore, when you logout - it quits!

What I did was install SCREEN and start a session specifically for rtorrent, disconnect from it THEN logout. The rtorrent session remains active, watching the folder you want it to watch.

You can name sessions in screen. I called mine rtorrent. I simply enter "screen rtorrent" to reconnect to it at the command line.

Also, take care to set your upload/download throttle and your cutoff ratio or rtorrent will try to monopolize your internet connection.

If you are running a server, you can set the default actions for torrent files on your client machines to download torrent files directly to your "watched" folder on the server (via Samba).

---

