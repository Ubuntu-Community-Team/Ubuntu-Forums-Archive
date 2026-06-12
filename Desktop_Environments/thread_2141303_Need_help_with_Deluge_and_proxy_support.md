---
title: "Need help with Deluge and proxy support"
date: 2013-05-02
forum: Desktop Environments
---

### Post by nleibert on 2013-05-02
Hi guys, I'm having a problem getting Deluge to work with torrents while using a SOCKS5 proxy.

I'm using Ubuntu 13.04 and I cannot get Deluge to work with UDP trackers / torrents using proxies. It works fine on Windows and on Debian Linux but it won't work on Ubuntu. The only torrent program on Ubuntu 13.04 that will work is Utorrent Server or Vuze.

I think I have narrowed it down to a problem with libtorrent-rasterbar because Vuze and Utorrent Server work perfectly but torrent clients like Deluge and Qbittorrent do not work. It seems to not work at all with UDP trackers and that's the problem. I use proxies from torguard and their support also says it's a problem with libtorrent-rasterbar.

On Debian Sid (and Wheezy), Deluge with my SOCKS5 proxy works PERFECT! Debian is using:

libtorrent-rasterbar6 (Version 0.15.10-1+b1)
deluge (Version 1.3.3-2+nmu1)
deluge-common
deluge-gtk

so is there any way I can use those debian packages on my Ubuntu 13.04 setup or downgrade those packages on Ubuntu? or is there another work around that I could do? I would really love to be able to get Deluge working with proxy support!

Thank you.

---

