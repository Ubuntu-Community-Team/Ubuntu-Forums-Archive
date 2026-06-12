---
title: "what media player R U using?"
date: 2007-09-07
forum: Dell  Ubuntu Support
---

### Post by newtimes on 2007-09-07
I have an XPS m1210 running fiesty but when I try to play any media(mp3,video,wav,etc.) it trys to start then disapears.

---

### Post by gbrainin on 2007-09-07
MP3, at least, is considered a "restricted format."  You need to get the appropriate codecs for the formats you want to play.  See:

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by neptho on 2007-09-07
> **newtimes said:**
> I have an XPS m1210 running fiesty but when I try to play any media(mp3,video,wav,etc.) it trys to start then disapears.

ATI videocard?  The current ATI drivers, to be blunt, suck.  They puke with multiple XV attempts.  Set the output for video to SDL or GL.

Try running from the command line to see if it works, or crashes:

```
%xine -V opengl (or sdl)
```

If this works, set your configuration in ~/.xine/config.

I used GNOME, but I've been seduced by KDE.  I use Codeine and Amarok.  Everything just works.  Everything.  :)

---

### Post by strabes on 2007-09-08
```
sudo aptitude install ubuntu-restricted-extras
```

---

### Post by kuja on 2007-09-08
> what media player R U using?
Amarok (audio), Kaffeine (video)

---

### Post by deeminter on 2007-09-09
Amarok for music and radio.
VLC for video play back and movies.

Dee Minter

---

