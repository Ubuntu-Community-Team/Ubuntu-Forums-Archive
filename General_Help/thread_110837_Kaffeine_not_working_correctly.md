---
title: "Kaffeine not working correctly"
date: 2005-12-31
forum: General Help
---

### Post by Kobra on 2005-12-31
Ok, whenever I try to run Kaffeine, it gives me this mumbo jumbo:
```
Kaffeine Part...
Part not found. Please check your installation!
KDE...
Found version: 3.4.3
Ok.
xine-lib...
Found version: 1.0.1
Ok.WIN32 Codecs...
Ok.
libdvdcss...
Ok.
DVD Drive...
DMA mode off! For smooth DVD playback run as root: "hdparm -d1 /dev/dvd".
DVB-Device...
No DVB-Devices found. The DVB related functions will be hidden.
Distribution...
Ok.
RESULT: Found some problems, but nevertheless Kaffeine may work.


```
Could anyone help me out here?  All I wanna do is just play some videos and my DVD's.  I use Kaffeine because it has DVD Menu support

---

### Post by briancurtin on 2005-12-31
turn DMA mode on. this can be done several ways, the easiest being through the automatix script

i used kaffeine a while back and the only thing that came up was the one about DVB-devices. i dont have one, dont know what one is, and dont want one, yet every time i opened kaffeine it would display that. it got too annoying so i canned it and used other stuff

---

### Post by Kobra on 2006-01-01
Well, could you suggest another player with DVD Menu support?

---

### Post by iand675@gmail.com on 2006-01-01
I'm not positive, but I believe that mplayer can do dvds.

---

### Post by piq on 2006-01-01
I've tried to play three rental dvd's in vlc, totem, ogle, okle, xmms and it hasn't worked once. Any idea why?

---

### Post by zoiks on 2006-01-01
[QUOTE=piq]I've tried to play three rental dvd's in vlc, totem, ogle, okle, xmms and it hasn't worked once. Any idea why?[/QUOTE]

Possibly because you haven't installed libdvdcss.  It "decrypts" DVDs so they can be played on Linux.  Not sure which repo it's in, but note that this software may be illegal in the United States under the DMCA.

---

### Post by Kobra on 2006-01-02
MPlayer does DVD's, I'm sure of that.  But it doesn't have DVD Menu support.  For me, it's practically impossible to watch a DVD through that because I have to search through the titles to find what I'm looking for, which is wayyy too much work for me

---

