---
title: "How do I add songs to Frets on Fire?"
date: 2008-03-15
forum: Gaming &amp; Leisure
---

### Post by hyrule_man on 2008-03-15
I have all the GHI, GHII, GH Encore, and GHIII songs downloaded and working in Windows, they're stored on my 320GB HDD. Now where do I place those song files in Ubuntu for them to work..? Same for mods. Where do they go? Thanks in advance. OSs are XP Pro and Linux Mint Daryna.

---

### Post by hyrule_man on 2008-03-15
...Bump...

---

### Post by NJHokie on 2008-03-18
they go in the same place they go for the windows version, in the /FretsOnFire/data/songs folder.

the mods are different.  windows mods don't necessarily work with linux.  i think the only one that was ported was the RF mod which has a specific version for linux that matches your FoF version.

---

### Post by movesandpepper on 2008-07-08
hey, this isn't marked solved so I figured I might explain a little further. NJhokie is right they go in the same folder they would in windows, and that folder's full path would be 

/usr/share/games/fretsonfire/data/songs

you will have to open your file browser as root in order to add files to it though. after adding songs to that folder, you should be able to open FOF and see them.

---

### Post by drascus on 2009-07-11
thank you so much movesandpepper I had been really annoyed with FOF for a while because I couldn't figure out how to add more songs now I am filling up my folders with the good stuff!!!

---

### Post by ajack38 on 2009-12-05
uh yea im running jaunty jackalope and it wont allow me to do anything with the folder so i was wondering how to get root permission for that folder?

---

### Post by aspartam on 2009-12-16
sudo chmod 777 -R /usr/share/games/fretsonfire/data/songs/

---

### Post by ElighCS on 2010-09-26
Every time I add a song (Ubuntu 10.04) I get error no13 I can't seem to find what causes this please help.

---

### Post by ElighCS on 2010-09-26
Nevermind I used nautilus as root to copy the songs in and the permission was set to root so I kept getting error 13. It worked once I set myself as owner.

---

