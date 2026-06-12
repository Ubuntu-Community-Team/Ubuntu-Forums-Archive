---
title: "Refresh Rate Problem"
date: 2009-01-26
forum: General Help
---

### Post by PurpleDog on 2009-01-26
I have a Phillips Brilliance 202P4 flatscreen CRT monitor and my standard Windows settings are 1024x768@100Hz refresh rate. My graphics card is an nVidia GeForce 7600 GS. I have installed Ubuntu 8.1 and after install it automatically updated the nVidia driver.

I still only have an option for 640x480@51HZ and the display hurts my eyes. Before I can possibly continue with Linux I have to get this right. How?

I am new to Linux.

---

### Post by Egi_Power on 2009-01-26
You could try installing the driver from nVidia.com.

Check out this post by *starcannon*, it might be helpful:

[http://ubuntuforums.org/showpost.php?p=5086971&postcount=6]("http://ubuntuforums.org/showpost.php?p=5086971&postcount=6")

Did you try to boot into recovery mode, and select [COLOR="Blue"]xfix[/COLOR] from the menu?

---

### Post by cyclobs on 2009-01-26
your monitor might not be detected properly.

best option to see if this is right you could try changing the resoultion manually.

```


*first thing to do is back up your current xorg (incase something goes wrong)

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bkp

[
so if something goes wrong you just do the opposite to that and you have a usable linux again

sudo cp /etc/X11/xorg.conf.bkp /etc/X11/xorg.conf
]

*open xorg with sudo

sudo gedit /etc/X11/xorg.conf

*once that opens look for something like 

640x480_51 +0 +0 under display or screen or something simular (can't help you specifally with that one since my conf is quite complicated thanks to dual monitors)

then replace it with 

1024x768_100

then save and press ctrl+alt+backspace

```

hopefully that will work out for you

---

### Post by PurpleDog on 2009-01-26
Thanks for the info everyone. I have tried both routes several times and still only 640 x 480 @ 50HZ. I will have to get someone in here to help me before I can continue.

---

