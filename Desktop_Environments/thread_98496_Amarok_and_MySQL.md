---
title: "Amarok and MySQL????"
date: 2005-12-03
forum: Desktop Environments
---

### Post by sammyguy193 on 2005-12-03
First off, breezy rocks! I have never, and I mean never seen such a combination of usability, robustness, and stability in a linux computer. That said, I need help setting up a mySQL server to use with amrok. I was told on the forums that it was substantially faster than SQLite, and for an mp3 collection of >10000, amarok needs all the help it can get. Anyone know of any How-tos? I am totally new to mySQL, so dont count on my understanding anything too complicated....

Cheers & thanks!!!

Sam :smile:

---

### Post by INMCM on 2005-12-04
I did the following which seems to work fine and dandy. If anyone out there has a better way, please post.

First:
```
sudo apt-get install mysql-server
```

Select localhost or whatever at the little config screen that pops up.

Next, follow the instructions here: [http://amarok.kde.org/amarokwiki/index.php/MySQL_HowTo](http://amarok.kde.org/amarokwiki/index.php/MySQL_HowTo)

Skip right too 'MySQL setup' and make sure to put in real passwords if you cut and paste all the commands. You don't need to do any of the database conversion stuff unless you want to. I'll talk about that in a sec.

Now in Amarok, go to Settings --> Configure Amarok --> Collection

Change the Database type to MySQL and enter the database name (amarok), username (amarok), and your the password you set. Then click apply.

You'll need to rescan your collection unless you followed the Database Conversion stuff. I didn't care enough about the info Amarok complies to try and save it from SQLite. Now enjpy the much faster MySQL.

---

### Post by sanguinemoon on 2005-12-04
Does it really make that much difference, though? When I start Amarok, my collection comes up instantly and I too have 10,000 + MP3s? Or is this difference come in at some other function?

---

### Post by atoponce on 2005-12-04
[quote=sanguinemoon]Does it really make that much difference, though? When I start Amarok, my collection comes up instantly and I too have 10,000 + MP3s? Or is this difference come in at some other function?[/quote]

You won't notice the difference when just pulling up MP3 titles.  However, when you save ablum art, lyrics, ID3 tags, comments and other things, a collection that size will definitely utilize MySQL much better than SQLite.

---

### Post by sammyguy193 on 2005-12-06
Yup. BIG difference. Amarok is soooo much more responsive, especially when it comes to searching... SO much thanks! There should be a how o posted in the wiki for this... BIG help!

CHEERS!

sam

---

### Post by chemicalcomfort on 2007-04-20
thanks a million.  i didn't notice a huge performance jump when i switched it to mysql (8700+ music files), but it doesn't hang anymore on certain music files and it seemed to fix some of the bugs i was having.  (amarok 1.4.5) (ubuntu dapper)

---

