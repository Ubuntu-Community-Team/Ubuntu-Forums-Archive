---
title: "Encrypted DVDs"
date: 2005-11-29
forum: Desktop Environments
---

### Post by GrumpyBob on 2005-11-29
Ive been looking round the forums for clues on playing DVDs.  I've got my system playing commercial DVDs...sort of.

Starting Totem from the menu as a regular user works fine for some DVDS.  However some just throw a Totem error about being unable to play encrypted DVDs.  At this point I searched the forums some more, without finding the answer.

Just on the off chance, I started totem from the command line as sudo...and I find that it plays the encrypted DVDs just fine.

Is there some way to make the user-started Totem play these DVDs?

Robert

---

### Post by kosmic on 2005-11-29
Hum if you say you can read encrypted dvds with superuser powers I think you should already have installed libdvdcss ? if it is the case try to see the movies in VLC or Mplayer, is just an apt-get install away :)

---

### Post by GrumpyBob on 2005-11-29
Yep, I installed the codecs, libdvdcss etc as described at [http://help.ubuntu.com/starterguide/C/faqguide-all.html#sect-music-and-movies](http://help.ubuntu.com/starterguide/C/faqguide-all.html#sect-music-and-movies)

Just find it peculiar that some movies need Totem launched as superuser.  Presumably some of the files I installed are not readable by a normal user?

Robert

---

### Post by dafl00 on 2005-11-29
try
```
sudo chown : cdrom /dev/[hdwhatever ur cdrom is]

```

---

