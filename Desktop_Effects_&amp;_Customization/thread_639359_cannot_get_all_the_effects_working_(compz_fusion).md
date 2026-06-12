---
title: "cannot get all the effects working (compz fusion)"
date: 2007-12-13
forum: Desktop Effects &amp; Customization
---

### Post by ishanmahajan on 2007-12-13
hi
I´m a newbie to linux...have gutsy gibbon running on my laptop compaq presario m2002al.
It has intel extreme graphics 2 
I cannot get all the effects of compiz fusion working...
the cube is not working (have only 2 desktops instead of 4)
the water effect and animations are not working
although other effects such as the fire, window preview, ring switcher etc are working.

in the graphics tab under administration it shows graphic card intel 85x and driver- experimental modesetting driver for intel integrated graphics chipset.
Is this the correct driver?

thankyou

---

### Post by vapore0n on 2007-12-13
Install the comopiz manager
sudo apt-get install compizconfig-settings-manager

and in there you can find where you set how many desktops you want. So from 2 to 4 or more.

Some effects might not work. Intel's driver sucks.

---

### Post by Posterus on 2007-12-13
I really doubt the driver is the issue in this situation, try installing the compiz manager like vapore0n suggested.  I'm guessing that this is just an error on your part (no offense) setting the effects correctly.

[http://www.compiz-fusion.org/]("http://www.compiz-fusion.org/") visit this site and make sure you understand everything compiz does and also how it does it.

---

### Post by mozetti on 2007-12-13
You only have 2 desktops because I think that's the default. After you install the Compiz Config Settings Manager following **vapore0n**'s instructions, change your horizontal desktop size to 4.

---

### Post by ishanmahajan on 2007-12-13
hey thank you all for the replies but i forgot to mention that i have already installed the manager and have changed the settings as mentioned by you all. But it didn't change a thing...and what about the water effect etc

---

### Post by NateMan on 2007-12-13
For the water, try manualy setting the activation key to something like crtl + r or something instead of is default, which it won't accept for some reason. What is going on when the animations don't work? A little more description would help us trouble shoot the lack of animations. The drivers should be correct, if you have an intel graphics card. what model of machine is it?

---

### Post by ishanmahajan on 2007-12-14
My laptop model is compaq presario m2002al.
It has intel extreme graphics 2

I changed the key combo but its still not working

in the graphics tab under administration it shows graphic card intel 85x and driver- experimental modesetting driver for intel integrated graphics chipset.
Is this the correct driver?

---

### Post by ishanmahajan on 2007-12-14
by animations i mean the minimize , close effect etc

---

### Post by eeshking on 2007-12-28
I don't think the graphics card is the problem. I have intel 85x too and compiz works fine for me.

---

