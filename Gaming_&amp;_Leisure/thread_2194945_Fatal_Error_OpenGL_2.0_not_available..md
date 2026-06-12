---
title: "Fatal Error: OpenGL 2.0 not available."
date: 2013-12-21
forum: Gaming &amp; Leisure
---

### Post by AE14318791841955 on 2013-12-21
Hi guys

I have searched forums but i am unable to fix it 

[IMG]http://i.imgur.com/SpP6Dej.png?1[/IMG]

[IMG]http://i.imgur.com/yBZXh8y.png?1[/IMG]

---

### Post by bapoumba on 2013-12-21
Thread moved to Gaming.

---

### Post by AE14318791841955 on 2013-12-21
Sorry about that , GUYS HELP ME i can't uninstall , the game savage 2 

OMG savage is a linux game and it wont start  

I TRIED ALL COMMANDS :S

UPDATE : i FIXED IT NOW :)

sudo rm -r /usr/local/games/Savage2

Lol i removed the directory not uninstalled HOW TO FIX IT ??

---

### Post by bapoumba on 2013-12-21
No need to be sorry, I thought some people here could help you.

How did you install the game ? Removing directories is not the way to remove a package.

---

### Post by AE14318791841955 on 2013-12-21
installed via terminal dragging or inserting code , i know but i runned uninstall but it says failed error etc
so i thought remove directory but if i click search and then write savage 2 it still exist but cannot be open any suggestions?

---

### Post by bapoumba on 2013-12-21
Please find again the link for the instructions you ran to install. There probably is a way to uninstall, but if you removed files, you'll probably have to reinstall and uninstall in a clean way as per the instructions. Did you run some dpkg command ?

---

### Post by AE14318791841955 on 2013-12-21
chmod +x Savage2Install-2.1.0.1-x86_64.bin
sudo ./Savage2Install-2.1.0.1-x86_64.bin

This i used for installation ( i installed again same directory how i uninstall now or how i start savage 2 without getting errors? )

and this i get too in terminal after run commands above

(Savage2Install-2.1.0.1-x86_64.bin:21567): IBUS-WARNING **: The owner of /home/hl/.config/ibus/bus is not root!

---

### Post by bapoumba on 2013-12-21
Where did you download the package from ? Would you have a link ?
You cannot run the game now if you have manually removed files. You'd need to reinstall it.

---

### Post by AE14318791841955 on 2013-12-21
I reinstalled savage 2 
and i got the package from [www.playsavage2.com]("http://www.playsavage2.com") 

Linux 64 bit

UPDATE Its still not fixed any help much apreciated :)
           cannot start savage 2 it turns black then it goes back to desktop

---

### Post by bapoumba on 2013-12-21
May be here: [http://forums.savage2.com/showpost.php?p=219828&postcount=5](http://forums.savage2.com/showpost.php?p=219828&postcount=5)

---

### Post by AE14318791841955 on 2013-12-21
the link is dead within the link ( so i give up savage 2 ) so what i want is uninstall 
but getting failed how i make it work?

[IMG]http://i.imgur.com/sUsLL4k.png?1[/IMG]

---

### Post by bapoumba on 2013-12-21
For the uninstall script to work, you need to reinstall it as you have removed some files. So install it over and uninstall.

---

### Post by AE14318791841955 on 2013-12-21
i did install it over still getting error ? do i need copy paste first the script in terminal and then run uninstaller?

is there any chance of u willing to help with remote program?


UPDATE i uninstalled it this helped me [http://ubuntuforums.org/archive/index.php/t-1020630.html](http://ubuntuforums.org/archive/index.php/t-1020630.html)

i added sudo and then dragged the uninstaller to the terminal with space between sudo and uninstaller :))
 sudo '/usr/local/games/Savage2/uninstall-Savage2.sh'

I will mark this as solved , technicaly game didnt start so i don't know its solved but i will try another games :)

---

### Post by bapoumba on 2013-12-21
OK, so your screenshot is after reinstalling.

Looks like the script owner is root, so you'd need to use a root shell to run it.
```
sudo su
```
Careful, you'll be root with a # prompt. When done, exit the root shell with
```
exit
```

---

### Post by bapoumba on 2013-12-21
> **AE14318791841955 said:**
> i did install it over still getting error ? do i need copy paste first the script in terminal and then run uninstaller?

is there any chance of u willing to help with remote program?


UPDATE i uninstalled it this helped me [http://ubuntuforums.org/archive/index.php/t-1020630.html](http://ubuntuforums.org/archive/index.php/t-1020630.html)

i added sudo and then dragged the uninstaller to the terminal with space between sudo and uninstaller :))
 sudo '/usr/local/games/Savage2/uninstall-Savage2.sh'

I will mark this as solved , technicaly game didnt start so i don't know its solved but i will try another games :)

Sorry, I did not see the edit on this post as I was looking around the savage website for info, until I went back to your screenshot :)

Glad you fixed it!

---

