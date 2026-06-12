---
title: "WallpaperZapper!! How to install"
date: 2006-06-15
forum: Desktop Environments
---

### Post by true_friend on 2006-06-15
HI folks its true firend. any one can help him he is woundering how to install the zapper there are only two souce code files.:confused:  
>>>>>>>>>>    [http://www.gnomefiles.org/app.php?soft_id=999](http://www.gnomefiles.org/app.php?soft_id=999)
and hows to install the themes relating to mouse cursors and icons:rolleyes:

---

### Post by blackjack6.21.91 on 2006-06-15
To build a package from source, it's important to have the package build-essential.  Once you have that, you should extract the file and open a terminal in the directory with the extracted source.  To change into this directory, use the command
> cd ~/Desktop/wallpaperzapper-0.1.1
assuming you saved the file to your desktop and the extracted folder is named wallpaperzapper-0.1.1.  In the terminal you would then punch in
> ./configure
make
sudo make install

You might get some error's - I probably can't help you with those, so good luck!

---

