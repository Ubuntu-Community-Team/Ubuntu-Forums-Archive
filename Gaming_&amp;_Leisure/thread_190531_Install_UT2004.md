---
title: "Install UT2004?"
date: 2006-06-06
forum: Gaming &amp; Leisure
---

### Post by Flashstar on 2006-06-06
I know that UT2004 is designed for Linux, and I have the DVD version, so I was wondering how to install it in Dapper? Thanks

---

### Post by goobers on 2006-06-06
For me, the script wouldn't work just by running it straight, so i'll tell you what i did.
try this:

open a terminal
type: 

sudo sh

then from the ut2004 dvd in the root folder, there should be a file called linux-installer.sh. drag it to the terminal window, then click on the terminal window and press enter.

hopefully the installer should then run.

i'd reccomend setting the install path to /home/(whatever your username is)/ut2004/ or something like that, cos you won't need to be a super user to run it.

I hope this helps :)

---

### Post by siorai on 2006-06-06
[QUOTE=goobers]For me, the script wouldn't work just by running it straight, so i'll tell you what i did.
try this:

open a terminal
type: 

sudo sh

then from the ut2004 dvd in the root folder, there should be a file called linux-installer.sh. drag it to the terminal window, then click on the terminal window and press enter.

hopefully the installer should then run.

i'd reccomend setting the install path to /home/(whatever your username is)/ut2004/ or something like that, cos you won't need to be a super user to run it.

I hope this helps :)[/QUOTE]

Even if you install to the default location (can't remember exactly what it is) you don't need to be a super user to run it.

---

### Post by goobers on 2006-06-06
thats wierd, cos it won't run for me unless its run as a super user...

---

### Post by =Kevin= on 2006-06-06
^It depends if you installed it in sudo or didn't.
If you installed it as sudo it's installed in /usr/local/games, if you installed without sudo it can be installed in for example /home/name/ut2004.

But I can still run ut2004 without sudo even when it's installed in /usr/local/games.... (just installed the game too and it works great :D)

-Kevin

---

### Post by goobers on 2006-06-06
oh well, haha, the instructions for installation should still stand, but just ignore my ramblings about installing in some crazy place :p

*runs off to play ut2004*

---

### Post by Flashstar on 2006-06-06
Thanks for the replies, and I got it installed with sudo, but when I try to run it the UT2004 logo appears, then disappears quickly. I guess I will try to update it but I first need to discover how to do that lol. :D

---

### Post by goobers on 2006-06-06
yeah, thats what happened with me, i had to run it under sudo to make it work. try that perhaps?

in a terminal window, try typing:

sudo /usr/local/games/ut2004//ut2004

---

### Post by Flashstar on 2006-06-06
Thanks that seemed to work. :) So I won't have to type this in over and over if I just install it as a regular user not root?

---

### Post by goobers on 2006-06-06
yeah, but what i did was just change the link in the menu to have sudo in front of it, cos i'm feeling too lazy to reinstall it at the moment :p

---

### Post by Flashstar on 2006-06-06
*Error*

---

### Post by Flashstar on 2006-06-06
How do you do that? Also, I saved the ece map pack to my user folder and now I can't copy it to the folder where I have UT2004 installed because it says I don't have permissions. How do I copy it? Sorry about the trouble. Thanks

---

### Post by goobers on 2006-06-06
lol, you can't copy it cos you need to be a superuser :P you could either reinstall ut2004 as a regular user (i reccomend this- sorry about making you do it this stupid way :P) or copy the file with the file browser with su permissions:
type  "sudo nautilus" in a terminal to do this

sorry again :D

---

### Post by Zeppfan on 2010-05-16
I tried to install UT2004 in terminal and this is what I got...

patrick@patrick-desktop:~$ sudo sh
[sudo] password for patrick: 
# '/media/UT2004_DVD/linux-installer.sh' 
sh: /media/UT2004_DVD/linux-installer.sh: Permission denied
# 


Help!?! I'm VERY new to Linux and appreciate any help. Thanks.
I'm running Ubuntu 10.04 LTS, btw.

---

