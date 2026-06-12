---
title: "Problems with resolution need help!!! Plz!!!"
date: 2010-04-13
forum: Dell Ubuntu Support (CLOSED)
---

### Post by jaimemetalgc on 2010-04-13
hi, i'm new with this ubuntu 9.10. I installed ubuntu on my optiplex gx110 a very very ultra old pc PIII 512 RAM 60gb HDD / so everything was fine, ubuntu installed fine, but when i restarted the pc, I log in and ubuntu started but my resolution was very very small, i ussually use 1024 x 768 ; but now am at 640x480 and it really sucks, also my screen is horrible i can't see anything i just can see white lines and a orange background , i just can see my desktop when i log in in GNOME(safe mode), i really need help. thanks.

---

### Post by 2hot6ft2 on 2010-04-13
I had that happen before and had to guess as where the System menu might be (by clicking around with my mouse) until I found it. Try this

Press Alt+F2
tick the Run in Terminal box
and run
```
sudo apt-get update
```
You will have to enter your password which wont be displayed just type it in and hit Enter
then once it finishes if you can go to
System > Administration > Hardware Drivers
and see if there is a restricted driver for your graphics card.
If there is select it in the top window and click on Activate at the bottom.
It will download it and install it, then you will have to reboot.

You can also start Hardware Drivers by using Alt+F2 and using this in it (without the Run in Terminal box checked)
```
/usr/bin/jockey-gtk
```

Now whether or not any of it shows up in the part of the screen that you CAN see is another thing.

And welcome to the forum.

---

