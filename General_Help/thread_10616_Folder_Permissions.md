---
title: "Folder Permissions"
date: 2005-01-09
forum: General Help
---

### Post by Dayson on 2005-01-09
Okay so I'm very new to linux, in fact I installed it yesterday, but I figured out how to mount my usb hard drive then move my mp3's to my internal linux drive.  Okay thats all fine and dandy but I cant access them because I dont have root permission (I put them in a folder in my home dir) so I did sudo nautilus and added permission but then all the subfolders and files arent changed just the top one.  So in short I dont want to have to change over five thousand files/folders so can someone help me out and tell me what I can do to speed this up please? Thanks for reading this!

---

### Post by fng on 2005-01-09
go to the root-folder of your mp3 collection.
```
$ sudo chown -R your_username:your_username *
$ sudo chmod 644 -R *
```

---

### Post by Dayson on 2005-01-09
Okay thanks a ton man that worked, but now it wont let me open any of the files themselves.  When I click on them nothing happens at all, when I right click on them I cant do everything its all dimmed.  What does this mean?

---

