---
title: "[SOLVED] MPD/Sonata: I Don't Get It."
date: 2008-12-11
forum: General Help
---

### Post by Mark76 on 2008-12-11
What's the point of a music player that can't see your files?

---

### Post by Mark76 on 2008-12-11
Why doesn't it work?

What the hell else am I supposed to install?

---

### Post by Nepherte on 2008-12-11
You will have to be a little more specific about your problem. You could start with provding your mpd configuration file.

---

### Post by Ecclesia on 2008-12-11
I'm having a hard time getting Sonata to work, but I'm using mpd on a remote machine.

I read somewhere that you had to update both the music folder in your mpd.conf file as well as in the preferences for Sonata.  This might be the fix you're looking for.

Have you verified that mpd is working and that you have a working database? You do this by editing your mpd.conf to show your music folder and then

```
mpd --create-db
``` 

after this you may have to restart your mpd
```
/etc/init.d/mpd restart
```

I wouldn't be using mpd except to remotely control my music from other machines.  It works amazingly for controlling a little server that stores my music (old laptop with dead screen - sits on top of stereo).  As just a music player I prefer Rhythmbox, Songbird, or Amarok.

Good luck.

---

### Post by Mark76 on 2008-12-11
It's too hard. I can't be bothered

Problem solved

---

