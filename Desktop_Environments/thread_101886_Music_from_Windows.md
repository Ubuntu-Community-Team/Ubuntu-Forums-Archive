---
title: "Music from Windows"
date: 2005-12-10
forum: Desktop Environments
---

### Post by jørgen on 2005-12-10
I have managed to share files between my Ubuntu and my XP computer. But i cant figure out how to get the music into the Rhytmbox music library. (Playing it from the other computer, not just copying the files to Ubuntu)

Does enyone know how i can do that?

---

### Post by justinjstark on 2005-12-10
[QUOTE=jørgen]I have managed to share files between my Ubuntu and my XP computer. But i cant figure out how to get the music into the Rhytmbox music library. (Playing it from the other computer, not just copying the files to Ubuntu)

Does enyone know how i can do that?[/QUOTE]

You should be able to mount a network location somehow and then be able to import your music from the mount point.  I know I have done similar things in the past but not recently.  Try google.  Can anybody else help?

---

### Post by antiemptyv on 2005-12-10
When I first moved music over to my Ubuntu computer, Rhythmbox couldn't read it, but that was because I had not yet installed MP3 support for it yet.  Maybe that's the problem you're having?

---

### Post by justinjstark on 2005-12-10
I think this is what you want:

[http://www.linuxplanet.com/linuxplanet/tutorials/2047/3/]("http://www.linuxplanet.com/linuxplanet/tutorials/2047/3/")

---

### Post by doclivingston on 2005-12-10
[QUOTE=jørgen]I have managed to share files between my Ubuntu and my XP computer. But i cant figure out how to get the music into the Rhytmbox music library. (Playing it from the other computer, not just copying the files to Ubuntu)
[/QUOTE]

Currently released versions of rhythmbox don't support *remote gnome-vfs*, which means that you will have to mount the share as described in the link blaksaga gave. Rhythmbox 0.9.3 (which isn't out yet) has support for remote gnome-vfs, so with that you will be able to use it like you do in Nautilus.

---

### Post by jørgen on 2005-12-11
I doesn't have a mp3 codec for it. How can i get one?

---

### Post by doclivingston on 2005-12-11
[https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)

---

