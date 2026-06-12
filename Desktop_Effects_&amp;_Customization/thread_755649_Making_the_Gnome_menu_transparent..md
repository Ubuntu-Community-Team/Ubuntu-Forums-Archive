---
title: "Making the Gnome menu transparent."
date: 2008-04-15
forum: Desktop Effects &amp; Customization
---

### Post by Gaztech on 2008-04-15
Hello,

I was wondering if someone could help me, I've managed to make my gnome panel transparent (very easy:)) so it looks like something below, which merges nicely with my wallpaper and the white texts stands out nicely. However I would like to the make the gnome menus (that fall underneath Applications, Places and System) to have the same effect, transparent background with white text. Can anyone tell me how this is done? 

I have tried to change the opacity setting in the general section of the compiz fusion options menu (CCSM) pointing it to gnome-panel but that changes the top panel and I want to change the menu transparency. Also if someone can tell me how to change the text colour I'd also be very appreciative :)
[[IMG]http://img143.imageshack.us/img143/9572/76338911wq8.th.jpg[/IMG]](http://img143.imageshack.us/my.php?image=76338911wq8.jpg)

Many thanks!

---

### Post by LeoSolaris on 2008-04-15
Transparent I have not figured out, but opacity I can tell ya.

To give the menus some opacity, get to the general setting in compiz, then to the Opacity Settings tab. You will have to add ```
popupmenu
``` and a value above 700 (on the positive side) on that slider. I have not learned yet how to fine tune it, but a little bit of playing with it will get ya somewhere I am sure. 

Leo

P.S. Do not put "any" in that box, it will make every window you have transparent, leaving you with just your desktop and mouse! I fixed that by logging out and logging into failsafe Gnome. Its in the Sessions at login.

---

### Post by Gaztech on 2008-04-15
Heh thanks for the tip :)

---

### Post by LeoSolaris on 2008-04-15
> **Gaztech said:**
> Heh thanks for the tip :)
Your most welcome!

(Just so ya know, that little star with a blue ribbon by the quote button at the bottom of the posts you didn't write is a "thanker" It will add to the number of thanks received, which is displayed at the top of the post on the right.)

---

### Post by strabes on 2008-04-15
The transparency in that screenshot would have to be accomplished by right clicking on some empty space in the panel, clicking on "Properties," going to the "Background" tab of the Panel Properties window, enabling "Solid color," and then lowering its transparency in that same window. I'm not sure how you would make the menu text white.

---

### Post by studo77 on 2008-04-28
> **strabes said:**
> The transparency in that screenshot would have to be accomplished by right clicking on some empty space in the panel, clicking on "Properties," going to the "Background" tab of the Panel Properties window, enabling "Solid color," and then lowering its transparency in that same window.

On my system it only changes the color and transparency on empty panel-space, and on the program link icons. Also when going all transparent it goes dark instead of see-through.

In short: I would also like to see the easy way to get the attached style of panel. > to make my gnome panel transparent (very easy)  How?

[edit]:Ok, the problem is somewhere in my theme choosing. Tried Human, and the transparency is good. But the text colour, is still an unfound variabel.

---

### Post by studo77 on 2008-04-28
Install gnome-color-chooser and choose the rainbow of your liking. :-P


But the panel transparency is not good looking. It somewhat transparent, but nowhere near some of images scattered here on the forums.

How do you get the background of the panel so that it looks like it is not even there?

---

### Post by locketine on 2008-04-28
> **studo77 said:**
> Install gnome-color-chooser and choose the rainbow of your liking. :-P


But the panel transparency is not good looking. It somewhat transparent, but nowhere near some of images scattered here on the forums.

How do you get the background of the panel so that it looks like it is not even there?

oh man, thanks for that bit about gnome-color-chooser, now I can actually read the panel text when I have a dark background.

I dunno what ur problem is exactly.. I have my panel set at max transparency and the only way you can tell it's there is the glowing border effect compiz throws on it.

---

