---
title: "Torrent Downloader with Web GUI"
date: 2009-05-19
forum: General Help
---

### Post by Th0rn0 on 2009-05-19
Hey all,

Getting my Ubuntu server up and running (again).

Was wondering if there is a torrent downloader that has a web GUI for me to admin from my Main rig. CBA SSH'ing in or Remote desktop.

Thanks

---

### Post by kpkeerthi on 2009-05-19
Transmission w/ Web GUI 
rtorrent w/ wtorrent (the web GUI). [http://www.wtorrent-project.org/trac/]("http://www.wtorrent-project.org/trac/")

---

### Post by colau on 2009-05-19
> **Th0rn0 said:**
> Hey all,

Getting my Ubuntu server up and running (again).

Was wondering if there is a torrent downloader that has a web GUI for me to admin from my Main rig. CBA SSH'ing in or Remote desktop.

Thanks
+1 for Transmission.
From Applications>Internet>Transmission BitTorrent Client

---

### Post by lovinglinux on 2009-05-19
Forget about Transmission. What you are looking for is Deluge. It has a great webui, plus remote gtk and remote cli. With the remote gtk interface you will not be limited by webui refresh and other stuff. The frontend interface is installed on your machine, but it connects to Deluge daemon on the server. It's really great. Besides, Deluge has a lot more features than Transmission.

Deluge is in the repositories, but I suggest you add it's [PPA repository](https://launchpad.net/~deluge-team/+archive/ppa) to keep it updated. You also can download the deb file from [here](http://www.getdeb.net/app/Deluge).

For more info about deluge: [http://dev.deluge-torrent.org/wiki/Faq](http://dev.deluge-torrent.org/wiki/Faq)

---

