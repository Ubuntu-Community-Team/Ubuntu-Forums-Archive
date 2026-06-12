---
title: "Desktop effect has stoped working, Samsung nc10, 8.10"
date: 2009-02-23
forum: General Help
---

### Post by Sjellest on 2009-02-23
Hi.

I bought a Samsung NC10 for about 3 weeks ago, and except for some minor frustrations with backlight, shortcuts and so on, it have worked perfectly! 

I haven't had any problem with desktop effects at all, but yesterday i needed to a show a slideshow on a external monitor and since then i have been unable to enable desktop effects. I cant figure out what the problem is, but PlEASE help me :)
And by the way...: Im NOT looking for people to tell me that i shouldn't be using desktop effects on a netbook, because i was perfectly happy with the previous setting...

---

### Post by hangnail on 2009-02-25
i had exactly the same problem a few days ago...

i found a solution in another thread....im searching for it all the while but cant find it any more...

i think i made a bookmark on my other pc...i will post it as soon as i come home from work.

EDIT: ok, here it is...

[http://swiss.ubuntuforums.org/showthread.php?p=6582144](http://swiss.ubuntuforums.org/showthread.php?p=6582144)

---

### Post by Sjellest on 2009-02-25
I appreciate you taking time to help me :)
But im not so skilled with all this computer fixing stuff :O But i read that thread and tried to run the commands, but it didn't work. 
Every command said "No such file or directory" except for the last one:
"sudo echo 'KERNEL=="card[0-9]", MODE="0666", OWNER="root", GROUP="video"' > /etc/udev/rules.d/60-card.rules"
It said: "bash: /etc/udev/rules.d/60-card.rules: Permission denied"

It seems like i have misunderstood something or running the commands wrong or maybe have my card placed somewhere else? I would really appreciate some help here.

I use my computer for studying and many of my fellow students have showed interest in the computer (samsung nc10) and ubuntu, but without the desktop effects, and without me being able to do anything about it, i dont think i can seriously convince them about using this with ubuntu... :/

---

### Post by hangnail on 2009-02-26
ok...open the terminal in type in: glxinfo | grep OpenGL

you should see something like:

> OpenGL vendor string: Mesa Project
OpenGL renderer string: Software Rasterizer
OpenGL version string: 2.1 Mesa 7.2
OpenGL shading language version string: 1.10
OpenGL extensions:


**OpenGL renderer string: Software Rasterizer** -> this is your problem. there should stand something like that:

> 
OpenGL vendor string: Tungsten Graphics, Inc
**OpenGL renderer string: Mesa DRI Intel(R) 945GME 20061102 x86/MMX/SSE2**
OpenGL version string: 1.4 Mesa 7.2
OpenGL extensions:

i fixed this issue by adding this to my xorg.conf:

> Section "DRI"
mode 0666
EndSection

to do that open the terminal again and type in: sudo gedit /etc/X11/xorg.conf

in the new window you can copy the text above into the xorg.conf file and save it.
(if you dont have gedit just install it with sudo apt-get install gedit or use another editor).

after that type this into the terminal : sudo chmod 666 /dev/dri/card0

done. reboot your nc10 and youre ready.

---

### Post by cherry316316 on 2009-04-03
> **hangnail said:**
> ok...open the terminal in type in: glxinfo | grep OpenGL

you should see something like:




**OpenGL renderer string: Software Rasterizer** -> this is your problem. there should stand something like that:



i fixed this issue by adding this to my xorg.conf:



to do that open the terminal again and type in: sudo gedit /etc/X11/xorg.conf

in the new window you can copy the text above into the xorg.conf file and save it.
(if you dont have gedit just install it with sudo apt-get install gedit or use another editor).

after that type this into the terminal : sudo chmod 666 /dev/dri/card0

done. reboot your nc10 and youre ready.
when i use command 

```

sudo chmod 666 /dev/dri/card0

```

i get message no file found :(

also when i do 
```

ls /dev/dri

```
i dont see any folder. The "dri" folder is missing.

what can I do? I am using Ubuntu 9.04 beta on Samsung NC10.

---

