---
title: "Gnome bittorrent ports"
date: 2005-03-29
forum: Desktop Environments
---

### Post by jeremy on 2005-03-29
Does anyone know if it possible to change the port(s) that gnome bittorrent uses?

---

### Post by vassie on 2005-04-15
[QUOTE=jeremy]Does anyone know if it possible to change the port(s) that gnome bittorrent uses?[/QUOTE]

I would like to know this too
Thanks
Ben

---

### Post by Tristan9669 on 2005-08-11
[QUOTE=vassie]I would like to know this too
Thanks
Ben[/QUOTE]
me three

---

### Post by yyagol on 2005-08-17
I am looking for a way to do so too for the DC++

---

### Post by thechitowncubs on 2005-10-03
me 5

---

### Post by SickTwist on 2005-11-28
I figured there would be a way to do this in the gconf editor but I didn't see anything listed for gnome-bt or gnome-btdownload.

I'm also curious to know if this can be done because I have two computers running Ubuntu on my LAN and I do not think that my firewall can forward the same range of ports to both computers. (If this is not the case please let me know.) I'd prefer to use GNOME BitTorrent if at all possible as I like its simplicity.

---

### Post by mike1138 on 2005-11-30
I'd like to know also. I've got BitTornado working, but I'd like to use Gnome BT instead.

---

### Post by Sureshot324 on 2006-01-19
I've found a way to do this from the command line though it is hardly ideal.  Instead of opening the torrent from your web page, save it to your hard drive.  Then type something like this:

btdownloadcurses --minport 1720 --maxport 1720 mytorrent.torrent

You may need write and/or execute permissions on the torrent file, or might even have to sudo that command.  You can see all the binaries for the bittorrent client by going

cd /usr/bin
ls -l|grep torrent

so maybe you can look up the man pages and find something better.

---

