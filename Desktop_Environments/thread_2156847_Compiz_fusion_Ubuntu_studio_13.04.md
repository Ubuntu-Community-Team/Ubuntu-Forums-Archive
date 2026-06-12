---
title: "Compiz fusion Ubuntu studio 13.04"
date: 2013-06-23
forum: Desktop Environments
---

### Post by danielcrvg on 2013-06-23
Hi all i'm trying to install compiz on the ubuntu studio 13.04.

I already install compiz manager and compiz extra..


but i install fusion icon, and when i run it, returns this error:


dani3l@nirvana:~$ fusion-icon 
 * Detected Session: ubuntustudio
 * Searching for installed applications...
Falha de segmentação (imagem do núcleo gravada)
dani3l@nirvana:~$ 


Translating means Segmentation Fault...


what can i do now??

i saw some people saying its a bug.. has any solution by this time??

---

### Post by Frogs Hair on 2013-06-23
First try the following .

```
compiz --replace
``` 

The instructions at the link are for Xubuntu, but I find no equivalent for Ubuntu studio . What they have in common is XFCE/XFWM4 window manager, but the instructions may not work on U Studio.  [http://www.webupd8.org/2012/11/how-to-set-up-compiz-in-xubuntu-1210-or.html](http://www.webupd8.org/2012/11/how-to-set-up-compiz-in-xubuntu-1210-or.html)

---

### Post by danielcrvg on 2013-06-23
i really need dconf and gconf? they are for gnome ...

---

### Post by danielcrvg on 2013-06-23
On the gconf configuration, i cant find the theme metacity to chance to Greybird! it´s no inside App..

---

### Post by Frogs Hair on 2013-06-23
I can only ask if Greybird is installed and set as your current theme ?

---

### Post by danielcrvg on 2013-06-23
yes, greybird is the my current theme..

---

### Post by Frogs Hair on 2013-06-23
The title-bar /Metacity theme also ? If yes you will have to wait for someone using Compiz. I have the XFCE session installed, but have not enabled Compiz. You can check the title-bar theme under window manager.

---

### Post by danielcrvg on 2013-06-24
hi i saw at Cofiguration/configuration manager/window manager and the theme there is BlackBird

---

### Post by Frogs Hair on 2013-06-24
I am logged into XFCE and I see both Blackbird and Greybird title bar themes in settings> window manager.

---

### Post by danielcrvg on 2013-06-24
i know.. but dont have metacity. On the tutorial is saying to change metacity to Greybird, but i didn't found metacity on the gconf to swich the themes...

---

