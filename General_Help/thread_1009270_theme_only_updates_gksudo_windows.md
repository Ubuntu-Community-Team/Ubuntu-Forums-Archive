---
title: "theme only updates gksudo windows"
date: 2008-12-12
forum: General Help
---

### Post by birnam on 2008-12-12
This is a weird problem -- or at least I think so, I'm relatively new to linux. This is on a new installation of Ubuntu 8.10 amd64.

I'm trying to customize the themes in the Appearance dialog. Specifically, I have one called Cassandra Mint, although as far as I can tell this is part of a general issue that affects all themes. In theme customization, when I select "controls" and select the Cassandra Mint controls, I see only a very minor difference, if any, in most of my windows.

Except! And here's the weird part. If I have a window that I opened with gksudo, then the theme is applied perfectly.

The Cassandra Mint theme is a good test for this because it comes with two variations, one with boxy buttons and one with rounded buttons. Flipping between these shows appropriate results in a gksudo window, but has zero effect in my other windows.

I've attached a side-by-side capture of two windows, one of which was opened with gksudo (top) and one that was opened normally through the menu.

What is the world is going on?

---

### Post by aysiu on 2008-12-12
It could be any number of things.

It could be a weird symlink between the root themes folder and the user themes folder. It could be permission issues related to that. It could be a badly constructed or improperly installed theme.

Not sure how to diagnose it exactly.

Does it happen only with Cassandra Mint or also with other themes? Does this occur for every user (hint: if you have only one user, create a test user)?

---

### Post by birnam on 2008-12-12
Hi, and thanks! I looked in both themes folders. There's nothing unusual in my user's themes, and the root themes folder is empty.cd /usr

I've tried uninstalling and reinstalling it repeatedly, and have never made any progress. I currently have the theme installed in /usr/share/themes by the way.

Annoyingly, if I create a new user it works fine there.

The theme has a question mark over it in the Theme panel with a note:

*"This theme will not look as intended because the required window manager theme 'Murrine' is not installed."*

Several of the themes I have have that, from what I've read it is a common symptom of pre-8.10 themes. The other user that this themes works beautifully for also gets this message and the question mark.

Is there maybe a trick to fully deleting a theme that I don't know? (i.e. hidden or permission-inaccessible files that tend to stick around)

---

### Post by Ivo Moelans on 2008-12-13
> The theme has a question mark over it in the Theme panel with a note:

"This theme will not look as intended because the required window manager theme 'Murrine' is not installed."

Several of the themes I have have that, from what I've read it is a common symptom of pre-8.10 themes. The other user that this themes works beautifully for also gets this message and the question mark.


In the theme's directory */home/<username>/.themes/Cassandra Mint Green* or */usr/share/themes/Cassandra Mint Green* there is a file also called *Cassandra Mint Green*. This is the index.theme file and it's function a.o. is to tell the theme where to get it's components. You can open and edit the file with gedit (Text Editor) with superuser privileges (terminal: *sudo gedit*).
You will find the following code:

```
[Desktop Entry]
Name=Cassandra Mint Green
Type=X-GNOME-Metatheme
Comment="Cassandra (Green)" theme revised by DrSnow
Encoding=UTF-8

[X-GNOME-Metatheme]
GtkTheme=Cassandra Mint Green
MetacityTheme=Murrine
IconTheme=Cassandra

```

As you can see the theme expects to find a Metacity theme (= window manager theme) called *Murrine* and an icon theme called *Cassandra*. If these are not on your system the theme will complain, hence the big '?' and the warning text.
The solution is simple: you can try to hunt down both themes or you can change the entries with themes that you know are installed on your system, e.g. *Human*, or whatever metacity theme and icon theme you like in combination whith this theme.

That's one problem out of the way. The other could, like aysiu said, be any number of things. Maybe you've got a slightly corrupted install file. You could try downloading it again from [http://www.gnome-look.org/content/show.php/Cassandra+Mint+Green?content=64998]("http://www.gnome-look.org/content/show.php/Cassandra+Mint+Green?content=64998"). When unpacked this file contain two versions of Cassandra: *Cassandra Mint Green* and *Cassandra Mint Green (Boxed)*. Maybe one of these works for you.

---

### Post by birnam on 2008-12-13
Well, I found the problem! I had installed a packaged called gtk-chtheme that had decided to take over the controls theming. (of course, it would be something I did to myself...)

I've tried removing that package but I still couldn't gain control over the controls from the normal appearance dialog, so I reinstalled and now just need to remember to use both dialogs in conjunction to change my themes. Perhaps if I did the "complete removal" option it would fix this the rest of the way -- but I don't have to worry about that now at least!

Thanks for your help!

---

