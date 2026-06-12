---
title: "Complete  beginner On the rainslick precipice of Darkness installation problems"
date: 2008-07-12
forum: Gaming &amp; Leisure
---

### Post by Kayza on 2008-07-12
Greetings to all,

Recently I have burned windows at the stake and went all out for Ubuntu, which I find to be great. But now I would like to install some things once in a while, one of those being, On the rainslick precipice of Darkness by Penny Arcade. I have downloaded the demo, and that is about as far as I can get. It took me two days of reading through posts just to figure out I had a terminal. I have tried a variety of commands, tar, sudo and whatnot. But in the end, I am completely lost. So I wonder if there is a good soul out there who could help me going, I would really appreciate it. Keep in mind I'm probably not going to understand what you are saying. I'm already glad I found the terminal, even though I still can't 

Thanks a million in advance.

---

### Post by gaminggeek on 2008-07-13
Have you managed to get the game out of the tar file? 
If your running ubuntu go to where you have the file and right click on it and go extract here

---

### Post by acoustibop on 2008-07-14
Be careful, Kayza!  Unlike most application packages made for Linux, the OTRPOD one does not decompress to a folder: you should create one first (best place is probably in your home folder) and extract the package to that.  Then just cd into the folder and do ./RainSlickEp1

You need to start the game from this script rather than the executable (RainSlickEp1_bin) itself as the script calls a couple of library files that come with the game - it won't work without them.

**Edit:** forget that warning - they're now packaging the current demo so it unpacks to its own folder.  Should be Ok.

---

### Post by anotherconfused1 on 2008-07-16
I was able to run the game after I extracted it, jsut double click RainSlickEp1 not RainSlickEp1_bin to start the game. Have fun with the game, I liked it and bought it too.

---

