---
title: "can't open avi from windows share in vlc remotely"
date: 2006-01-15
forum: Desktop Environments
---

### Post by salparadi on 2006-01-15
i'd like to be able to open avi files remotely from my windows box and play them automatically with vlc in ubuntu.  when i double click them it says "can't display location" and 

Couldn't display "smb://salparadi/Television/C...nivale.S01E05.DVDRip.XViD.avi".

i uninstalled totem the best i could but this is my first time using ubuntu and i'm not sure i did it correclty.  initially when i opened the files over the share it did automatically open totem but it wouldn't play the files.  i assumed if i uninstalled through the synaptic and installed vlc that it would automatically open that.

i have tried doing "properties / open with" and adding vlc as well as right clicking and hitting "open with application"

any ideas?  thank you very much

---

### Post by schilcha on 2006-01-16
Mount the windows-share, so you can access the file as any other file.
There's a document in the wiki describing the necessary steps: [https://wiki.ubuntu.com/MountWindowsSharesPermanently]("https://wiki.ubuntu.com/MountWindowsSharesPermanently")

Good Luck!

---

### Post by salparadi on 2006-01-16
thank you kindly that did the trick.  i'll look there from now on for stupid questions.  i appreciate the link though, perfect!!!

---

### Post by schilcha on 2006-01-16
... there are no stupid questions -- just stupid answers ...

You can look there, if you know what you're looking for. But! connecting to a windows-share the way you did seems perfectly right in the first place -- it's what the desktop offers. You have to know that there are other approaches as well (I learned it from another thread somewhere here...)

---

