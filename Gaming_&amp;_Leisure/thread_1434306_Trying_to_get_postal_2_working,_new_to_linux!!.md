---
title: "Trying to get postal 2 working, new to linux!!"
date: 2010-03-20
forum: Gaming &amp; Leisure
---

### Post by goofy00 on 2010-03-20
Hi, recently installed postal 2 fudgepack, and I've run into a problem. When I try to click on it and boot it up, a warning screen pops up but that is all. I'm fairly new to linux so if anyone could help me out that would be great. Thanks!!

---

### Post by ad_267 on 2010-03-20
What does the warning screen say?

---

### Post by goofy00 on 2010-03-20
Sorry its not like any error screen or anthing, its just the games disclaimer screen about violence and what not. But after it pops up and you think the game is about to boot.....nothing.

---

### Post by Sockerdrickan on 2010-03-20
Start it from a terminal and post the output here in a [code] tag

---

### Post by ad_267 on 2010-03-20
You can open a terminal from Applications -> Accessories -> Terminal. To find out what command to run, drag the entry for Postal 2 from your menu onto the desktop. Right click on it and select properties, then copy the command entry into the terminal.

---

### Post by goofy00 on 2010-03-20
umm the file is a postal2.sh . When I get into that folder  into the terminal using the cd command...and type postal2 ...I get the following

No command 'postal2' found, did you mean:
 Command 'postal' from package 'postal' (universe)
postal2: command not found

Also to [ad_267]("http://ubuntuforums.org/member.php?u=472577") I tried copying the file onto the desktop, and when i did , I clicked promperties, and saw its name postal2, and when it was created...but no command line....??

---

### Post by Perfect Storm on 2010-03-21
Try;
```
cd ~/Desktop
chmod +x postal2.sh
sudo sh postal2.sh
```

---

### Post by goofy00 on 2010-03-21
Okay after all the tips, and help I've gotten, I've managed to get it booted up with the terminal....still the same problem the games disclaimer comes up then no game...but I did get some errors come up on the terminal. 

Can't find 'ini:Engine.Engine.GameEngine' in configuration file

History: 

Exiting due to error

Hope this leads someone in the right direction!  Cause I don't know what to do with it lol. Thanks!

---

### Post by ELD on 2010-03-22
Where did you buy your copy from? Or are you trying to use the very outdated installer (which probably wont work) for the windows version to make it run under linux.

---

### Post by saturnoyo on 2011-04-12
Hello, I have problems with this game on linux (Ubuntu 10.10).

¿What do you mean about the installer? ¿Need I to look for another installer (linux installer) to run the game or what?

There are people that say that they can install the game with the .sh that it has. I have problems with the archive "setup.data/setup.xml", it says: "document is empty".

Thanks.

PS: I am sorry, my English is not very good... I'm spanish.

---

### Post by SeijiSensei on 2011-04-12
Sounds to me like you installed a package of add-ons that didn't include the original game engine.

---

### Post by saturnoyo on 2011-04-12
Hello [goofy00]("http://ubuntuforums.org/member.php?u=1039185"): I have searched with google and I find the same problem, but with windows. They say that it is a problem with some *.ini (there are people that say that if you copy these files the game works). I found too that Unreal Tournament 2004 has this problem (I remember that Postal use his engine, ¿no?).

I don't know, I can't install the game (Ubuntu 10.10) but I have other errors first :P

Don't look at [www.runningwithscissors.com]("http://ubuntuforums.org/www.runningwithscissors.com"). They don't have any help...

Here [http://forums.postalnetwork.org/](http://forums.postalnetwork.org/) neither (well, if you know German... I can only read the English forum and I can't find help there).

Loki and Linux Game Publishing (the companies that made the ports) don't have anything. Well, LGP has a FAQ for the linux Postal 2: [http://www.linuxgamepublishing.com/faq.php?id=22&](http://www.linuxgamepublishing.com/faq.php?id=22&)

---

