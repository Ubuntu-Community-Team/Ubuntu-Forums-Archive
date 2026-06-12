---
title: "THE BEST way to torrent?"
date: 2009-01-27
forum: General Help
---

### Post by nintennuendo on 2009-01-27
Transmission?  uTorrent via wine?  azureus or vuze?  are there others?  

What about booting to a livecd and downloading to a hard drive and torrenting from that overnight or something?  

How do you guys torrent, if you do?

---

### Post by theApokalypsis on 2009-01-27
I use Deluge Torrent its worth checking out. I have also tried Transmission and QTorrent.

[http://deluge-torrent.org/]("http://deluge-torrent.org/")

Deluge is kind of like Utorrent in the windows world. and its very actively updated.

---

### Post by nintennuendo on 2009-01-27
I've only heard of deluge once, on lifehacker when it came out, then nothing more.  I might have to give it a try.

---

### Post by waxBall on 2009-01-27
+1 for this question from me!

Is Deluge the most similar to uTorrent for Linux?  I personally don't mind but if I were to recommend a novice Win user to switch, what would be the easiest switch?

---

### Post by Egi_Power on 2009-01-27
Hi there!

I'm using Transmission when I need it. It does the job well.

I also tried Deluge, it's very similar to &#956;Torrent.

I don't know about the LiveCD thing, but it might just work.

Best regards,

Egi_Power

---

### Post by mobilediesel on 2009-01-27
I use [rtorrent]("http://libtorrent.rakshasa.no/") and automate its use with [this]("http://techknack.net/torrent-management-system-with-rtorrent-and-bash/") guide. With the rtorrent config file and a bash script run by cron, you can: 
[LIST]
[*]Limit the number of torrents downloading at a time
[*]Move completed torrents to a different directory
[*]Take up very few resources compared to GUI-based torrent programs
[/LIST]

---

### Post by adamlau on 2009-01-28
aria2 Bash Aliases:

alias idx='aria2c --no-conf --show-files'
alias bit='aria2c --conf-path=${HOME}/.aria2/aria2.bit'
alias ver='aria2c --conf-path=${HOME}/.aria2/aria2.bit -V'

aria2 Configuration File:

seed-time=60
seed-ratio=10.0
check-certificate=false
dir=/files/Downloads
max-upload-limit=128K
bt-max-open-files=1

---

### Post by dhughes on 2009-01-28
I've heard rtorrent is good especially to automate things.

 Deluge is OK I tried it and have it installed, I may switch to it since it looks nice and is easy to use.

 Transmission had trouble when I was downloading a 60GB torrent, at one point Transmission just stopped, no error message, just stopped. Overall it's OK and I have used it a lot, the large torrent problem was the only problem I had with it.

---

### Post by syga on 2009-01-28
Deluge for torrents
GTK-Gnutella for p2p
Mobloquer for the linux version of Peerguardian

---

### Post by simtaalo on 2009-01-28
ktorrent is the fastest torrent client i've ever used by a big margin.

---

### Post by mb_webguy on 2009-01-28
I've tried Transmission, Azureus, uTorrent under Wine, and Deluge.  Deluge is my favorite by a wide margin.  I have heard favorable things about ktorrent, but I'm happy enough with Deluge that I haven't bothered to try it.

You should, however, install Deluge from the [Deluge website]("http://deluge-torrent.org/") rather than from the Ubuntu repositories.  The repositories are still using version 0.5.9, while the latest version on the Deluge website is 1.1.1.

---

### Post by elf_cleric on 2009-01-28
I am using Azureus and happy with it :)
I have tryed Tarnsmission as well but didn't like it because it was too slow and it was uploading more than downloading.

Cheers

---

### Post by glotz on 2009-01-28
Dpends quite a lot on your definition of 'best'.

Want a gorgeous looking app? A very responsive user interface? A boat load of features? High throuhgput?

---

### Post by kavon89 on 2009-01-28
> THE BEST way to torrent?

Legally

---

