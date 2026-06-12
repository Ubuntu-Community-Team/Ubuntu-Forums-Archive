---
title: "Motorola Rokr, Itunes and Linux"
date: 2006-12-17
forum: Desktop Environments
---

### Post by giruzz on 2006-12-17
Hi,

Using my ROKR+Itunes with linux,is one of the last three things that I have to fix to be completely happy with Ubuntu.

What I tried and what doesn't work:

1) I'm actually using the libgpod-0.4.0.tar.gz that I download and compiled from their original website because the 0.3.2 lib included with Ubuntu aren't working with a Rokr mobile phone. Anyway, my mobile is seen as Ipod and this is working fine...(now it can be only used as kind of usb-key)

2) I tried: 
[LIST]
[*]Amarok: it doesn't detect my ipod. I think because it is looking in the wrong place for my Itunes database which is here /media/ipod/iTunes/iTunes_Control/iTunes (tried with the last version 1.4.4)
[*]GtkPod: it sees my Ipod, but it crashes and if it doesn't crash it seems to work but it doesn't update my Rokr database. (In other words, I can create playlists, upload or delete songs but when I unplug the Rokr...those songs don't show up in Itunes)
[*]YamiPod: it offers me to choose between two Rokr mobiles but when I choose one of the two crashes with a <check exception, quitting> error
[*]Floola: same as GtkPod, seems to work but when I'm opening my Rokr no songs in there...(at least it doesn't crash every 2 min)
[/LIST]

3) Each time I tried I first formatted the card, then I connected the Ipod to a WinXP-Itunes to upload at least 1 song and create a database. After that I just simply tried without anything on the card after a fresh format...

any suggestions? This really sucks...it is the most important problem I'm having with Linux at the moment...

thanksss

g.

---

### Post by iamhugeinjapan on 2006-12-18
What happens with Rhythmbox?

---

### Post by giruzz on 2006-12-18
> **iamhugeinjapan said:**
> What happens with Rhythmbox?

I'm using Kubuntu...can I use Rhythmbox?

g.

---

### Post by iamhugeinjapan on 2006-12-18
Yes you can. It will install some GTK libs with it but that's okay because you probably already have them for GTKPod ;)

---

### Post by 3rdalbum on 2006-12-18
Rhythmbox doesn't let you transfer songs to an iPod yet.

Apparantly, although iTunes can run in Wine, it can't load songs onto an iPod. Crossover Linux might work.

---

### Post by iamhugeinjapan on 2006-12-18
Rhythmbox (0.9.6) does let you transfer files to an iPod. I do it myself.  Select the song(s) in the library and drag them to the iPod device in the sources panel.

---

