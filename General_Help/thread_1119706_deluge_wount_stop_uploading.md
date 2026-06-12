---
title: "deluge wount stop uploading"
date: 2009-04-08
forum: General Help
---

### Post by markg48 on 2009-04-08
ive set    deluge not to upload data but its still uploading  :S plz help...

---

### Post by kpkeerthi on 2009-04-08
You should upload atleast while the torrent is still downloading. Otherwise, your download speed will start to crawl soon.

---

### Post by lovinglinux on 2009-04-08
Could you be more specific about which option you choose to prevent the upload?

Would be nice to know Deluge's version and if you are referring to completed downloads or active downloads.

---

### Post by markg48 on 2009-04-11
i set upload rate to zero because i have limited connection and data usage but   it say uploaded 300 mb of     data  for a 700 meg file so i end up using 1 gig -.- delug still uploading tho

---

### Post by Vaphell on 2009-04-11
hmm, in your connection both upload and download count? that truly sucks, you probably should find another way to dl movies :-) How high is your real upload?

Sidenote: you probably can minimize uploading to minimum but it's not nice from a philosophical point of view. Peer2peer networks are about exchanging data between peers, so you have to upload - not that you HAVE TO, but it wouldn't work if everyone was only leeching. Someone has to upload to allow another guy to download.

---

### Post by lovinglinux on 2009-04-11
I'm not sure you can really set the upload limit to zero. I don't think that feature was designed with that intention. Nevertheless, it could be a bug in the feature itself or in the display of amount of data uploaded. Have you checked your ISP history to see if you really used the bandwidth? 

You should report this in the [Deluge's forum](http://forum.deluge-torrent.org/), so you can get feedback from the developers.

> **Vaphell said:**
> Sidenote: you probably can minimize uploading to minimum but it's not nice from a philosophical point of view. Peer2peer networks are about exchanging data between peers, so you have to upload - not that you HAVE TO, but it wouldn't work if everyone was only leeching. Someone has to upload to allow another guy to download.

+1

Additionally, if you set your upload rate too low you won't get high download speeds, because the most you give, the most you get.

You should consider subscribing to a broadband service without bandwidth limit. If you can't, then you will have to live with it and slow down your downloading habits.

---

### Post by fr0g on 2009-09-08
You could also just set Deluge's upload to 1 kb/s..and yes there is a bug in the program where you cannot enter 0 for the limited upload rate..however, it seems to get higher download rates if you set upload at unlimited, a way to keep the torrents well seeded i suppose.

---

