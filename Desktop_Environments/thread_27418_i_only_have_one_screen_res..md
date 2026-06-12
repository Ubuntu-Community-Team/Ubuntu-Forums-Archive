---
title: "i only have one screen res."
date: 2005-04-16
forum: Desktop Environments
---

### Post by murrowman789 on 2005-04-16
hello....i am new to linux...

i have been contemplating whether to go to linux or not...and then i found ubuntu..

so i took an old 8 gig hard drive, formated it with windows and ordered a cd from easylinuxcds.com...

i got everything installed fine..but i have one problem...

on my 15 inch gateway monitor the whole screen is way fricken to big....some windows i cant even close so i have to reboot...

the only screen resolution available is 640x480 which makes everything really big...

i need help fast....if anyone can help me please do....kthx

---

### Post by nad on 2005-04-16
Hi,

Welcome to linux.

---

### Post by nad on 2005-04-16
Further to my thick fingered command of a moment ago:

Do you know what version of ubuntu you are using?

Do you know what video adapter/display card you are using?

Dan M

---

### Post by murrowman789 on 2005-04-16
wow...for some reason you have the same first name and last initial as me...

but anyway...

i am using the newest ubuntu 5.04 Hoary

and im not sure on the video card...

looking through windows its an intel 82845G/GL/GE/PE/GV Graphics Controller

---

### Post by nad on 2005-04-16
There are currently issues with your graphics controller. Please see:

[http://www.ubuntuforums.org/showthread.php?t=27029&highlight=i810](http://www.ubuntuforums.org/showthread.php?t=27029&highlight=i810)

Keep at it and good luck.

Dan M

---

### Post by murrowman789 on 2005-04-16
i could get it to work i had write permisions on the xorg.conf file

---

### Post by nad on 2005-04-16
Open a terminal session (Applications -> System Tools -> Terminal) and enter ' sudo gedit /etc/X11/xorg.conf ' . You will be prompted for your password. You have just opened the text editor as if you were the super user. It is always safest to make a copy of a config file before you modify it. ' cp /etc/X11/xorg.conf ~/xorg.conf.orig ' . This will put a copy in your home directory.

Dan M

---

### Post by murrowman789 on 2005-04-16
i tried that from reading other posts about this problem....you have to have write permissions to edit the file

but i got help from another post....thx nad

---

### Post by nad on 2005-04-16
I'm sorry if my instructions were not clear. You will be able to save the edit as the super user.

Please describe the problem you are having with permissions.

Dan M

---

### Post by firthy on 2005-04-16
Nad, I used your info as I was having a similar prob, worked a treat..this "sudo" thing Ive gotta get used to hehehe

---

### Post by murrowman789 on 2005-04-16
thanks nad, i got it all fixed...i had to do sudo nautilus and it let me edit it

---

### Post by glucas on 2005-04-22
Adicionalmente de Ejecutar las instrucciones del enlace, tuve que definir los Hrz de refrescamiento en el monitor porque queria refrecar a  110 Hrz y para mi monitor no era valido. ok talvez a alguien le sirva esto.

---

### Post by glucas on 2005-04-22
review the refresh Hrz of monitor  an put this in the file /etc/X11/xorg.conf  sonting like that
       HorizSync       31.5 - 48.5
       VertRefresh     59.0 - 75.0

---

### Post by Stormy Eyes on 2005-04-22
[QUOTE=glucas]Adicionalmente de Ejecutar las instrucciones del enlace, tuve que definir los Hrz de refrescamiento en el monitor porque queria refrecar a  110 Hrz y para mi monitor no era valido. ok talvez a alguien le sirva esto.[/QUOTE]

Can anybody translate this? Being young and stupid, I studied French in high school, thinking I could use my knowledge to seduce pretty girls.

---

### Post by murrowman789 on 2005-04-23
i translated with google (teh 1337) and this is what happend (some words are slang and can not be translated)

[quote="google"]Additionally To execute the instructions of the connection, I had to define the Hrz of refrescamiento in the monitor because queria to refrecar to 110 Hrz and for my monitor was not valued.  ok talvez to somebody serves this to him.[/quote]

**edit-btw...its spanish...

---

### Post by Eau on 2005-04-23
I'm also experiencing the same problem where I'm only given one option for
screen resolution.....600X800

I'd need a greater screen resolution. . . perhaps there's a fix someone is aware of?

here's my video thang.

"Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device"

Since im totaly ignorant to how the terminal works and what values to edit in
Xorg Config files and the like, I'd need some one to take baby steps with me : )

---

