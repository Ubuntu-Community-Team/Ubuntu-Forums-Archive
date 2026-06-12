---
title: "ACER Netbook help please"
date: 2012-09-16
forum: Desktop Environments
---

### Post by Softa on 2012-09-16
I have an Acer netbook running Unity. I have a folder on the desktop of my netbook called *usr*, with these folders: /home/keshet/Desktop/usr/bin  /home/keshet/Desktop/usr/lib /home/keshet/Desktop/usr/shar  Can I delete it, or is it something that I need?

If possible, please phrase your answers as if you were talking to your grandmother, because I probably am old enough to qualify.

Thank you

---

### Post by beboylips on 2012-09-17
Do those folders contain any files? If not, delete it.

---

### Post by mparillo on 2012-09-17
> **beboylips said:**
> Do those folders contain any files? If not, delete it.

But be careful.
Some file managers may hide certain 'system' files for you.
You may need to invoke an option to view hidden files or from a command line:

```
ls -alc
```

Apologies in advance if this is an insultingly elementary caution.

---

### Post by Softa on 2012-09-17
Sorry, I wasn't clear.  The folder contains these files: /home/keshet/Desktop/usr/bin  /home/keshet/Desktop/usr/lib  /home/keshet/Desktop/usr/shar

---

### Post by sideburns on 2012-09-17
What we're trying to find out is are there any files, or just folders inside folders inside folders?  (Rather like a set of nested Russian dolls.)  Keep opening the folders until you either find some files, or there arn't any you haven't looked into.

---

### Post by Softa on 2012-09-17
OK, there are folders inside.  The first is the bin, with a single file called flash-player-properties.  The second folder is lib, and there is a folder inside that says kde4.  The file inside kde4 is kcm_adobe_flash_player.so.  The last folder says share, and inside, there four folders...and they are...applications, icons, kde4, and pixmaps.

If you want to know the contents of these last folders, I'll be happy to let you know.

---

### Post by DogMatix on 2012-09-17
kcm_adobe_flash_player.so is a file. Quite what those folders are doing on your desktop I don't know. When did they appear?

---

### Post by Softa on 2012-09-17
> **DogMatix said:**
> kcm_adobe_flash_player.so is a file. Quite what those folders are doing on your desktop I don't know. When did they appear?
Not quite sure when they showed up.  I try not to have anything on the desktop except what I need for school, and when I was cleaning up, I realized it was there.

---

### Post by newb85 on 2012-09-17
Rename the top-level folder and leave it alone for a while to see what happens.  It's a non-permanent way of testing what would happen if you delete it.

(Just remember the original name in case you need to put it back.)

---

