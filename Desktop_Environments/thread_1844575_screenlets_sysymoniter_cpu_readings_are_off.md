---
title: "screenlets sysymoniter cpu readings are off"
date: 2011-09-15
forum: Desktop Environments
---

### Post by murderd2death on 2011-09-15
i downloaded and installed screenlets, i have sysmoniter up and running on the side. the cpu and up/download readings are [off significantly]("http://i.imgur.com/911Tm.png"). i was wondering if there was anything i could get or do to correct this.

regards.

---

### Post by Frogs Hair on 2011-09-15
The type of sensors used in your computer might not be compatible with the Screenlet and I don't know if there is anything can be done about that . Have you considered Conky ?  This one comes with dark and light version and is not too hard to set up .  [http://gnome-look.org/content/show.php/Conky+Flavours?content=94467](http://gnome-look.org/content/show.php/Conky+Flavours?content=94467)

---

### Post by murderd2death on 2011-09-15
> **Frogs Hair said:**
> The type of sensors used in your computer might not be compatible with the Screenlet and I don't know if there is anything can be done about that . Have you considered Conky ?  This one comes with dark and light version and is not too hard to set up .  [http://gnome-look.org/content/show.php/Conky+Flavours?content=94467](http://gnome-look.org/content/show.php/Conky+Flavours?content=94467)
  it says i have conky installed but i dont know how to run it

to be more specific, i have "highly configurable system moniter (transitional package)" and when i do "sudo apt-get install conky" it says i have the newest version already there, i just cant seem to find the front end GUI  of it, am i going to have to run terminal?

---

### Post by Frogs Hair on 2011-09-15
> **murderd2death said:**
> it says i have conky installed but i dont know how to run it

Are you using the one at the link I posted or another one ?  If you are using the one I posted  , download ,  extract the package and move the folder any place you want  in your home folder .

Inside the  the folder is an install run document  . Click on the document  , select run  , and follow the instructions  . A desktop icon will be created with this theme and you can drag it to the folder where you moved Conky to if you don't want it visible . Click the icon to start and a dark or light option will be offered .

This is a configuration for Conky as the default configuration is not much to look at . If you would like to see the default configuration use Alt+F2 .   
to start type conky and to stop type killall conky  .

---

### Post by murderd2death on 2011-09-15
> **Frogs Hair said:**
> Are you using the one at the link I posted or another one ?  If you are using the one I posted  , download ,  extract the package and move the folder any place you want  in your home folder .

Inside the  the folder is an install run document  . Click on the document  , select run  , and follow the instructions  . A desktop icon will be created with this theme and you can drag it to the folder where you moved Conky to if you don't want it visible . Click the icon to start and a dark or light option will be offered .

This is a configuration for Conky as the default configuration is not much to look at . If you would like to see the default configuration use Alt+F2 .   
to start type conky and to stop type killall conky  .

i tried running conky through that program but it doesnt find anything, ive used terminal but like you said its not much to look at and i cant move it off to the other side. im going to look into the more graphic versions of conky later. 

i did look into another screenlets monitor and they seem to be [more accurate]("http://i.imgur.com/RYhWj.jpg"), but altogether its very wonky.

---

### Post by Frogs Hair on 2011-09-15
Make sure you have lm sensors installed properly  .  ```
sudo apt-get install lm-sensors
``` Then run the following command and answer yes to all questions . ```
sudo sensors-detect 
```

---

