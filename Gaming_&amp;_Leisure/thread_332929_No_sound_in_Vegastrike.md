---
title: "No sound in Vegastrike"
date: 2007-01-06
forum: Gaming &amp; Leisure
---

### Post by tjb891 on 2007-01-06
I installed vegastrike and the music server through the repositories and the only sound i get is music with no voices or weapons sound or engine noices. Does anyone know how to fix this?

---

### Post by NiksaVel on 2007-04-07
I don't, but I got EXACTLY the same problem

---

### Post by dulbirakan on 2007-08-24
I also have the same problem with the version in repos.

When I install it from projects own site I have sound but this time my joystick stops functioning.

There is more information here:
[http://ubuntuforums.org/archive/index.php/t-403885.html]("http://ubuntuforums.org/archive/index.php/t-403885.html")

---

### Post by NiksaVel on 2007-08-24
yeah same here....  it's either joystick or sound...    and I need both to have a pleasant gaming experience...   it's a shame because the game really looks fun...

---

### Post by pwerner2 on 2009-10-25
I haven't had any sound at all with the latest version, but I also have something of a quick-fix. Pull up a terminal and search for the vegastrike music files (make sure you've installed the vegastrike-music package -- you won't need anymore it after you copy the files); you can do this with something like: 

du | grep -F vegastrike

Move the .ogg files to a separate folder, then you can just drop into a tty and say something like mplayer ~/music/vegastrike-music/* -shuffle -loop 25, go back to x, and play vegastrike with its own music, or whatever music you want, for that matter. You need to start the music before you start the game, though. Works for me, should work for you, too.

---

### Post by pwerner2 on 2009-10-25
But yeah, tjb891, I'm pretty sure vegastrike has only music, not sound effects or voice. I could be wrong. I've used several versions of it, though I've only had issues with the latest one.

---

