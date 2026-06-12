---
title: "Qtorrent and ports?"
date: 2006-03-10
forum: Desktop Environments
---

### Post by Biffy on 2006-03-10
I know this has been posted before but i can't solve the problem.

So i want a lightweight torrent. I am used to Azureus, wich is a good client, but it's so damn slow.

So qtorrent looks nice. But there are no options to change ports. There only are "Torrent" and "Help" to click on, nothing else. Can i change ports in this client?

---

### Post by renzokuken on 2006-03-10
never even heard of qtorrent....

u should try bittornado (available in Automatix), lightweight and you can def configure your own ports

---

### Post by KnottyMan on 2006-03-11
Also try updating java.  Had same slowness with Az.  After updating java, much better.

---

### Post by twigboy on 2006-03-11
If its open source you can modify the source for which port you want.  Im on a windows machine right now so I cant take a look at it.

---

### Post by Killgore on 2006-03-11
Try looking for the configuration files for it. Also the screenshots show a connection tab so if you havnt looked there yet that might be a start.

---

### Post by hamil on 2006-05-06
For Qtorrent3, I found this solution:

I found a file called: defaultargs.py in the folder: /usr/lib/python2.4/site-packages/pyqtorrent3/BitTorrent/

I opened that file wit sudo gedit, and found some lines with some nice info:
```
    ('forwarded_port', 0,
        "world-visible port number if it's different from the one the client "
        "listens on locally"),
    ('minport', 6881, 'minimum port to listen on, counts up if unavailable'),
    ('maxport', 6991, 'maximum port to listen on'),

```
I edited this to my preference, and it seems like it is working fine with it... :)

Hope that this might help you?

Lasse

---

