---
title: "Three questions."
date: 2005-11-19
forum: Desktop Environments
---

### Post by Didius on 2005-11-19
hi

A week ago i upgraded from Hoary to Breezy, and so far i am satisfied.
However some things happend that i don't like/want.

1) In the Hoary edition i loved the progress bar animation, i guess that was clearlooks. But when i upgraded to Breezy, the animation was gone. It was just a progress bar but not animated. Is there any way to get it animated once again?
[IMG]http://img474.imageshack.us/img474/7068/anim2xh.png[/IMG]

2) Is it possible to unistall theme's?

*3) In hoary i could open the terminal with a simple rightmouseclick and choosing the first item (something like "open the terminal"). In Breezy this isn't possible anymore. Can i get this handy thing back? Problem Solved*

---

### Post by Redindian on 2005-11-19
Question 3: Install nautilus-open-terminal
have fun.

---

### Post by Didius on 2005-11-19
great, thnx a lot!

---

### Post by Tiede on 2005-11-19
[QUOTE=Didius]hi

A week ago i upgraded from Hoary to Breezy, and so far i am satisfied.
However some things happend that i don't like/want.

1) In the Hoary edition i loved the progress bar animation, i guess that was clearlooks. But when i upgraded to Breezy, the animation was gone. It was just a progress bar but not animated. Is there any way to get it animated once again?
[IMG]http://img474.imageshack.us/img474/7068/anim2xh.png[/IMG]

2) Is it possible to unistall theme's?

*3) In hoary i could open the terminal with a simple rightmouseclick and choosing the first item (something like "open the terminal"). In Breezy this isn't possible anymore. Can i get this handy thing back? Problem Solved*[/QUOTE]
Well I know your frustration, since I needed to uninstall a theme also. I achieved the goal but I don't know if there exist an easier way. What I did was browse to my themes folder and delete the theme from there. i.e, in a terminal it would go like this:
```
cd ~/.themes
ls
#to identify the themes, and then
rm Whatever-the-theme-nam-eis

```

But I don't know if there is a simple way than that.

---

### Post by Didius on 2005-11-19
thnx,

that helped me a bit but not completly. When I go to my Theme preferences and if I choose Theme details, then I can choose a variaty of things. Here I have elements, window borders and icons. Is there any way of removing such a things? 

Because perhaps a reinstall of clearlooks would solve question 1

---

### Post by Tiede on 2005-11-19
Euh...  I think you did not understand me.... I deleted the WHOLE folder containing the theme I did not want. For example, if the output of 
```
ls
``` was ```
My_Theme_1
Theme_I_Like
Theme_i'll_delete 
```,
then I just delete the whole Theme_i'll_delete folder

Too confusing explanation? :D

---

