---
title: "Move window controls without breaking theme"
date: 2010-05-03
forum: Desktop Environments
---

### Post by cfalzone on 2010-05-03
Could anyone point me to modifying metacity themes so that the window controls will be displayed with the correct image even after being moved using gconf-editor?

I have seen many scripts that move the window controls to the right as they were in previous releases of Ubuntu before Lucid Lynx, however, I'm looking the move the controls to the left with a metacity theme that currently displays the controls on the right side.  I have no experience making metacity themes -- as such, what should I edit in the theme.xml file to make the theme place the images on the left side and display correctly?

Thanks to all who help!

---

### Post by dagrump on 2010-05-03
Well, it stands to reason if in gconf-editor to move them back to the the right, it's menu:minimize,maximize,close then close,maximize,minimize:menu should toss them to the left. I've never tried it, but I see no reason too!
It is your box do whatever you like.
If that doesn't work then you just need to put it back as it was & wait till some else chimes in. 
Good luck.

---

### Post by kenweill on 2010-05-03
just customize the theme like what i did. start form "clearlooks" theme then customize.

---

### Post by cfalzone on 2010-05-04
Right -- I know that I can use gconf-editor, but the problem is that the themes only display the the controls "correctly" on the right side of the window.  I can move them around on the right side in any way I please and they still look correct, but if I move the controls to the left side then they no longer look correct.

I think the problem is that the .xml theme file can only specify the color of the control boxes when they're on the right side.  I don't know how to fix this, however, and was wondering if anyone happened to know how to quickly resolve the issue.

[EDIT]
I actually just used a tool called Homosapien Customizer to make the theme the way that I want it.  However, if anyone knows of a way to change the control position (left, right)without breaking the button color it would still help.

---

