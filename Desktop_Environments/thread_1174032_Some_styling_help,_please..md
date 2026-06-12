---
title: "Some styling help, please."
date: 2009-05-30
forum: Desktop Environments
---

### Post by Zilch on 2009-05-30
Hi.

I just installed some OS X themes, and so far, I like everything.... except for two things - the panel's and the title bar's colour.

What I would like to do is to change this:
[img]http://img41.imageshack.us/img41/8368/queriendo.png[/img]
to this:
[img]http://img297.imageshack.us/img297/1007/want.png[/img]
(I know the editing is horrible but I hope you get the idea)
Shortly put: black panel, white panel text, black window border, white window border text.

Unfortunately my knowledge of Linux is too limited for me to do this myself, and Google is not helping either. So I'd now like to ask you.... is this possible?

If it matters, I'm on Ubuntu Hardy.

Thanks.

---

### Post by picopir8 on 2009-05-30
Get emerald, then download one of the mac clone emerald themes that are out there.

Also download compiz config settings manager if you have not already done so.  Open it, click on window decorations, then replace the text in the "command" edit box with "/usr/bin/emerald --replace"

Log out, then log back in.  Now launch emerald and as you edit your theme you will see the changes apply to any open windows.

Open the theme that you want, then click the edit themes tab.  Click on the theme engine drop down, it will allow you to change the colors.  Selecting different theme engines will allow for different window effects.

Dont worry if the buttons at the top of the title bar in in the wrong place.  If you click on the titlebar tab you can move them around by editing the title-bar object layout.

Here is how I modified my title bar using emerald:
[IMG]http://img6.imageshack.us/img6/9197/screenshotvan.png[/IMG]

---

### Post by Zilch on 2009-05-30
Thank you so much! The window borders are nice and black now. :D

Can I do anything to make the gnome panel black?

---

### Post by picopir8 on 2009-05-30
Right click panel and edit the properties, you can set it to any color you want.  If you want any sort of texture, save a .png file that looks like what you want then set that as the background image.

Or use cairo-dock if you want to stick with your mac like theme.

---

### Post by Zilch on 2009-05-31
Tried setting the panel background already......this is the result:
[img]http://img5.imageshack.us/img5/5346/schermafdruk1h.png[/img]

---

