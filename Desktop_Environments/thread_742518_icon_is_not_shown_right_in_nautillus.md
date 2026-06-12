---
title: "icon is not shown right in nautillus"
date: 2008-04-01
forum: Desktop Environments
---

### Post by thomas_vergote on 2008-04-01
Hi,

I've tried some icon themes in Ubuntu (Hardy-Heron beta) but I seem to have a problem. In nautilus the icon for the normal folders is the icon of the 'gnome' icon theme, while it should be something totally different. I saw earlier that the theme didn't seem to be applied in the 'Places' menu and in the side bar of nautilus, but now it doesn't even apply the theme for the normal folder icons. 
Strangest thing of all: if I click properties of a random folder, and I try to change the icon manually (by clicking the icon in the "Properties" dialog), I get a dialog where I have to choose an icon, so actually again a 'file manager', and I assume (what would it be else?) a nautillus file manager-dialog. But here, the icon theme is applied just like it should be, even in the side bar!

So the logical question is, how should I make nautilus applying the icon themes, or, otherwise, how should I totally change my file manager if there is no other solution? (I have been using thunar lately, but the need for nautilus stays, and working with two file manager doesn't seem very efficient..)

Thanks!

---

### Post by dulbirakan on 2008-04-26
I have the same problem in 8.04 Hardy Heron...

---

### Post by alfiejs on 2008-05-13
Ok, same problem for me, but only in one particular icon theme.  My spidey sense is leading me to think it's a scalable (SVG) icon issue, or the lack of a scalable icon in the correct folder  I am going to continue playing with what I have until I break my icon theme beyond recognition or solve it.

---

### Post by alfiejs on 2008-05-13
You probably originally used the gnome-dev-harddisk.png to show a hard disk icon.
In some themes, not having the gnome-dev part, but just drive-harddisk.png shows the object with the correct icon.

Playing with these names (renaming to create a fallback)  has returned my icon theme to the way it should look.

---

