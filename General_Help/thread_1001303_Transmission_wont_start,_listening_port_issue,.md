---
title: "Transmission wont start, listening port issue,"
date: 2008-12-03
forum: General Help
---

### Post by Epidural on 2008-12-03
So, I thought I'd be smart and change my port to get past Bell's bittorrent limit for bandwidth. But... I don't know enough about this stuff, and I changed the port without thinking "Oh, my router needs the port open, too" and so on. 
The trouble I'm having is that as soon as I change the listening port to 21 from my original, Transmission shut down and the GUI won't load anymore. I tried opening it via the terminal, and it tells me:

open_listening_port(21): Permission denied
cannot open port 21

And then nothing happens, nothing opens, nothing comes up that lets me change the port back to the original. Is there a way to change the port via the terminal? Any help is greatly appreciated, but, I'll warn now, I'm a newbie to Ubuntu and to Linux in general. 

Thanks in advance.

---

### Post by iaculallad on 2008-12-03
That would be a mistake of configuring transmission to use port 21. Port 21 is reserved for FTP services thus you can't connect from it. And one thing more, of the permission denied issue, port 21 seems to be blocked by a firewall.
Try re-configuring your transmission to use port ranging from, say, 6881 to 6889. And be sure that those port are opened on your firewall machine.

---

### Post by Slim Odds on 2008-12-03
> **iaculallad said:**
> Try re-configuring your transmission to use port ranging from, say, 6881 to 6889. And be sure that those port are opened on your firewall machine.

And if you have a router, you'll need to forward those port to your computer.

---

### Post by josephellengar on 2008-12-03
> **Epidural said:**
> So, I thought I'd be smart and change my port to get past Bell's bittorrent limit for bandwidth. But... I don't know enough about this stuff, and I changed the port without thinking "Oh, my router needs the port open, too" and so on. 
The trouble I'm having is that as soon as I change the listening port to 21 from my original, Transmission shut down and the GUI won't load anymore. I tried opening it via the terminal, and it tells me:

open_listening_port(21): Permission denied
cannot open port 21

And then nothing happens, nothing opens, nothing comes up that lets me change the port back to the original. Is there a way to change the port via the terminal? Any help is greatly appreciated, but, I'll warn now, I'm a newbie to Ubuntu and to Linux in general. 

Thanks in advance.

I don't know much of anything about this, but I use deluge.  It allows you to randomize valid ports when you first start it to ports that ISPs won't monitor, and I've never had problems with it on any ISP, even public wireless connections.  I like that client.  It's really good and has a whole lot more options than does transmission.  Good luck!

---

### Post by adult swim on 2008-12-03
do isp's even monitor specific ports or do they just take  note when you are using alot of bandwidth, regardless of port number?

---

### Post by josephellengar on 2008-12-03
> **adult swim said:**
> do isp's even monitor specific ports or do they just take  note when you are using alot of bandwidth, regardless of port number?

I think that they monitor ports, specifically those that the torrent and other p2p is on by default.  I don't know if they monitor bandwidth usage, but I think that that alone would be difficult to find illegal activity.  I know that downloading KDE or gnome takes as much bandwidth as (or more than) a torrent, and that's certainly legal.

---

### Post by iaculallad on 2008-12-03
> **adult swim said:**
> do isp's even monitor specific ports or do they just take  note when you are using alot of bandwidth, regardless of port number?

Some ISP's monitor or even block ports (Usually, 6881-6889) that are commonly used by Torrent applications. The thing you can do to is to use/activate "Protocol Encryption" in your torrent app so as to bypass any port-filtering configured by your ISP.

---

### Post by adult swim on 2008-12-03
hmm i didnt know about the port monitoring.  it seems like a silly thing to do since the port can be changed so easily.

---

### Post by ofirp on 2009-01-04
> **Epidural said:**
> So, I thought I'd be smart and change my port to get past Bell's bittorrent limit for bandwidth. But... I don't know enough about this stuff, and I changed the port without thinking "Oh, my router needs the port open, too" and so on. 
The trouble I'm having is that as soon as I change the listening port to 21 from my original, Transmission shut down and the GUI won't load anymore. I tried opening it via the terminal, and it tells me:

open_listening_port(21): Permission denied
cannot open port 21

And then nothing happens, nothing opens, nothing comes up that lets me change the port back to the original. Is there a way to change the port via the terminal? Any help is greatly appreciated, but, I'll warn now, I'm a newbie to Ubuntu and to Linux in general. 

Thanks in advance.

Try starting Transmission using sudo:

sudo transmission

then change the port so you can start it as a regular user.

---

