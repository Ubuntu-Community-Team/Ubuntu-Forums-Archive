---
title: "Streaming radio: can you please check if this website works for you?"
date: 2006-02-20
forum: Desktop Environments
---

### Post by megamania on 2006-02-20
Whenever I try to listen to this radio, firefox crashes and ALL windows are closed. The MediaPlayer Connectivity extension is installed.

If you want to check if it works with your computer, please go to 

[http://www.capital.it](http://www.capital.it)

and click on the "accendi la radio" (turn on the radio) button right below the Radio Capital logo.

Any feedback/suggestion will be much appreciated.

---

### Post by knalle on 2006-02-20
"Ascolta con Realplayer"

aye demonos!

---

### Post by megamania on 2006-02-20
[QUOTE=knalle]"Ascolta con Realplayer"

aye demonos![/QUOTE]
does that mean it works for you? It doesn't for me. :( 

Firefox (1.0.7) usually crashes when I click on "ascolta con Realplayer", but sometimes it doesn't even make to it, and crashes when I click on the "turn the radio on" button on the main page.

What can i try to fix it?

---

### Post by kaamos on 2006-02-20
I can listen to it using ff 1.5. It starts playing in mplayer-plugin.

Bologna.. Spent two nights there last summer. In the trainstation waiting hall. :D (Interrail)

---

### Post by megamania on 2006-02-20
[QUOTE=kaamos]I can listen to it using ff 1.5. It starts playing in mplayer-plugin.
[/QUOTE]
hmmm... so, anybody with Firefox 1.0.x out there? Just to see if it's the program that has to be updated, or a different issue with my computer/o.s.

[QUOTE=kaamos]
Bologna.. Spent two nights there last summer. In the trainstation waiting hall. :D (Interrail)[/QUOTE]
TWO nights in the waiting hall? Why didn't you give me a phone call?  I'm a committed traveller and would have been happy to host you.  ;-)

---

### Post by pataphysician on 2006-02-20
1.0.7 and it works for me. looks like you need both flash and the mplayer plugin working for this.

---

### Post by hajk on 2006-02-21
Both RealPlayer and MPlayerplug-in work fine for me with the standard FF 1.0.7, the sites is loading rather slow though.

---

### Post by megamania on 2006-02-21
[QUOTE=hajk]Both RealPlayer and MPlayerplug-in work fine for me with the standard FF 1.0.7, the sites is loading rather slow though.[/QUOTE]

So it's definitely something with my setup. I'll check when I'm home, but at the moment I have no idea what to try...

Thank you all for now!

---

### Post by hajk on 2006-02-21
My setup for MPlayer:

1. packages mplayer-586 and mozilla-mplayer from Breezy repositories.
2. changed video driver from vo=x11 to vo=xv, and audio driver from ao=alsa to ao=esd in /etc/mplayer/mplayer.conf.
3. installed w32codecs from "deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) etch main"
(though I don't know whether MPlayer needs this).

Just my €0.02 worth...

---

### Post by megamania on 2006-02-21
[QUOTE=hajk]1. packages mplayer-586 and mozilla-mplayer from Breezy repositories.
[/QUOTE]
I had these installed already.

[QUOTE=hajk]
2. changed video driver from vo=x11 to vo=xv, and audio driver from ao=alsa to ao=esd in /etc/mplayer/mplayer.conf.
[/QUOTE]
This helped apparently, as now I can listen to the radio with the mediaplayer. :-)

[QUOTE=hajk]
3. installed w32codecs from "deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) etch main"
[/QUOTE]
I think the correct url is:
[ftp://ftp.nerim.net/debian-marillat/dists/etch/main/](ftp://ftp.nerim.net/debian-marillat/dists/etch/main/)      (pointing this out just for the records :-))

I re-installed the real player, which wasn't installed correctly, but firefox still crashes badly when trying to use it...

Anyway, thanks to the help from you all, I managed to solve my problem, or at least 50% of it. Still curious about why the realplayer streaming crashes firefox though...

---

### Post by hajk on 2006-02-21
Use the "deb ftp://ftp.neri...." line temporarily in /etc/apt/sources.list, then after "sudo apt-get update" pull in the w32codecs package in Synaptic. Afterwards, remove the "deb ftp://ftp.neri..." line again, and run "sudo apt-get update" once more. Downloading directly from that ftp-site is not the Ubuntu/Debian way..., but hey, it's up to you!

---

### Post by megamania on 2006-02-21
[QUOTE=hajk]Use the "deb ftp://ftp.neri...." line temporarily in /etc/apt/sources.list, [..]
Downloading directly from that ftp-site is not the Ubuntu/Debian way..., but hey, it's up to you![/QUOTE]
I understand. I had not downloaded those files, I stopped when I reached that ftp page.

I'll do the way you suggested. Thanks again!

---

