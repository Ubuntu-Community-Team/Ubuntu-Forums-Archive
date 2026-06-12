---
title: "Enemy territory from Playdeb seems to be broken"
date: 2014-08-02
forum: Gaming &amp; Leisure
---

### Post by mastablasta on 2014-08-02
```
http://archive.getdeb.net/ubuntu/pool/games/e/enemy-territory-data/enemy-territory-data_2.60b-1~getdeb1_all.deb
Connection failed


http://archive.getdeb.net/ubuntu/pool/games/e/enemy-territory/enemy-territory_2.60b+pb2.213-1~getdeb2_i386.deb
502  Proxy Error

```

while the first time i downloaded the package i got the broken package something about incomplete file (the data file is the problematic one). hmm shouldn't these be packages signed and checked on download?

---

### Post by mastablasta on 2014-08-03
managed to somehow reinstall. got the game working. but...

when connecting to server the messgae on server is

```
*user* unpure client detected. Invalid .pk files referenced.
```

where user is the one tryign to connect to windows XP server.

i just spent 3 hours (!) debugging searching for correct way to use this along with omnibot and their crappy linux instructions. leave it to Linux software to ruin your afternoon. and google, with it's crappy search engine finding 7 year old unreleted threads first. 

here is how it goes:
on windows: double click, "next, next, next....", extract omnibot, create shortcut, run game, profit.

linux: install, reinstall, delete all files, download, bad download again (broken package-why would you use a broken package if oyu knwo it's broken? remove it!). delete, download, install again. finally! connect to server. get kicked off. connect again. kicked off again. modify, troubleshoot, connect and get kicked off. move the files arround, check files and settings on server, troubleshoot some more. nothing. uninstall the thing, call an exorcist and invoke the purge command.

linux a viable gaming OS? yeah right...

---

### Post by mastablasta on 2014-08-04
have managed to solve it after another hour of searching. the problem was the game was pulling old bot file from server instead of using it's new file. 

the porblem to solve htis was Linux file system as it throws arround all the files in various folders all over the place. seriously something should be done about this. in Windows it was trivial to compare the games folders. all i needed to do was launch the tree command on client and server and print it to file. then compare the two files. in Linux files were all over the disk. something here, something there, something in usr, something in home. i finally managed to ifnd and psot the difference. deleting the offending older file  from server prevented it from being downloaded. and suddenly it Works.

---

