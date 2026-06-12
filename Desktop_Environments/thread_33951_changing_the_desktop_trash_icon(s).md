---
title: "changing the desktop trash icon(s)"
date: 2005-05-12
forum: Desktop Environments
---

### Post by 23meg on 2005-05-12
For the impatient, question first: how exactly do i change the desktop trash icons (full and empty)? Where are the default ones located?

For those with some time on their hands, the details: I've always thought it's a waste of panel space to have the trash on a panel, since I'll not empty the trash every few minutes, and prefer to have a trash icon on the desktop instead. And i'm not much into the idea of using icon themes, because I've looked into just about every icon theme on art.gnome.org and gnomelook.org, and the few acceptable ones I've come across either have a few icons missing, or have a few very bad icons.. Plus, I more or less like the default GNOME icon theme, I love the way it thumbnails text files (icon themes destroy this feature), and I like customizing icons myself.

---

### Post by shakin on 2005-05-12
/usr/share/icons/Human/scalable/filesystems/gnome-fs-trash-empty.svg
/usr/share/icons/Human/scalable/filesystems/ gnome-fs-trash-full.svg

---

### Post by 23meg on 2005-05-12
Alright, they're just kept in icon theme folders, nowhere special like /pixmaps or something. Forgive my dumbness; i always assumed otherwise for some reason. It seems mine are 

/usr/share/icons/gnome/48x48/filesystems/gnome-fs-trash-full.png
/usr/share/icons/gnome/48x48/filesystems/gnome-fs-trash-empty.png

, though, since i'm using the GNOME theme.

---

### Post by pedro_cesar on 2007-09-09
I'm using Ubuntu Feisty Fawn and my icon set is not there, and I'm using the Human Icon set. At the /usr/share/icons/Human/scalable/filesystems/ I have 6 icons and none of them are the trash's. One more thing, I realized the icons are svg but the icons I have are .ico and .png. will they work?

---

### Post by Perfect Storm on 2007-09-10
Nope. You need Inkscape or the latest version of gimp to convert to .svg files.

First you save the .png file in the rightful directory, then you open it with inkscape and save it as plain .svg (note there more than one .svg file type) in the same place as the .png file. Do not move or delete the .png file as the .svg file is now link to the .png file.

---

### Post by pedro_cesar on 2007-09-17
Well it took me sometime to figure everything out, thanks "Artificial Intelligence" for explainning all the .svg related, it really helped.

I want to point out that the files were not in that location, the empty trash icon was at:
/usr/share/icons/Human/scalable/places

and the full trash icon was at:
/usr/share/icons/Human/scalable/status

but for those who could still have'm at a different location, you can use locate name_of_file to find them, the names given by "shakin" did match.

---

### Post by George1234 on 2007-11-14
ok guys go easy on me  im very new to ubuntu and linux all together :P

ok so thanks to another thread on these forums i got my trash bin on to the desktop 
and like 23meg i wanted to change the ugly looking icon 

[img]http://img405.imageshack.us/img405/8131/71696598zt8.png[/img]
the icon on my desktop^

my empty icon was in 
/usr/share/icons/Human/scalable/places

and the full icon
/usr/share/icons/Human/scalable/status

i got inkscape like Artificial Intelligence said to 
i put the .png of the "full" icon i wanted  into /usr/share/icons/Human/scalable/status
and opened it up in inkscape  and saved it as a plain .svg 
then renamed it to gnome-fs-trash-full
[img]http://img208.imageshack.us/img208/2421/fullix0.png[/img]

i did the same in /usr/share/icons/Human/scalable/places
to the "empty" icon that i wanted to use 
[img]http://img210.imageshack.us/img210/9764/emptyct8.png[/img]

i go back to my desktop and  to my disappointment  its still this
[img]http://img405.imageshack.us/img405/8131/71696598zt8.png[/img]

i restarted the computer to see if that would do it  
and i also changed to another icon set and then back to human  but nothing has changed 

what did i do wrong? :/
(im using  Ubuntu 7.10 Gutsy Gibbon by the way)

---

### Post by George1234 on 2007-11-15
anyone? :-?

---

### Post by wireddad on 2008-02-18
I am curious also, any one has an answer for George1234?  I am looking to make the same changes.  Thanks.

---

### Post by bilal.17 on 2008-04-13
same here ^^

---

### Post by Xgen on 2008-04-13
I don't use the Human set but I have changed my trash container (on my tray) with other icon sets. The Human icon set also contains specific sizes other than scalable. If you use a set size (e.g. 36x36) then I assume that it will use that size if it is available and use the scale size for any other size in between.

---

