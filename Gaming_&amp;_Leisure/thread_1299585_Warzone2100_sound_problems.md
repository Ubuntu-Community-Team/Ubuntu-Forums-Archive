---
title: "Warzone2100 sound problems"
date: 2009-10-24
forum: Gaming &amp; Leisure
---

### Post by tuahaa on 2009-10-24
I've had this problem in 9.04 (although it wasn't playable when I had Jaunty due to Intel card) and now I'm having it in 9.10. The problem is that all the sound in Warzone2100 is really stuffed up- it's all jumbled and muffled and lags. It sounds like screeching too. I started it through terminal and closed it again and this is what I got:
```

bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
```

I would really appreciate it if anybody can help me. It's been ages since I had to wait to play any real Linux games because 9.04 isn't very compatible with Intel cards and I don't have Windows anyhow.

Thanks guys

---

### Post by tuahaa on 2009-10-24
bump:(

---

### Post by Eddward on 2009-10-24
I don't know if you want to try this but there are directions at [http://idyllictux.wordpress.com/2009/04/21/ubuntu-904-jaunty-keeping-the-beast-pulseaudio-at-bay/](http://idyllictux.wordpress.com/2009/04/21/ubuntu-904-jaunty-keeping-the-beast-pulseaudio-at-bay/).  It worked for my with my sound problems.  (Mentioned in another thread that got no response.)  I have an emu10k, but the writer had an intel card and he had some special directions for them.  There a link there to a HowTo for intel cards.  The author has become my hero.  Good luck.

Edd

---

### Post by tuahaa on 2009-10-24
Didn't work for me. I have 9.10...

Seems like a PulseAudio problem then

EDIT: When I said I had an Intel card, I meant I had an Intel Graphics Card, that's why I couldn't play games in Jaunty

---

### Post by tuahaa on 2009-10-25
bump

---

### Post by delcypher on 2009-11-02
See my post here [http://ubuntuforums.org/showpost.php?p=8225093&postcount=3]("http://ubuntuforums.org/showpost.php?p=8225093&postcount=3")

---

### Post by bronquel on 2010-02-12
i had this issue just today, and the fix was this
```
sudo apt-get purge bluez-alsa
```
 i also learned that ctrl-alt-f1 will pull you out of a frozen game... you can login and kill the game
```
killall -9 warzone2100
```
and ctrl-alt-f7 to bring you back to ubuntu.  hope that helps out.

---

