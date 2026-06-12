---
title: "sunbird"
date: 2006-02-02
forum: Desktop Environments
---

### Post by ESPOiG on 2006-02-02
i installed alien, then installed mozilla sunbird with it

sudo alien -i /home/ross/Desktop/sunbird-0.3a1.en-US.linux-i686.tar.bz2

ive never done this before... so i dunno if it is installed or not and if it is how do i run it... i typed sunbird into terminal and mozilla-sunbird

how do i know :P

---

### Post by DaMasta on 2006-02-02
You don't need to alien a tar.bz2 file. Run **bunzip sunbird-0.3a1.en-US.linux-i686.tar.bz2 | tar -xvf sunbird-0.3a1.en-US.linux-i686.tar.bz2**. Then cd into the firebird directory. You should see a sunbird file. Run ./sunbird.

---

### Post by ESPOiG on 2006-02-02
i dont understand

---

### Post by GeirG on 2006-02-02
As your reply was pretty general, I assume you didn't understand **anything** of what DaMasta wrote.
If this is not the case, please remember to be more spesific about what you didn't understand the next time. That makes it easier to help, and shows a little effort on your part.

1. Alien is used to convert or install a binary package, like changeing a .rpm (redhat) to a .deb (Debian, Ubuntu). Your file is not such a package, its a compressed archive kinda like zip (just a little different)
I'm not too familiar with alien, but I would think it gave some kind of error message telling you that it didn't do anything with the file.
This kind of information would also be nice to know for people trying to help you.

2. What you need to do is to extract the archive to your disk.
Open a terminal:  Applications->accessories->Terminal
Change to the Desktop directory by typing "**cd Desktop**", and hit enter. 
Extract the archive by typing:
**bunzip sunbird-0.3a1.en-US.linux-i686.tar.bz2 | tar -xvf sunbird-0.3a1.en-US.linux-i686.tar.bz2**

This probably creates a directory called sunbird, or sunbird-03a1, or something like that.
Move into this directory, using the cd command as you did to get into te Desktop directory. 
**Note:** DaMaster has made a typo, as he tells you to cd int the **firebird** directory. This should of course be the **sunbird** directory.
If DaMaster is correct, which I have no reason not to belive, there should be an executable file called **sunbird** in this directory.
Run this file using the command **./sunbird**

Hope this helps

---

### Post by ESPOiG on 2006-02-02
sorry for being brief... i was busy but i did understand most of it... the firebird item threw me off as i dont really that much as wat i was doin... and as firebird = firefox sum time ago i was sorta confused but now i get yah and i have the program workin fine

sorry to both of yah

1 more thing how hard is it to make a .deb file from those that are in the tar.gz file or do i need the source as the know how :D

thx anyway

---

### Post by ESPOiG on 2006-02-02
another question how do i gksudo (create a launcher) :P

---

### Post by GeirG on 2006-02-02
Don't really know much about making .debs, sorry.

Don't know what you want gksudo for, but creating a launcher is as easy as right-clicking on the desktop and choosing "Create Launcher..."

---

### Post by ESPOiG on 2006-02-02
no i mean if i copy my say sunbird files into the filesytem and then make a launcher for it i cant use the icon that is in the files... unless i set permission for my self to be able to access the icon

---

