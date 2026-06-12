---
title: "Installpkg"
date: 2005-12-16
forum: Desktop Environments
---

### Post by dyawlak on 2005-12-16
Have downloaded the latest firefox version from Mozilla. When trying to install using KPACKAGE, it tries to use the program INSTALLPKG but can't find it. I have done a file search and I cant find it.  Did web search to download it.  Found it and installed it. It creates a ruby installpkg file but KPACKAGE still wont work.  Any ideas please?

Thanks

---

### Post by DaMasta on 2005-12-16
Where are you installing it to? Is is a .tar.gz package?

---

### Post by dyawlak on 2005-12-16
yes its firefox-1.5.tar.gz 

Using the install option in kpackpage   (file - open )

---

### Post by DaMasta on 2005-12-16
Does it show you the contents? And then you click extract? Or is the error immediate?

---

### Post by dyawlak on 2005-12-16
Using KPACKAGE, 
File
Open
locate file on  hard disk.


it opens another window headed
Install: 1 Slackware Package

Click Install

it then asks for the root password and then opens a terminal screen and tries to execute the installpkg command with the file name as a parameter.  It fails saying that it cant find installpkg.







If i use ARK it can extract the package no problem - but I don't know how to install from there - I'm a newbie where linux is concerned hence why I was using kpackage.

---

### Post by DaMasta on 2005-12-16
Yeah, that's not a slackware package. That's probably the cause of the error. Unless you're just itching to use kpackage, you can manually install it. 
Open a terminal and change to the location of the .tar.gz package. 
tar -zxvf name_of_file.tar.gz
cd name_of_unpacked_file
./configure
make
make install

---

### Post by angkor on 2005-12-16
[QUOTE=dyawlak]If i use ARK it can extract the package no problem - but I don't know how to install from there - I'm a newbie where linux is concerned hence why I was using kpackage.[/QUOTE]

I don't think it needs installing. Once you extracted the package go to the /firefox folder and launch firefox by ./firefox.

---

### Post by DaMasta on 2005-12-16
[QUOTE=angkor]I don't think it needs installing. Once you extracted the package go to the /firefox folder and launch firefox by ./firefox.[/QUOTE]
Yep, that's right. Forgot about that.

---

### Post by dyawlak on 2005-12-16
Thanks for your help on this one.

Ok ran the tar command which extracted the files to ./firefox

so cd ./firefox ok no probs.

when i did ./configure    reports no such file or directory.



Sorry to be a pain!!!

---

### Post by angkor on 2005-12-16
You do not need to *install* this package. It contains the entire program. So after extracting the package go to your newly created firefox folder and launch firefox by ./firefox.

Alternatively you can double-click on the 'firefox' file in the firefox directory in your file browser.

From the [http://www.mozilla.com/firefox/releases/1.5.html#install:](http://www.mozilla.com/firefox/releases/1.5.html#install:)

"Linux/GTK2

Extract the tarball in the directory where you want to install Firefox:

tar -xzvf firefox-1.5.tar.gz

This will create a firefox subdirectory of that directory."

In that dir will be a firefox file you can use to launch the browser.

EDIT// You don't need to use the 'tar' command. You can extract the package using Ark as you mentioned earlier in this thread.

---

### Post by DaMasta on 2005-12-16
Yes sorry, listen to angkor on this one. I forgot that you do not have to compile firefox (you did back in the day though). As he said, you can double click the firefox script in that directory or type ./firefox from that directory to launch.

---

### Post by dyawlak on 2005-12-16
ok extracted to 

./usr/bin/mozilla/firefox

select the firefox.sh from the firefox directory. Asks if I want to run it - which I do but nothing seems to happen.


Do I give up now or shoot the computer ????

---

### Post by DaMasta on 2005-12-16
DId you extract it as root? 
Type cd /usr/bin/mozilla/firefox. Then type ./firefox. Tells us of any messages that scrolls on the terminal.

---

### Post by angkor on 2005-12-16
Try installing it in your home dir. It will create a /firefox in your home. When you go to that dir.

/usr/bin/ is not the right place to extract it to

You could go for /opt (optional software)

---

### Post by dyawlak on 2005-12-16
Success,    it was missing a library file  - downloaded it and put it in /usr/lib and all works.   


MANY THANKS everyone.

---

