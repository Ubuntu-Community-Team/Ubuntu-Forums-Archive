---
title: "Extracting .zip file error - HELP! its a backup of my old computer!!!!!!!!!!"
date: 2010-06-24
forum: Desktop Environments
---

### Post by guyshoxton on 2010-06-24
[CENTER][SIZE="4"][FONT="Arial"]May some one please help me as fast as possible!? On my old ubuntu before i re installed it, i made a backup of all my files and my images and videos and compressed it and put it on my pendrive, but now after i tried extracting it on my re installed ubuntu machine (i use lucid - AKA ubuntu 10.04 LTS) it just gives me this error thing... [IMG]http://ipic.tk/s/mjm.png[/IMG] and i have a bunch of important files and images that are only in that zipped folder and i have no where else! and i am a web designer, my website files and images are all in that folder! its a total of 2GB the size of the folder, but it wasn't a problem compressing it, why is it extracting? because it was compressed as .zip on ubuntu 10.04 and i re installed ubuntu 10.04 and for some reason that pop up appears!!

PLEASE MAY SOME ONE HELP!!!!????:confused::confused::frown::frown:](*,)](*,)](*,)[/FONT][/SIZE][/CENTER]

P.S. this is what the error thing says: 


Archive:  /media/PENDRIVE/Documents.zip
Zip file size: 2147483647 bytes, number of entries: 36023

warning [/media/PENDRIVE/Documents.zip]:  end-of-central-directory record claims this
  is disk 32050 but that the central directory starts on disk 38692; this is a
  contradiction.  Attempting to process anyway.
error [/media/PENDRIVE/Documents.zip]:  missing 750403024 bytes in zipfile
  (attempting to process anyway)
error [/media/PENDRIVE/Documents.zip]:  start of central directory not found;
  zipfile corrupt.
  (please check that you have transferred or created the zipfile in the
  appropriate BINARY mode and that you have compiled UnZip properly)

---

### Post by Revolutionary101 on 2010-06-24
There are some big problems with this. Let me translate the error file for you and you might see what I am talking about.

> **guyshoxton said:**
> ]error [/media/PENDRIVE/Documents.zip]: missing 750403024 bytes in zipfile
(attempting to process anyway)

That means that you are missing you are missing 715.64 MB out of the 2047.99 MB zip file.

> **guyshoxton said:**
> warning [/media/PENDRIVE/Documents.zip]: end-of-central-directory record claims this
is disk 32050 but that the central directory starts on disk 38692; this is a
contradiction. Attempting to process anyway.

The computer is reading the zip file and it basically says that "The index starts before it ends". That just means that the index is corrupt.

> **guyshoxton said:**
> error [/media/PENDRIVE/Documents.zip]: start of central directory not found;
zipfile corrupt.
(please check that you have transferred or created the zipfile in the
appropriate BINARY mode and that you have compiled UnZip properly)

This is the last of the bad news. The computer doesn't know where the index of all the files start so thus it can't find the files inside the zip file.

I'm sorry to be the bearer of bad news but I doubt there is anything that can be done about this. (I may be wrong though)

---

### Post by perky on 2010-07-01
[This post]("http://ubuntuforums.org/showthread.php?t=789205") recommends WinRAR via wine or ```
zip -FF /media/PENDRIVE/Documents.zip
```

Also try google:  [linux]("http://www.google.com/search?hl=en&q=linux+fix+corrupted+zip+files") or [windows programs]("http://www.google.com/search?hl=en&q=fix+corrupted+zip+files") via wine.

You may be able to salvage some of your data back, good luck!

---

