---
title: "Freespace 2"
date: 2007-11-18
forum: Gaming &amp; Leisure
---

### Post by MikeSz on 2007-11-18
Been browsing round the net and have come across Freespace 2.  According to their website, there is a Linux version so I am assuming that it is now open source and free etc (if not I apologise profusely) 

I have a .run file which is about 4mb called freespace2-1.20-x86.run which is an installer - unfortunately I have no idea what to do with it.  

Does anyone know how one would get this game working on 7.10?  A .deb file by any chance?

Any help appreciated...

---

### Post by misfitpierce on 2007-11-18
put in home folder and open terminal

sudo sh FREESPACEFILENAME.run

should run

---

### Post by hikaricore on 2007-11-18
[http://ubuntuforums.org/showthread.php?t=528880&highlight=freespace](http://ubuntuforums.org/showthread.php?t=528880&highlight=freespace)
[http://ubuntuforums.org/showpost.php?p=2831809&postcount=3](http://ubuntuforums.org/showpost.php?p=2831809&postcount=3)
[http://www.hard-light.net/wiki/index.php/Fs2_open_on_Linux](http://www.hard-light.net/wiki/index.php/Fs2_open_on_Linux)

---

### Post by MikeSz on 2007-11-18
hmmm - got this.....

zer0cool@zer0cool:~/Desktop$ sudo sh freespace2-1.20-x86.run
[sudo] password for zer0cool:
Verifying archive integrity... All good.
Uncompressing Freespace 2 for Linux.....................................................................................
/home/zer0cool/.setup7699: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory

Had a look at the links - thanks for those, some bedtime reading I think!  I promise i will educate myself but at the moment I just want to see if I can make it work in a quick and painless way, lol.

---

### Post by daengbo on 2007-11-18
You need to install [libgtk1.2]("apt:libgtk1.2"). Click my link to do so.

---

### Post by MikeSz on 2007-11-19
thanks v.much for the link - appreciated.  I have looked through synaptic and noticed that I have version 2.0 installed (see screenshot) although the description is different.  

I take it I can just check the box to install version 1.2 and it will run along side version 2.0 or am I worrying over nothing?

---

### Post by Vadi on 2007-11-19
Yeah, that game wants gtk 1.2, so install it too - you'll be okay, they'll both cope together well.

---

### Post by MikeSz on 2007-11-20
unfortunately it doesnt seem to work!  Im assuming this is now an open source game but the installer is asking me for the CD (which obviously I dont have)

screenshot attached - any ideas or is this the end of the line for freespace for me?

---

### Post by Vadi on 2007-11-20
I'd say someone might actually be offended by your assumption that open source has a price of $0. It certainly doesn't cost that to develop it.

As for the thing, I found this link ([click]("http://www.hard-light.net/wiki/index.php/Freespace_2_EULA_Issues")), looks like the company went out of business, and the game is now, well, "free". As I understand, there's nobody to sue you.

Google tells me you can download it here - [http://liberatedgames.com/game.php?game_id=8](http://liberatedgames.com/game.php?game_id=8).

---

### Post by Vadi on 2007-11-20
Another linky: [http://icculus.org/freespace2/index.php](http://icculus.org/freespace2/index.php)

---

### Post by MikeSz on 2007-11-20
Cheers for the links - just to clarify, im only being careful which games I use on Ubuntu - I buy all of my games that I play in Windows and dont use anything that isnt 100% above board.

Didnt want to download or use a game which isnt open source or free to download - you can get lost very easily looking for games on the net for linux!

---

### Post by MikeSz on 2007-11-20
unfortunately, none of those links will let me download and run a linux version of the game.  One takes you to a site where you can get allsorts (except freespace from what I can tell) and the other one is for the demo.  Also they seem to be windows based.  

Does anyone have a linuz version of this game or am I on a road to nowhere?

---

### Post by hikaricore on 2007-11-20
You already have the Linux version of the game.

You just need the data files, which have been released for free by the original developer.

There are (or used to be) download links in the FAQ I gave you a link to.
Worse comes to worse you can track down a torrent for it as the game data is now public domain and legal.

---

### Post by MikeSz on 2007-11-20
Thanks Hikaricore - yes I did have a browse through the links you have me, I have to confess it all got a little confusing - think as im not used to games and Ubuntu I was sort of looking for a "please ckick me and all your problems will be solved" link :)

---

### Post by hikaricore on 2007-11-20
If I'm not mistaken the data files for FS2 consist of 3 ISO files which are about 650mb each.

Hopefully this makes things a little clearer.

---

