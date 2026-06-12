---
title: "Unity broken after wine install/remove"
date: 2012-10-07
forum: Desktop Environments
---

### Post by schmi85 on 2012-10-07
Hello Everybody!

Yesterday I installed the nvidia driver for my laptop. What actually worked in the end.

Linux: Ubuntu 12.04
Graphic card: GeForce GT 330M

But today, after restart (computer was switched off while I was sleeping :) ) it does not use the nvidia driver anymore.

So:

[LIST=1]
[*]I cannot set icon size of launcher anymor
[*]openGL does not work anymore
[*]all cool window effects (shadows, transition) do not work anymore
[/LIST]
all in all when I was searching I could find out that it is connected to the unity mode 2d and 3d, while it refuses to use 3d.


[IMG]http://i.stack.imgur.com/jBXtF.png[/IMG]

that is the result of running the **unity_test -p** 

Yesterday it worked, today not --> it is not depending on the hardware, something broke when deinstalling wine1.5, with this I am quiet sure but I do not know how to fix it.

Greetings
philipp

edit:::

so I tried to reinstall xorg with:

apt-get remove --purge xserver-xorg
apt-get install xserver-xorg

nothing changed

and when I tried just to reinstall the graphics driver with

apt-get remove --purge nvidia*

it tells me that nothing was removed...

what could I try???

---

### Post by 2F4U on 2012-10-07
If you can't remove the nVidia driver, it may have been remove before and this could also be the reason why you are in Unity2D instead of Unity3D. Did you try to install the nVidia driver again?

---

### Post by schmi85 on 2012-10-09
Hello!

The driver was installed. But re installing it solved the problem. Now everything works fine again.

Greerings
philipp

---

