---
title: "Making a list of all my mp3s"
date: 2009-04-27
forum: General Help
---

### Post by t0p on 2009-04-27
I've got a bunch of mp3s on my computer.  They are all in a number of subdirectories, contained in a directory called Music in my home directory (eg I have all the tracks from Amy Winehouse's album *Back to Black* in a directory ~/Music/Back to Black, and the tracks from the Arctic Monkeys album *Favourite Worst Nightmares* in a directory ~/Music/Favourite Worst Nightmares.)

I want to make a list of all my mp3s.  But I don't particularly want to sit here manually going through the file listings and typing it all into a textfile.  Can someone please enlighten me as to a simple way to automate this task?

---

### Post by mb_webguy on 2009-04-27
If you just want a list of the files, use the following command.```
find ~/Music -name "*.mp3" >> MyMusicListing.txt
```

---

### Post by t0p on 2009-04-27
It's okay, I've figured it out for myself.  The command

```
ls -R Music
```

will do it for me.

Thanks anyway, anyone who was going to help me!

---

### Post by Wiebelhaus on 2009-04-27
> **t0p said:**
> It's okay, I've figured it out for myself.  The command

```
ls -R Music
```

will do it for me.

Thanks anyway, anyone who was going to help me!

I was typing that!

---

