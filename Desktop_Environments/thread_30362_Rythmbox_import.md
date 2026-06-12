---
title: "Rythmbox import"
date: 2005-04-28
forum: Desktop Environments
---

### Post by psoulocybe on 2005-04-28
A64 rythmbox is only importing partials of my folder structures.

I try to add /Tunes/ which contains my music, and it only imports about 30 tracks of the 10 gigs or so of music.

Any reason it might be doing this?

---

### Post by duff on 2005-04-28
Usually a bad MP3, or some non-audio file.  The only thing you can really do about it is to run rhythmbox with the `-d` flag from the terminal, import the directory, and see which file is screwing it up.  Then move it, and try again.  And you can submit a bug report (along with the problematic file) to the rhythmbox guys, and they'll fix it or send it upstream to the gstreamer devs.

---

### Post by GTKpower on 2005-04-28
Rhythmbox is a nice music-manager app - it aint no amaroK, but I'm sure one day we'll have an amaroK version for GNOME.

Anyway, Rhythmbox can't read certain mp3 files.  It's rare (I have a huge collection and it failed to read only ONE file), but you can always convert that mp3 to .ogg using an app like Audaciy (in the repos.)

---

### Post by psoulocybe on 2005-04-28
can you say apt-get remove --purge rythmbox

XMMX it is

---

