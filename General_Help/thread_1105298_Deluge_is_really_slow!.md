---
title: "Deluge is really slow!"
date: 2009-03-24
forum: General Help
---

### Post by nikitas on 2009-03-24
Hello everyone! I'm having problem with Deluge BitTorrent. It's really slow!!! For example I have atorrent with 50 seeders with download speed 3 KiB/s. I've tried the exact same torrent with &#956;Torrent and it reached a speed of 100!!! I have checked my connection and everything works like it should. Also when I run Deluge after a while Firefox becomes very very slow!
Please help me, I'm new with LINUX. Just one week using them.
My version is ultimate ubuntu edition 2.0

---

### Post by mb_webguy on 2009-03-24
Are you behind a router?  If so, then you might not have port forwarding enabled for Deluge.  Deluge and uTorrent use different default ports, so enabling port forwarding for uTorrent will do nothing for Deluge.

To test this, open Deluge and go to Preferences->Network, and click the Test Active Port button.  In older versions of Deluge this will open a web page in your browser and tell you if the ports are open or not.  In newer versions of Deluge an icon will appear next to the button.

---

### Post by nikitas on 2009-03-24
I have done this over and over. The port is open.

---

### Post by mb_webguy on 2009-03-24
How long did you monitor the speed in both uTorrent and Deluge?  Assuming both are set up correctly, there shouldn't be any difference between the two on average.  But like all filesharing protocols, bittorrent is extremely variable, and depends on the exact peers you're currently connected to at any given time.  

If you noticed this difference consistently over a period of an hour or so, then there may be a problem.  But if you noticed this over a period of only 15 minutes or so, it could simply be due to differences in peer upload speeds.

---

### Post by hockeyhead019 on 2009-03-24
that's weird because i had no problem with deluge and speeds but if you really want to you can install uTorrent under ubuntu just follow the directions from this site:

[uTorrent on Ubuntu]("http://news.softpedia.com/news/uTorrent-under-Ubuntu-in-3-Easy-Steps-49037.shtml")

worked like a charm for me :)

so maybe that could just be a quick fix for whatever problem you are experiencing with deluge

---

### Post by nikitas on 2009-03-24
The port for deluge is open but it's same with utorrent's. Is that ok?
Should I change something in the preferences of deluge?



I monitored both deluge and utorrent for 40-45 minutes.

---

### Post by mb_webguy on 2009-03-24
As long as the port used by Deluge is being forwarded by the router, the specific port shouldn't matter.

What version of Deluge are you using, the version in the Ubuntu repositories, the one in the Deluge PPA, or the version from the Deluge website (which should be the same as the one in the PPA)?

---

### Post by hockeyhead019 on 2009-03-24
idk bout that one... i don't think that the ppa is up to date with the website but i'm not positive on that

---

### Post by Draugen777 on 2009-03-24
Hey guys, i have pretty much the same problem...deluge is very slow... i checked the ports on deluge and they are not open...anyone knows how do i change that?

---

