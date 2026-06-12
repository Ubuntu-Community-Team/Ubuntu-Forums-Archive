---
title: "[SOLVED] Desktop launchers not working on laptop"
date: 2008-05-01
forum: Desktop Environments
---

### Post by tropdoug on 2008-05-01
HI guys, 

I have a desktop machine and a Toshiba A100 laptop. Both have new clean installs of 7.10 on them (not prepared to move to 8.04 yet until I learn more) My wife prefers icons on the laptop, so for openoffice.org word processor, I right clicked the menu and created a desktop launcher. The command code is ```
ooffice -writer %U
```when clicked the icon darkens, and nothing happens. When the menu item is clicked all is well, the program opens. When I put the command in a terminal I got ```
/hom/kim/%U does not exist
``` but if I remove the %U it opens the program.

So I removed the %U from the launcher command line, and it still won't work. I have tried this with a number of other launchers, and found that none will work on the desktop. I have done exactly the same thing on the desktop machine, and all work perfectly. 

Any ideas?

---

### Post by Hagar Delest on 2008-05-03
Try soffice instead of ooffice.

---

### Post by tropdoug on 2008-05-05
Just tried that, no difference. any other ideas? anyone?

---

### Post by Hagar Delest on 2008-05-05
And if you right click on the desktop to create the launcher and then browse the files until you find the soffice script in the /OpenOffice.org 2.4/program folder?

---

### Post by tropdoug on 2008-05-05
and where can I find that folder, I have been searching and cannot find it? also what is the Linux equivalent of a MS Exe file for launching it? By the way what is soffice? I thought it was always ooffice

---

### Post by Hagar Delest on 2008-05-05
soffice or ooffice (may depend on the version you're using) are the file to be launched. They can be in /usr/lib/openoffice or /opt/openoffice.org 2.4.

---

### Post by retrow on 2008-05-06
If you want to search for the location of a specific file:
```
sudo updatedb
```This may take a while depending upon the size and contents of your drives. Once you're done, you can search for a cerain filename by running:
```
locate filename
```

---

### Post by tropdoug on 2008-05-06
Thanks for that retrow, I found em. 

Ok so I created the launcher and found the right files, but still no dice. If I right click and then click 'Open' the file program opens, but if I left click (double or single) nothing happens. Its as if the launcher is not picking up the double click. 

I checked the mouse utility in systems and the double click time is perfect, so I am still scratching my head. 

Using the location of those files, and the advanced desktop settings manager, I have added the command lines to shortcut keystrokes, like alt+w to open writer, and that works perfectly too. So the problem is definately in something in gnomes desktop not being right.

---

### Post by retrow on 2008-05-06
Oh, now this reminds me of a time not too long ago. I had a similar problem which prevented me from opening OpenOffice.org writer. Try opening it from the menu itself. If it doesn't open from the main menu, there is a chance that the package is broken. Try searching for and reinatalling *openoffice.org-writer*. If there is a problem with the word processor package itself, the launcher is just firing blanks.

---

### Post by tropdoug on 2008-05-06
All the menu items work perfectly, but the user (wife) of the laptop prefers icons on the desktop to launch her programs. It seems that none of the programs will open from their launchers on the desktop, (see my original post in the thread) 

it really seems odd, particularly because the same system from the same disc was setup a few weeks before on my machine and all works fine with that. 

So still looking for other thoughts. :-)

---

### Post by tropdoug on 2008-05-12
Please ignore. Problem now solved, and as usual it was simple. Even though every other part of office was working okay, none of the programs would launch off the desktop. Other programs like gimp etc would, so I removed and reinstalled Open office suite, and all is well. 

Thanks for the time people spent with me on this one. :-)

---

